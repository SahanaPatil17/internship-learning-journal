# Clean up data in Excel

## Text Transformations
- Removed unwanted suffix "[more]" using Find & Replace.
- Eliminated extra internal spaces using TRIM() function.

## Structural Transformations
- Deleted rows with blank values in important columns.
- Removed duplicate country entries to retain unique values.

## Data Type Transformations
- Converted numeric columns from "General" to "Number" format.
- Standardized decimal precision to two decimal places.

## Data Quality Improvements
- Cleaned inconsistent text formatting.
- Ensured correct numeric interpretation.
- Reduced redundancy.
- Removed incomplete records.

---

# Data Transformation in Excel

## 1. Ratio Calculations

### A. Metro Area to City Area Ratio
- Formula used:
  ```
  =G2/D2
  ```
- Purpose: Compare metropolitan expansion relative to city limits.
- Insight Example: Tokyo’s metro area ≈ 6 times its city area.
- Errors observed where metro area data was missing.

---

### B. Metro Population to City Population Ratio
- Formula used:
  ```
  =F2/C2
  ```
- Purpose: Compare metro population against core city population.
- Insight Example: Tokyo ≈ 2.76 ratio.
- Automatically filled using double-click (AutoFill).

---

### C. Density Comparison (Crowding Indicator)
- Derived using relationship between:
  - Metro Area / City Area ratio
  - Metro Population / City Population ratio
- Used to measure crowd concentration differences between metro and city.

---

## 2. Pivot Table Transformations

### Creating Pivot Table
1. Select entire dataset.
2. Go to Insert → Pivot Table.
3. Create in a new worksheet.

---

### A. Aggregation by Country
- Drag "Country" into Rows.
- Displays unique country list.
- Pull "Country" again into Values → Count.
- Used to identify duplicate frequency.
  - Example: China appeared 20 times.
  - Angola appeared once.

---

### B. City-Level Aggregation
- Drag "City" under Country.
- Pull "City Proper Population" into Values.
- Change Values field to "Sum".
- Displays:
  - Population at city level.
  - Aggregated population at country level.

---

## 3. Chart-Based Insights

- Inserted bar chart from Pivot Table.
- Applied filter (e.g., China, US).
- Identified outliers:
  - China: Chongqing & Shanghai highest population.
  - US: Los Angeles highest density (crowding ratio).

---

# Text to Columns in Excel

## Structural Transformations
- Converted single-column raw text into multiple structured columns.
- Extracted categorical variables from mixed strings.

---

## Delimiter-Based Transformations
- "(" → Separated Senator Name.
- "-" → Extracted Party.
- ")" → Extracted State.
- "," → Extracted Vote Status.

---

## Data Structuring
- Transformed unstructured web data into tabular format.
- Created clean column headers.
- Removed redundant columns created during splitting.

---

## Analytical Readiness
- Converted scraped text into CSV-like dataset.
- Enabled filtering, sorting, and aggregation.
- Prepared data for further analysis or visualization.

---

# Data Aggregation in Excel

## 1. Weekly Aggregation using Pivot Table

Objective:
- Aggregate sum of New Cases
- Group by Country and Week
- Separate by Year (2020 & 2021)

### Pivot Setup:
- Rows → Location (Country)
- Columns → Week
- Values → Sum of New Cases
- Filter/Row grouping → Year

Insight:
- Weekly trends of COVID cases across countries.

---

## 2. Monthly Aggregation using Pivot Table

Objective:
- Aggregate sum of New Cases
- Group by Month and Country
- Separate by Year

### Pivot Setup:
- Rows → Year → Month
- Columns → Location
- Values → Sum of New Cases

Insight:
- Monthly wave patterns of COVID cases.

---

## 3. Color Scales (Conditional Formatting)

Purpose:
- Identify clusters of high and low new cases.

Configuration:
- 3-Color Scale:
  - Green → Low cases
  - Yellow → Medium
  - Red → High cases

Insight:
- Visual clustering of infection waves.
- Zoomed-out view shows progression trends.

---

## 4. Sparklines (Trend Visualization)

Purpose:
- Show weekly trend of new cases per country.

Steps:
- Insert → Line Sparkline.
- Data range → Weekly aggregated values.
- Enable High Point & Low Point markers.

Insight:
- Quick trend comparison across years.
- Identified peaks (e.g., India peak mid-2021).

---

## 5. Data Bars (Graphic Illustration)

Purpose:
- Visual representation of monthly aggregated data.

Steps:
- Select pivot values.
- Conditional Formatting → Data Bars.
- Used Gradient and Solid fills.

Insight:
- Clear wave patterns across months.
- Easy identification of peaks and declines.

---

## Result
Raw COVID dataset transformed into:
- Weekly and Monthly aggregated summaries.
- Trend visualizations.
- Cluster identification tools.
- Insight-driven comparative analysis across countries and years.

---

# Data Preparation using Shell Commands

## 1. File Retrieval Transformation
Downloaded web log data from a remote server using the curl command.

Result:
Raw compressed dataset obtained for analysis.

---

## 2. File Decompression
Converted compressed `.gz` file into readable log format using gzip.

Transformation:
Compressed file → Plain text log file.

---

## 3. Data Inspection
Used `head` and `tail` commands to preview the dataset structure.

Transformation:
Large dataset → Sample view for understanding format.

---

## 4. Data Counting
Applied `wc -l` to count total records.

Insight:
Number of requests made to the website during the month.

---

## 5. Field Extraction
Used `cut` command to isolate specific fields.

Example:
Extracted IP addresses from the first column.

Transformation:
Multi-field log data → Single-column IP dataset.

---

## 6. Sorting and Frequency Analysis
Used pipeline commands:

cut → sort → uniq → sort

Transformation:
Raw IP list → Ranked list of request frequency.

Insight:
Identified which IP addresses generated the most traffic.

---

## 7. Pattern Detection
Used `grep` with regular expressions to detect bots.

Transformation:
Filtered log entries containing bot identifiers.

Insight:
Recognized automated crawlers such as Googlebot and Applebot.

---

## 8. Log Format Conversion
Used `sed` to replace brackets with quotes.

Transformation:
Web log format → CSV-like structured format.

---

# Data Preparation using a Text Editor

## 1. JSON Formatting
Converted compact JSON structure into readable hierarchical format.

Transformation:
Compressed JSON → Structured JSON format.

Purpose:
Improved readability and easier data extraction.

---

## 2. Field Extraction
Extracted specific attributes such as City and Product using multi-selection.

Transformation:
Full JSON dataset → Individual attribute lists.

Purpose:
Focused analysis on specific columns.

---

## 3. Data Sorting
Applied alphabetical sorting to extracted city values.

Transformation:
Unordered list → Sorted dataset.

Purpose:
Identify duplicates and inconsistencies easily.

---

## 4. Duplicate Removal
Used editor command to delete duplicate lines.

Transformation:
Repeated values → Unique value list.

Purpose:
Identify distinct cities in the dataset.

---

## 5. Data Standardization
Corrected spelling variations of city names using multi-cursor editing.

Example:
Different spellings of Bangalore → Standardized as "Bangalore".

Purpose:
Ensure consistency in categorical data.

---
