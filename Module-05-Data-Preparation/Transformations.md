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
