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
