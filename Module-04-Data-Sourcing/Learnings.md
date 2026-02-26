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
