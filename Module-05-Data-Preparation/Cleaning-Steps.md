# Clean up data in Excel

## Dataset Used
- Source: Wikipedia (City-wise population dataset)
- Columns included: City Name, Country, Population Estimates, City Definition (Municipality/Capital/Autonomous), Area, etc.
- Mixed data types: Text and Numeric values.

---

## 1. Find and Replace (Ctrl + H)

**Objective:** Remove unwanted text ("more" inside square brackets) from the Country column.

### Steps:
1. Select the dataset or specific column.
2. Press `Ctrl + H` to open Find and Replace.
3. In "Find what", enter the unwanted term (e.g., [more]).
4. Leave "Replace with" empty.
5. Click **Replace All**.
6. Verify number of replacements made.

---

## 2. Change Data Format (General → Number)

**Objective:** Convert numeric columns (E to N) to proper Number data type.

### Steps:
1. Select columns E to N.
2. Go to the Home tab.
3. Change data type from **General** to **Number**.
4. Adjust decimal places if needed.

---

## 3. Remove Extra Spaces using TRIM()

**Objective:** Clean unnecessary spaces in text fields (e.g., extra spaces around hyphens).

### Steps:
1. Insert a new column (e.g., "Trim Column").
2. Use formula:
   ```
   =TRIM(D2)
   ```
3. Drag the formula down for all rows.
4. Replace original column if required.

---

## 4. Identify and Delete Blank Rows

**Objective:** Remove rows where important columns contain blank values.

### Steps:
1. Select the relevant column (e.g., Column D).
2. Go to **Home → Find & Select → Go To Special**.
3. Choose **Blanks**.
4. Right-click on highlighted cells.
5. Click **Delete → Entire Row**.

---

## 5. Remove Duplicates

**Objective:** Keep only unique country values.

### Steps:
1. Copy the Country column to a new sheet.
2. Select the column.
3. Go to **Data → Remove Duplicates**.
4. Confirm selection.
5. Excel shows count of removed duplicates and remaining unique values.

---

# Data Transformation in Excel

## Step 1: Compute Ratios
- Calculate Metro Area / City Area.
- Calculate Metro Population / City Population.
- Use AutoFill to apply formulas across rows.
- Handle missing values carefully.

---

## Step 2: Create Pivot Table
- Insert Pivot Table from entire dataset.
- Create in new worksheet.

---

## Step 3: Detect Duplicates
- Drag Country to Rows.
- Add Country again to Values → Count.
- Identify frequency of records per country.

---

## Step 4: Aggregate Continuous Variables
- Add City Proper Population to Values → Sum.
- View total population by country.

---

## Step 5: Identify Outliers
- Insert Pivot Chart (Bar Chart).
- Apply country filter.
- Observe extreme values in:
  - Population
  - Density ratios

---

# Convert Text to Columns in Excel

## Dataset Used
- Source: US Senate voting records (copied from website).
- Original format: Entire record pasted into a single column.
- Content included:
  - Senator Name
  - Party
  - State
  - Vote (Yea/Nay/Not Voting)

---

## Problem
All values were combined in one column separated by:
- Left parenthesis "("
- Hyphen "-"
- Right parenthesis ")"
- Comma ","

This made the dataset unstructured and unsuitable for analysis.

---

## Step 1: Split by Left Parenthesis "("
1. Select the column.
2. Go to Data → Text to Columns.
3. Choose "Delimited".
4. Select "Other" and enter "(".
5. Click Next → Finish.

Result:
- Senator name separated from remaining data.

---

## Step 2: Split by Hyphen "-"
1. Select the new column.
2. Data → Text to Columns.
3. Delimited → Other → "-".
4. Finish.

Result:
- Party separated into its own column.

---

## Step 3: Split by Right Parenthesis ")"
1. Select remaining column.
2. Data → Text to Columns.
3. Delimited → Other → ")".
4. Finish.

Result:
- State extracted into a separate column.

---

## Step 4: Split by Comma ","
1. Select final column.
2. Data → Text to Columns.
3. Delimited → Select "Comma".
4. Finish.

Result:
- Vote (Yea/Nay/Not Voting) separated.

---

## Step 5: Final Formatting
- Delete unnecessary extra columns.
- Add headers:
  - Senator
  - Party
  - State
  - Vote
- Apply formatting for clarity.

---
