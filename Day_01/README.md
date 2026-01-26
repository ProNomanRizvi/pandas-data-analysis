# 🐼 Day 01: Pandas I/O Operations

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 01 introduces fundamental Pandas input/output (I/O) operations. Learn how to read data from various file formats (CSV, Excel, JSON) and export DataFrames to different formats. These are essential skills for any data analysis workflow.

## Topics Covered

### 1. **Reading Data Files**

#### Read CSV Files
```python
import pandas as pd
df = pd.read_csv("sample_data.csv")
print(df.head())
```
- Most common data format in data science
- Fast and efficient for large datasets
- Supports various encoding options

#### Read Excel Files
```python
df = pd.read_excel("sample_data.xlsx")
print(df.head())
```
- Requires `openpyxl` library
- Can read specific sheets
- Handles formatted Excel data

#### Read JSON Files
```python
df = pd.read_json("sample_data.json")
print(df.head())
```
- Common for web APIs and modern applications
- Supports nested data structures
- Flexible data interchange format

---

### 2. **Exporting Data**

#### Create and Export DataFrames
```python
import pandas as pd

# Create sample data
data = {
    "Name": ["Noman", "Shah Nawaz", "Riaz Hussain", "Huzaifa Iqbal", "Haseeb Hassan", "Tayyab", "Samiullah", "Talha Fahad", "Saad"],
    "Age": [20, 21, 20, 22, 19, 20, 19, 20, 21],
}
df = pd.DataFrame(data)

# Export to different formats
df.to_csv("sample_data.csv", index=False)
df.to_excel("sample_data.xlsx", index=False)
df.to_json("sample_data.json", orient='records')
```

**Key Points:**
- Use `index=False` to avoid saving row indices
- `orient='records'` in JSON creates a list of dictionaries
- Always specify the file extension

---

## Files in This Directory

- **`day-01-work.ipynb`** — Main Jupyter notebook with I/O examples and exercises
- **`sample_data.csv`** — Example CSV file used in the notebook
- **`sample_data.json`** — Example JSON file exported from the notebook
- **`sample_data.xlsx`** — Example Excel file exported from the notebook

---

## Key Concepts

| Function | Purpose | Common Parameters |
|----------|---------|-------------------|
| `pd.read_csv()` | Read CSV files | `encoding`, `sep`, `header` |
| `pd.read_excel()` | Read Excel files | `sheet_name`, `header` |
| `pd.read_json()` | Read JSON files | `orient`, `lines` |
| `df.to_csv()` | Export to CSV | `index`, `sep`, `encoding` |
| `df.to_excel()` | Export to Excel | `index`, `sheet_name` |
| `df.to_json()` | Export to JSON | `orient`, `indent` |

---

## Best Practices

✓ Always use `index=False` when exporting unless you need the index  
✓ Check encoding when reading CSV files (use `encoding='latin1'` or `encoding='utf-8'` if needed)  
✓ Install `openpyxl` for Excel support: `pip install openpyxl`  
✓ Use `df.head()` to preview data after reading  
✓ Handle file paths carefully (use relative or absolute paths)

---

## Installation Requirements

```bash
pip install pandas openpyxl
```

---

## Practice Exercises

1. Create a DataFrame with 5 columns and 10 rows of data
2. Export it to CSV, Excel, and JSON formats
3. Read each file back and verify the data
4. Try different `orient` options for JSON export
5. Practice reading files with different encodings
