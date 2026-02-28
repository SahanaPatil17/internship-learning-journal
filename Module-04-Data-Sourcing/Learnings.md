# Module 4 – Learnings

## Get the Data – Scraping with Excel

### Learnings

This session introduced how to extract live data from websites directly into Excel using the Power Query feature.

I learned how to:

- Import web data using:
  - Data Tab → Get Data → From Web
- Paste a website URL to establish a connection
- Identify available tables from a webpage
- Use the Query Editor to:
  - Preview data
  - Remove unnecessary columns
  - Transform data before loading
- Understand the "Applied Steps" section
  - Each transformation is recorded step-by-step
- Load the cleaned table into Excel
- Refresh the data to fetch updated values from the website

### Key Understanding

- Excel can act as a lightweight web scraping tool.
- Data remains connected to the original source.
- Refresh updates the dataset dynamically.
- Transformations are stored and automatically reapplied during refresh.

### Practical Use Case

Imported:
Two Week Weather Forecast for Chennai

This data can now be:
- Analyzed
- Visualized
- Used for dashboards
- Used for trend analysis

## Get the Data – Scraping with Python

### What I Learned

This session introduced web scraping using Python to extract structured data from IMDB.

I learned how to:

- Import essential Python libraries:
  - requests
  - BeautifulSoup
  - pandas

- Fetch webpage content using requests.
- Parse HTML using BeautifulSoup.
- Inspect webpage elements to identify:
  - Tag names
  - Class names
  - Nested structure

- Understand HTML hierarchy:
  - Higher-level containers hold multiple records.
  - Lower-level tags hold specific data.

- Extract data using:
  - `a.text` → Movie title
  - `span.text` → Movie year
  - `strong.text` → Rating

- Store extracted data in lists.
- Convert lists into a pandas DataFrame.
- Display structured tabular output.

### Key Understanding

- Web pages are structured using HTML tags.
- Scraping requires identifying correct parent and child tags.
- Using higher-level containers allows extraction of multiple records.
- pandas helps convert unstructured scraped data into structured format.

### Practical Outcome

Successfully converted IMDB Top Movies list into a clean table format for:

- Data analysis
- Visualization
- Further processing

## Get the Data – Wikipedia

### What I Learned

This session introduced the use of the Wikipedia Python library to extract structured data directly from Wikipedia.

Instead of manually scraping HTML, the library provides built-in functions to access:

- Search results
- Page summaries
- Full article content
- References
- Images
- URLs
- Tables

### Concepts Understood

- Install external Python libraries using pip.
- Use `search()` to find relevant Wikipedia pages.
- Use `summary()` to retrieve concise information.
- Limit summary length using `sentences` parameter.
- Use `page()` to retrieve full article details.
- Access page attributes like:
  - `.url`
  - `.references`
  - `.images`

- Extract tables using:
  - HTML content
  - `pandas.read_html()`

### Key Understanding

- Wikipedia library abstracts HTML complexity.
- It provides structured access to knowledge data.
- Tables on Wikipedia are stored as lists.
- Sometimes trial-and-error is required to select the correct table index.

### Practical Outcome

Learned how to efficiently extract structured knowledge data from Wikipedia for:
- Research
- Data analysis
- Academic projects
- Automation tasks


## Get the Data – Scrape BBC Weather with Python

### What I Learned

This session focused on scraping structured weather data from the BBC Weather website using Python.

### Key Concepts Understood

- Web scraping involves extracting raw HTML from websites.
- `requests` fetches HTML content from web servers.
- `BeautifulSoup` parses HTML and allows element extraction.
- Browser Inspect tool helps identify:
  - Tag names
  - Class names
  - Element hierarchy

### Technical Learnings

- Use `find_all()` to retrieve multiple elements.
- Extract specific data from returned lists.
- Clean unwanted text using:
  - String splitting
  - Indexing
  - Regular expressions

- Convert extracted text into numerical format.
- Handle special characters like degree symbols.
- Generate date column dynamically using pandas.
- Combine multiple lists into structured DataFrame.
- Export results to CSV and Excel formats.

### Key Takeaways

1. `requests` → Fetches HTML.
2. `BeautifulSoup` → Extracts information from HTML.
3. Data cleaning is an essential part of scraping.
4. Scraped data can be structured and stored for analysis.
5. Legal considerations must be checked before scraping.

### Practical Outcome

Created a clean 14-day weather forecast dataset for Mumbai, ready for:

- Data analysis
- Forecast comparison
- Visualization
- Storage for future processing

---

## GitHub Actions – Scheduling & Automation

Core Learning:
GitHub Actions allows automation of workflows based on events such as push, pull request, or schedule (cron).

Key Concepts Learned:

• Workflows must be inside `.github/workflows/`
• YAML syntax is used to define jobs and triggers
• Cron expressions define time-based execution
• All schedules run in UTC timezone
• GitHub does NOT guarantee exact execution timing

Cron Structure:
Minute Hour Day Month Day-of-week

Example:
*/5 * * * *
Runs every 5 minutes.

Important Insight:
Even if you schedule something every 5 minutes, GitHub may delay execution due to internal queueing. Therefore, scheduled workflows should NOT be used for real-time monitoring.

Practical Applications:
• Automated deployments
• Dependency scanning
• Security checks
• Monthly reports
• Periodic backups

Major Takeaway:
Automation is powerful but must be designed with execution delays in mind.

---

## Screen Scraping with Gemini – Vision-Based Data Extraction

Core Learning:
Instead of scraping HTML using BeautifulSoup or Selenium, we can record screen content and let a multimodal LLM extract structured information from image frames.

Technical Insights:

• Recording at 1 frame per second converts each second into an analyzable image.
• Gemini processes video as sequential frames.
• Each frame costs tokens (~250 tokens/image).
• JSON mode must be enabled for structured output.
• This method relies on computer vision instead of DOM parsing.

Cost Efficiency:
Even 1000 frames cost only a few cents, making this scalable.

Advantages:
• Works on dynamic websites
• Bypasses HTML structure complexity
• Handles JavaScript-rendered content
• No need for browser automation

Limitations:
• Depends on visible content
• May skip content if scrolling too fast
• Not ideal for high-speed scraping

Major Insight:
We are increasingly better at vision-based extraction using AI than writing custom scraping logic.

Shift Observed:
Code-based automation → Vision-based automation

---

## Microsoft MarkItDown – Document Standardization for LLMs

Core Learning:
MarkItDown converts multiple file formats into clean Markdown, making documents LLM-friendly.

Why Markdown?
• Lightweight
• Human-readable
• Platform-independent
• Easy to chunk for embeddings
• Ideal for RAG pipelines

Modes of Operation:

A) Without LLM
• Direct parsing
• Fast conversion
• Works for PDFs and structured documents

B) With LLM
• Enables OCR
• Understands layout
• Improves formatting quality

Key Insight:
Data preprocessing is foundational for LLM performance.

Applications:
• Preparing enterprise documents
• Cleaning PDFs
• Knowledge base preparation
• Dataset generation
• RAG system pipelines

Comparison Insight:
MarkItDown is promising, but tools like Docling are currently more mature.

Major Takeaway:
Unstructured data must be standardized before feeding into AI systems.

---

## Nominatim – Geocoding with OpenStreetMap

Core Learning:
Geocoding converts text-based location names into structured geographic data.

Example:
"IIT Madras" → Latitude, Longitude, Full Address

Key Technical Points:

• Nominatim is powered by OpenStreetMap.
• Geopy is a Python wrapper for easy API access.
• user_agent parameter is mandatory.
• Returns structured JSON data.
• Includes class and type categorization.

Extractable Data:
• Latitude
• Longitude
• Display name
• Bounding box
• Class (tourism, amenity, etc.)
• Type (university, attraction, hospital)

Applications:
• Mapping applications
• Location analytics
• Delivery systems
• Geo-tagging datasets
• Urban planning

Major Takeaway:
Unstructured address text → Structured geographic intelligence.

---

## OVERALL TECHNICAL INSIGHTS FROM ALL SESSIONS

1. Automation (GitHub Actions) enables scheduled DevOps workflows.
2. Vision-based scraping reduces dependency on traditional HTML parsing.
3. Document conversion to Markdown improves LLM processing quality.
4. Geocoding enables spatial intelligence from text.
5. Structured output (JSON/Markdown) is essential for scalable AI systems.
6. Data preprocessing directly impacts AI/ML system performance.

# DocSearch Scraping Tutorial

### 1. Semantic Search vs Keyword Search
- Keyword search matches exact words.
- Semantic search uses embeddings to find meaning.
- Scraped data enabled building a semantic proof-of-concept search engine.

---

### 2. Caching is Critical During Development

The `cached_get()` pattern:
- Saves HTML responses locally.
- Prevents re-downloading on every run.
- Makes debugging dramatically faster.
- Allows safe interruption and resume.

Core idea:
- If cached file exists → load from disk.
- Else → fetch, save, then return.

This reflects the principle:
> Laziness, impatience, and hubris are programmer virtues.

---

### 3. Scraping Strategy

Scraping process must be broken into stages:

1. Get archive page URLs.
2. Extract article links.
3. Deduplicate links.
4. Fetch article pages.
5. Parse structured content.
6. Store structured output.

Small correct steps > Big complex logic.

---

### 4. XPath > Guesswork

Using browser DevTools:
- Inspect elements
- Identify stable container divs
- Avoid sidebars, popups, widgets
- Use `contains()` in XPath instead of exact class matching

Trial and error is normal.

---

### 5. Debugging Techniques (Top 3)

#### Print Liberally
Print variables frequently to confirm expectations.

#### Use Breakpoints
Use `breakpoint()` or debugger to inspect variables when confused.

#### Rubber Ducking
Explain the problem clearly (to a person or LLM).
Often clarity emerges during explanation itself.

---

### 6. Use LLMs Properly

Two modes:
- Ask implementation questions (e.g., how to use httpx)
- Ask troubleshooting strategy questions

Important:
- Be specific.
- Mention preferred libraries.
- Ask for short, readable code.

---

### 7. Proof of Concept > Presentation

A working demo:
- Converts clients faster than slides.
- Shows capability instantly.
- Enables rapid production deployment.

Portfolio > Certificates.

---

### 8. Save Incrementally

Write output JSON inside loop.
Benefits:
- Inspect progress early.
- Build next system phase without waiting for completion.
- Avoid losing hours of scraping.

---

### 9. Handle Edge Cases

Real-world scraping requires:
- Redirect handling
- Empty responses
- HTTP 200 with empty content
- Class name mismatches
- Deduplication

Expect imperfections.

---

## Broader Insight

- Small experiments can win major opportunities.
- Rapid prototyping changes competitive advantage.
- Technical curiosity + structured thinking = leverage.

# Scraping PDFs

### 1. Extracting PDFs from Webpages

- Use BeautifulSoup to parse HTML.
- Extract anchor tags.
- Filter links ending in ".pdf".
- Use string split to extract filename:
  link.split("/")[-1]

This allows automated downloading of multiple PDFs from a single page.

---

### 2. Handling File Storage

- Create folder if not exists.
- Use Google Drive (Colab) or local directory.
- Write PDF in binary mode.

Automation avoids manual downloading of 25–30 documents.

---

### 3. Reading Tables from PDFs

Tabula library:
- Works similar to pandas.read_csv
- Uses read_pdf()

Example:
- pages=18 → extracts only page 18
- pages="all" → extracts all tables

---

### 4. Problem: Extra Content in Table Extraction

Issue:
- Tabula detected multiple sections as tables.
- Page layout (landscape formatting) caused misinterpretation.
- Non-table content included.

Example:
- Newcastle United "125 years" text extracted unintentionally.
- Logos ignored (image content not parsed).

---

### 5. Solution: Area Parameter

Tabula allows:
area=[top, left, bottom, right]

This:
- Restricts extraction to specific region.
- Removes unwanted content.
- Produces clean structured table.

This is critical for precise PDF parsing.

---

### 6. Direct CSV Conversion

Using:
convert_into()

Benefits:
- Directly outputs CSV file.
- Reduces manual post-processing.
- Faster pipeline from PDF → structured data.

---

## Practical Insights

- PDF scraping is different from HTML scraping.
- Layout matters significantly.
- Always inspect extracted DataFrame before saving.
- Fine-tuning extraction region improves accuracy.

---

## Broader Learning

PDF scraping workflow:

Webpage → PDF download → Table extraction → Cleaning → CSV export

This pipeline is useful for:
- Financial reports
- Government documents
- Sports analytics
- Research publications

Automating PDF table extraction saves hours of manual work.
