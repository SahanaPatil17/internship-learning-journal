# Multi-Source Data Extraction Engine — Project Report

---

## Problem Understanding

The goal was to build a robust, large-scale data extraction engine capable of collecting information from multiple heterogeneous sources — websites, PDFs, CSV files, and Excel spreadsheets — and normalizing all output into a structured JSON format suitable for LLM training and fine-tuning.

The core challenges baked into the problem statement were:
- Sources are structurally inconsistent (a website is nothing like a PDF or a spreadsheet)
- Layouts vary wildly even within the same source type
- Missing fields and extraction errors must be handled gracefully without crashing the pipeline
- The solution must be modular, reproducible, and built only on open-source tools
- Output must be clean, structured, and LLM-ready

---

## Research Findings

Before writing any code, the following tools were evaluated:

| Tool | Purpose | Chosen? |
|---|---|---|
| `requests` + `BeautifulSoup` | Static HTML scraping | No — fails on JS-rendered pages |
| `Scrapy` | Large-scale crawling framework | No — overkill for multi-source, harder to extend |
| `Playwright` | Browser automation, handles JS | ✅ Yes |
| `Selenium` | Browser automation | No — slower, more setup, less async-friendly |
| `PyMuPDF (fitz)` | PDF text extraction | ✅ Yes — fast, per-page control, metadata access |
| `pdfplumber` | PDF extraction | No — slower, less metadata |
| `pandas` | CSV/Excel loading | ✅ Yes — industry standard |
| `openpyxl` / `xlrd` | Excel engines | ✅ Yes — needed for .xlsx and .xls respectively |
| `Streamlit` | UI dashboard | ✅ Yes — fast to build, no frontend knowledge needed |

Key finding from research: most modern websites are JavaScript-rendered, meaning a simple `requests.get()` returns an empty shell with no content. A real browser engine (Playwright) is mandatory for reliable web scraping at scale.

---

## Approach Taken

The engine was architected as a modular pipeline with four distinct layers:

```
Input → Detector → Extractor → Cleaner → JSON Output
```

**1. Detector (`detector.py`)**
Identifies the source type from the input string. Uses `urllib.parse` for proper URL validation rather than naive string checks.

**2. Extractors (`extractor/`)**
Three separate, independent modules — one per source type:
- `web_extractor.py` — async Playwright scraper
- `pdf_extractor.py` — PyMuPDF per-page extraction
- `csv_loader.py` — pandas with chunked reading for large files + multi-sheet Excel support

**3. Cleaner (`cleaner/cleaning.py`)**
Source-aware normalization — separate functions for web, PDF, and tabular data. Unicode normalization, control character removal, whitespace collapsing.

**4. Output**
All results saved as structured nested JSON with metadata (source type, timestamp, schema, error state).

**5. Interfaces**
- CLI (`main.py`) with `--input`, `--batch`, and `--output` flags
- Streamlit dashboard (`app.py`) with single URL, batch URL, and file upload tabs

---

## Alternatives Tried (Failed Attempts & Iterations)

### ❌ Iteration 1 — Basic requests + BeautifulSoup

The first attempt used `requests` to fetch page HTML and `BeautifulSoup` to parse it.

```python
import requests
from bs4 import BeautifulSoup

response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")
text = soup.get_text()
```

**What went wrong:** This worked fine on simple static pages like Wikipedia, but failed completely on any modern e-commerce or dynamic site. Sites like `books.toscrape.com/js` returned an empty `<body>` tag because the content is injected by JavaScript after the initial HTML load. `requests` only fetches the raw HTML — it never runs JavaScript. Output was either empty or just navigation boilerplate.

**Lesson:** Static scraping is insufficient for the modern web. A real browser engine is non-negotiable.

---

### ❌ Iteration 2 — Synchronous Playwright (headless=False)

Switched to Playwright but used the synchronous API with `headless=False`:

```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch(headless=False)
    page = browser.new_page()
    page.goto(url, timeout=60000)
    page.wait_for_load_state("networkidle")
    page.wait_for_timeout(5000)
    page.evaluate("window.scrollTo(0, document.body.scrollHeight)")
    page.wait_for_timeout(2000)
    text = page.locator("body").inner_text()
    browser.close()
```

**What went wrong — Problem 1:** `headless=False` opens a visible browser window on every single extraction. In a batch of 10 URLs this spawns 10 browser windows simultaneously, consuming enormous RAM and making the app unusable on any server or headless environment.

**What went wrong — Problem 2:** The synchronous API processes one URL at a time. Scraping 20 URLs took 3–4 minutes sequentially.

**What went wrong — Problem 3:** On Windows, running this inside Streamlit threw:
```
NotImplementedError
asyncio.base_events.py: _make_subprocess_transport
```
Because Streamlit runs its own event loop and `asyncio.run()` conflicts with it. Additionally, Python's default `SelectorEventLoop` on Windows cannot spawn subprocesses, which is what Playwright needs to launch Chromium.

**What went wrong — Problem 4:** The output was a single flat string — no structure, no metadata, no title, no links. Not useful for LLM training data.

**Lesson:** Needed async API, headless=True, Windows event loop fix, and structured output.

---

### ✅ Iteration 3 — Async Playwright with structured output (working, but detectable)

Rewrote using `async_playwright` with `asyncio.gather()` for concurrency:

```python
async with async_playwright() as pw:
    browser = await pw.chromium.launch(headless=True)
    context = await browser.new_context(user_agent="Mozilla/5.0 ...")
```

Added the Windows fix:
```python
if sys.platform == "win32":
    asyncio.set_event_loop_policy(asyncio.WindowsProactorEventLoopPolicy())
```

This worked correctly on the practice sites. However, testing against slightly more protected sites revealed the scraper was still being detected and blocked. Investigating with bot-detection checker sites showed the headless browser was leaking several fingerprints:
- `navigator.webdriver` was `true`
- Plugin count was `0` (real browsers have 3–5)
- WebGL renderer exposed `SwiftShader` (headless GPU)
- Chrome runtime object was missing entirely
- Screen dimensions were unrealistically small

---

### ✅ Iteration 4 — Stealth mode + rotating identities (final version)

Added a JavaScript stealth patch injected via `page.add_init_script()` before every navigation, fixing all detected fingerprint leaks. Added rotating user agents (9 real browser strings), random viewports, randomized human-like delays, isolated browser context per request, and optional proxy rotation.

```python
STEALTH_JS = """
() => {
    Object.defineProperty(navigator, 'webdriver', { get: () => undefined });
    Object.defineProperty(navigator, 'plugins', { get: () => [1, 2, 3, 4, 5] });
    window.chrome = { runtime: {}, loadTimes: () => {}, csi: () => {}, app: {} };
    // ... WebGL, screen dimensions, permissions API patches
}
"""
await page.add_init_script(STEALTH_JS)
```

Also replaced the single-jump scroll with a slow incremental scroll (150px every 150ms) to better trigger lazy-loading and look more human.

---

## Challenges Faced

**1. Windows asyncio subprocess error**
`NotImplementedError` when Playwright tried to launch Chromium inside Streamlit on Windows. Root cause: Python's default `SelectorEventLoop` on Windows does not support subprocess spawning. Fixed with one line: `asyncio.set_event_loop_policy(asyncio.WindowsProactorEventLoopPolicy())`.

**2. Bot detection on real sites**
Even with a real user agent, headless Chromium exposes itself through `navigator.webdriver = true`, zero plugins, and SwiftShader WebGL. Required writing a custom stealth JS patch injected before each page load.

**3. Large file handling**
Loading a 200MB CSV with `pd.read_csv()` directly consumed all available RAM and hung. Fixed by detecting file size and switching to chunked reading (`chunksize=10000`) for files over 50MB.

**4. Excel multi-sheet support**
The original `load_csv()` function called `pd.read_csv()` on `.xlsx` files, which threw an error. Required a separate `load_excel()` function using `openpyxl` (for `.xlsx`) and `xlrd` (for legacy `.xls`), with per-sheet extraction.

**5. JSON serialization of pandas types**
`pd.NaT`, `np.int64`, and `np.float64` are not natively JSON-serializable. `json.dump()` threw `TypeError`. Fixed by replacing `NaN` with `None` via `df.where(pd.notnull(df), None)` and passing `default=str` to `json.dump()`.

**6. Lazy-loaded content not appearing**
A single `window.scrollTo(0, document.body.scrollHeight)` jump did not trigger lazy-load observers on many sites because the Intersection Observer API fires based on incremental scroll events, not jumps. Fixed by replacing the scroll with an incremental loop (150px steps with 150ms intervals).

---

## Learnings

**Technical**
- Static scraping (`requests` + `BeautifulSoup`) is dead for modern websites. If the site uses React, Vue, or Angular, you need a real browser.
- Playwright's async API is significantly faster than sync for batch workloads — 5 concurrent tabs reduced a 20-URL batch from ~4 minutes to ~50 seconds.
- Headless browsers have a distinct fingerprint that most serious sites detect. Stealth patching is not optional if you want reliable results beyond sandboxed practice sites.
- Pandas chunked reading is essential for production data pipelines. A 200MB file should never be loaded in one shot.
- Each source type (web, PDF, tabular) needs its own cleaning strategy — a one-size-fits-all regex approach destroys useful content (URLs, emails, numbers).

**Architectural**
- Separating detection, extraction, and cleaning into independent modules made iteration much faster — each failed attempt only required changing one file, not the whole codebase.
- Returning structured dicts (not raw strings) from every extractor made the output immediately usable for downstream tasks like LLM fine-tuning without additional post-processing.
- Exposing both a CLI and a Streamlit UI from the same core logic (no code duplication) is the right pattern for tools that need to work both interactively and in automated pipelines.

**About bot detection**
- There is no single fix — bot detection is a cat-and-mouse game. The stealth patches cover the most common tells but are not a guarantee against enterprise-grade detection (Cloudflare, DataDome, PerimeterX).
- For sites with serious bot protection, the correct solution is their official API, not scraping.
- Proxy rotation is only useful if the proxies themselves are not already flagged. Free proxy lists are often pre-blocked; residential proxies from paid providers are far more reliable.

---

## Improvements Over Time — Summary

| Version | What Changed | Why |
|---|---|---|
| v1 — requests + BS4 | Static HTML scraping | Initial naive attempt |
| v2 — Sync Playwright | Real browser, but blocking, visible, flat output | JS pages now work |
| v3 — Async Playwright | Concurrent, headless, structured output, Windows fix | Batch performance + usability |
| v4 — Stealth + Rotation | Fingerprint patching, rotating UAs/viewports, delays, proxies, isolated contexts | Bypass basic bot detection |

---

## Tech Stack

| Component | Library / Tool |
|---|---|
| Web scraping | `playwright` (async) |
| PDF extraction | `PyMuPDF` (fitz) |
| Tabular data | `pandas`, `openpyxl`, `xlrd` |
| Text cleaning | `re`, `unicodedata` (stdlib) |
| UI | `streamlit` |
| Logging | `logging.handlers.RotatingFileHandler` |
| Output format | JSON (stdlib `json`) |
| Language | Python 3.11 |
