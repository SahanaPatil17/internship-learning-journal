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
