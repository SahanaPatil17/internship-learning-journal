# Module 4 – Web Sources

## Website Used

### Time and Date – Weather Forecast

URL:
https://www.timeanddate.com/weather/

Example Page Used:
Two Week Weather Forecast – Chennai

### Type of Data Extracted

- Date
- Temperature
- Weather conditions
- Wind
- Forecast information

### Method of Extraction

- Excel Power Query
- Data → Get Data → From Web
- Selected "Table 0" from detected webpage tables
- Removed unnecessary columns
- Loaded as refreshable table

### Live Data Connection

The Excel file remains connected to the webpage.

To update:
- Data → Refresh  
OR  
- Right click table → Refresh  

This fetches the latest forecast data.

### IMDB – Top Rated Movies

Source:
https://www.imdb.com/chart/top/

### Data Extracted

- Movie Title
- Release Year
- IMDB Rating

### Method Used

1. Copied IMDB Top Movies URL.
2. Loaded webpage using requests.
3. Parsed HTML using BeautifulSoup.
4. Identified required tags using Inspect tool.
5. Extracted:
   - `a` tag → Title
   - `span` tag → Year
   - `strong` tag → Rating
6. Converted extracted data into pandas DataFrame.

### Type of Extraction

- HTML Tag Based Scraping
- Class-based element selection
- Static Web Scraping

### Nature of Data

- Live website data
- Not automatically refreshable
- Requires re-running Python script for updated data

### Wikipedia

Website:
https://www.wikipedia.org/

Example Used:
Wikipedia article search (e.g., IIT Madras)

### Data Extracted

- Search results
- Page summaries
- Full article content
- Article URL
- References (external links)
- Images
- Tables (using pandas)

### Extraction Method

Instead of traditional scraping using:
- requests
- BeautifulSoup

Used:
- wikipedia Python library

### Table Extraction Method

1. Retrieve page HTML.
2. Use `pandas.read_html()` to read all tables.
3. Select required table by index.
4. Convert into DataFrame.

### Nature of Data

- Live Wikipedia data
- Requires script re-execution for updated content
- Structured access via API-like interface

### BBC Weather

Website:
https://www.bbc.com/weather

Example Used:
Mumbai – 14 Day Weather Forecast

### Data Extracted

- High Temperature (°C)
- Low Temperature (°C)
- Daily Summary
- Forecast Dates

### Extraction Method

1. Used requests to fetch HTML content.
2. Parsed HTML using BeautifulSoup.
3. Located data using:
   - Span tags
   - Specific class names
4. Used regular expressions to process summary text.
5. Structured cleaned data into pandas DataFrame.
6. Saved output as CSV and Excel files.

### Nature of Data

- Live weather data
- Requires script re-execution for updates
- Structured through HTML tag-based scraping
