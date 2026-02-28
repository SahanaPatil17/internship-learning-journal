# Files and APIs

## Topic: Getting Data by Scraping with Excel (From Web)

### Type of Source
- Web Source (Public Website)
- Structured HTML Table Data
- Live Connected Data Source

### Tool Used
- Microsoft Excel
- Power Query (Get & Transform)
- Data → Get Data → From Web

### Data Source Used
Website: https://www.timeanddate.com/weather/  
Example: Two Week Weather Forecast – Chennai

### What Was Done
- Connected Excel to a live website using **From Web query**
- Extracted structured table data (2-week forecast)
- Loaded data into Excel as a connected query
- Edited and transformed data inside Query Editor
- Removed unnecessary columns
- Created a refreshable data connection

### Key Concepts Covered
- Web scraping using Excel
- Query Editor
- Table View vs Web View
- Applied Steps tracking
- Data transformation
- Refreshable live data connection

### Important Feature
The imported table remains **connected to the website**.
Using **Refresh**, Excel fetches the latest updated data.

## Topic: Scraping Data from IMDB using Python

### 🔹 Type of Source
- Public Website
- HTML Structured Data
- Static Web Page

### Tools & Libraries Used

- Python
- Jupyter Notebook
- requests
- BeautifulSoup (bs4)
- pandas

### Purpose of the Exercise

To scrape the **Top Rated Movies list from IMDB** and convert:

- Movie Title
- Release Year
- IMDB Rating

into structured tabular format using Python.

### Technical Workflow

1. Import required libraries:
   - requests → Access webpage
   - BeautifulSoup → Parse HTML
   - pandas → Create DataFrame

2. Load webpage content using requests.

3. Convert HTML content into BeautifulSoup object.

4. Inspect webpage elements using:
   - Right click → Inspect
   - Identify HTML tags and classes

5. Extract data using:
   - Higher level tag: `chart full-width`
   - Title & Year: `titleColumn`
   - Rating: `ratingColumn imdbRating`
   - Title extraction: `a.text`
   - Year extraction: `span.text`
   - Rating extraction: `strong.text`

6. Store extracted data into lists.

7. Convert lists into a pandas DataFrame.

8. Display the table.

### Output

A structured DataFrame containing:
- Movie Title
- Year
- Rating


## Topic: Extracting Data Using the Wikipedia Python Library

### Type of Source
- Public Knowledge Base
- Wikipedia Articles
- Structured & Semi-Structured Web Data

### Tools & Libraries Used

- Python
- wikipedia (Python library)
- pandas
- Jupyter Notebook

### Installation

bash
pip install wikipedia

### Purpose of the Exercise

- To extract structured information directly from Wikipedia using the wikipedia Python library instead of manually scraping HTML.

### Functionalities Used

- Search for keyword: wikipedia.search()
- Get article summary: wikipedia.summary(), With sentences argument for limited summary
- Get full page: wikipedia.page()
- Extract: URL → page.url, References → page.references, Images → page.images
- Extract tables from page: Use page HTML, pandas.read_html() to extract tables, Select required table index

### Key Advantage

Using the Wikipedia library simplifies data extraction:
- No manual HTML parsing
- No need for BeautifulSoup
- Direct access to structured page elements


## Topic: Scraping BBC Weather Data using Python

### Type of Source
- Public Website
- Dynamic Weather Data
- HTML Structured Data

### Libraries Used

- Python
- requests
- BeautifulSoup (bs4)
- pandas
- re (Regular Expressions)
- datetime

### Purpose of the Exercise

To scrape 14-day weather forecast data for Mumbai from BBC Weather and store it in:

- pandas DataFrame
- CSV file
- Excel file

### Data Extracted

- Daily High Temperature (°C)
- Daily Low Temperature (°C)
- Daily Weather Summary
- Date

### Technical Workflow

1. Fetch HTML page using:
   - `requests.get(URL)`

2. Parse HTML using:
   - `BeautifulSoup(response.content, "html.parser")`

3. Inspect webpage elements to locate:
   - High temp → `day-temperature-high`
   - Low temp → `day-temperature-low`
   - Summary → Specific span blocks

4. Use:
   - `find_all()` to extract multiple elements
   - List processing to clean unwanted text
   - String split to remove Fahrenheit values
   - Regular expressions to split long summary string

5. Generate date column using:
   - `pandas.date_range()`

6. Create DataFrame using:
   - `pandas.DataFrame()`

7. Clean degree symbol and convert to float.

8. Save output as:
   - `.csv`
   - `.xlsx`

### Important Notes

- Web scraping may not always be legally permitted.
- Always check website terms and conditions before scraping.
- 
---

GitHub Actions – Scheduled Workflows


Required Folder Structure:

project-root/
│
└── .github/
    └── workflows/
        └── main.yml

GitHub ONLY detects workflow files inside `.github/workflows/`.

Example Workflow File (main.yml):

name: Scheduled Workflow

on:
  push:
    branches:
      - main
  schedule:
    - cron: "*/5 * * * *"

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: echo "Running scheduled workflow"

Cron Format:

* * * * *
| | | | |
| | | | └── Day of week (0-7)
| | | └──── Month (1-12)
| | └────── Day of month (1-31)
| └──────── Hour (0-23)
└────────── Minute (0-59)

Example:
0 8 1 * *
Runs at 8 AM on 1st of every month (UTC).

🖥 Environment:
- GitHub-hosted Ubuntu VM
- YAML configuration
- UTC timezone
- Execution time not guaranteed exactly

Use Cases:
- Automated deployments
- Security scans
- Vulnerability checks
- Periodic reports

---

Screen Scraping with Gemini (Vision-Based Scraping)


Concept:
Instead of scraping HTML using code, record the screen and let Gemini extract structured data from frames.

Files Used:
- screen_recording.mp4
- JSON output generated by Gemini

Recording Settings:
- 1 frame per second
- Scroll once per second
- Save short MP4

Platform Used:
Google AI Studio (Gemini Flash model)

Prompt Example:
"Extract all information in these tweets as JSON."

Example Output:

[
  {
    "username": "example_user",
    "handle": "@example",
    "text": "Sample tweet",
    "likes": 120
  }
]

Cost Estimation:
~250 tokens per image  
$0.075 per 1M tokens  

Example:
19 frames × 250 tokens = 4750 tokens  
Cost ≈ 0.04 cents  

Advantages:
- No HTML parsing
- No Selenium required
- Works visually
- Handles dynamic web apps

Limitations:
- May skip frames
- Not real-time
- Depends on visible content
- Requires good prompt formatting

---

Microsoft MarkItDown – File to Markdown Conversion

Purpose:
Convert multiple document types into clean Markdown format for LLM pipelines, indexing, and RAG systems.

Installation:

pip install markitdown

Supported Formats:
- PDF
- Word (.docx)
- Excel (.xlsx)
- PowerPoint
- Images (OCR)
- HTML
- XML
- JSON
- CSV
- ZIP
- Audio files

Basic Usage (Without LLM):

from markitdown import MarkItDown

md = MarkItDown()
result = md.convert("file.pdf")
print(result.text_content)

With LLM (OCR):

from markitdown import MarkItDown
from openai import OpenAI

client = OpenAI()

md = MarkItDown(llm_client=client, llm_model="gpt-4o")
result = md.convert("image.png")
print(result.text_content)

🖥 CLI Usage:

markitdown file.pdf

Using pipe:
cat file.pdf | markitdown

Use Cases:
- Preparing documents for RAG
- Cleaning enterprise PDFs
- Converting Excel knowledge bases
- Standardizing document formats
- Dataset generation

Key Insight:
Unstructured documents → Structured Markdown → Better LLM performance

---

Nominatim – OpenStreetMap Geocoding API

Purpose:
Convert text addresses into geographic coordinates and structured location data.

Installation:

pip install geopy

Python Example:

from geopy.geocoders import Nominatim

locator = Nominatim(user_agent="my_geocoder")
location = locator.geocode("Eiffel Tower")

print(location.latitude)
print(location.longitude)
print(location.address)
print(location.raw)

Example JSON Structure (location.raw):

{
  "lat": "48.8582602",
  "lon": "2.2944991",
  "display_name": "Eiffel Tower, Paris, France",
  "class": "tourism",
  "type": "attraction",
  "boundingbox": [...]
}

Extractable Fields:
- Latitude
- Longitude
- Full formatted address
- Bounding box
- Class (e.g., tourism, amenity)
- Type (e.g., attraction, university)

Example:
Input: "IIT Madras"
Output:
- Coordinates
- Full address with pincode
- Class: amenity
- Type: university

Applications:
- Location-based analytics
- Delivery optimization
- Geo-tagging datasets
- Urban planning
- Mapping systems

Important Notes:
- Free & open-source
- Rate limited
- Requires user_agent parameter
- Alternative to Google Maps Geocoding API

---

OVERALL TECHNICAL TAKEAWAYS

1. Automation can be scheduled using GitHub cron workflows.
2. Vision-based scraping is an alternative to HTML scraping.
3. Converting documents to Markdown improves LLM pipeline quality.
4. Geocoding converts unstructured text into structured geographic intelligence.
5. Data preprocessing is critical for AI/ML applications.
6. Structured output (JSON / Markdown) is essential for scalable systems.

# DocSearch Scraping Tutorial

## Files Created

### 1. scrape2.py
Main Python script used to:
- Iterate through archive pages
- Extract article URLs
- Scrape individual article content
- Save structured output

### 2. cache2/ (Directory)
- Stores cached HTML responses
- Uses MD5 hash of URLs as filenames
- Prevents repeated downloads during development

### 3. urls2.txt
- Stores extracted article URLs
- Allows resuming scraping without repeating archive parsing

### 4. scraped2.json
- Final structured output
- Contains:
  - title
  - body content

### 5. scraped2.csv (Optional)
- Alternative export using pandas
- Tabular representation of scraped content


---

## Python Libraries Used

### 1. httpx
- Used instead of `requests`
- Supports async (if needed later)
- Allows redirect handling
- Used with:
  - `follow_redirects=True`
  - `raise_for_status()`

### 2. lxml.html
- Used for fast and standards-compliant HTML parsing
- Used XPath expressions for content extraction

### 3. tqdm
- Displays progress bar while iterating pages

### 4. hashlib
- Used MD5 hashing for safe cache filenames

### 5. os
- Directory creation
- File existence checks
- Path handling

### 6. json
- Saving structured scraped data

### 7. pandas (optional)
- Exporting results to CSV


---

## Website Scraped

- Insider Intelligence archive
- ~369 archive pages
- ~7000 articles scraped
- Structure:
  - Archive pages list article links
  - Each article page contains:
    - Title (H1 with specific class)
    - Body content (within structured div containers)


---

## Architecture Flow

1. Loop through archive pages (archive/1 → archive/n)
2. Extract links containing `/content/`
3. Deduplicate links using set
4. Loop through article URLs
5. Fetch content using cached_get()
6. Parse title and body via XPath
7. Store structured results
8. Save JSON incrementally
