# 📊 Day 02: Previewing and Understanding Data

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 02 focuses on essential pandas techniques for exploring and understanding your data. These are fundamental skills for any data analysis workflow.

## Topics Covered

### 1. **Previewing the Data**

#### View First 10 Rows - `head()`
```python
df.head(10)
```
- Use `df.head(10)` to view the first 10 rows of your DataFrame
- Helps you quickly understand the structure and content of your data
- Default number of rows is 5 if no argument is provided

#### View Last 10 Rows - `tail()`
```python
df.tail(10)
```
- Use `df.tail(10)` to view the last 10 rows of your DataFrame
- Useful for checking the end of your dataset
- Helps identify patterns or anomalies at the end of the data

---

### 2. **Summary of Data - `info()` Method**

The `info()` method provides a comprehensive overview of your DataFrame:

```python
df.info()
```

**Output includes:**
- **Column Names**: All column names in the dataset
- **Data Types**: The data type of each column (int64, float64, object, etc.)
- **Non-Null Counts**: How many non-null values exist in each column
- **Memory Usage**: Total memory consumption of the DataFrame

**This is crucial for:**
- Identifying missing values
- Understanding data types before analysis
- Detecting potential data quality issues

---

### 3. **Descriptive Statistics - `describe()` Method**

The `describe()` method generates statistical summaries for numerical columns:

```python
df.describe()
```

**Statistics provided:**
- **Count**: Number of non-null values
- **Mean**: Average value
- **Std**: Standard deviation
- **Min**: Minimum value
- **25%, 50%, 75%**: Quartiles (25th, 50th/median, 75th percentile)
- **Max**: Maximum value

---

## Examples in Notebook

### Example 1: Sales Data Analysis
- Reads a CSV file with sales data containing 2823 rows and 25 columns
- Demonstrates `head()`, `tail()`, and `info()` on real-world sales dataset
- Shows handling of encoding issues (latin1 encoding)

### Example 2: Employee Data
- Creates a simple DataFrame with employee information
- Columns: Name, Age, Salary, Department
- Shows descriptive statistics for numerical columns (Age, Salary)

### Example 3: Student Grades
- Reads student grade data from CSV
- Demonstrates `head()` and `describe()` methods
- Shows statistics across StudentID, Midterm, and Final scores

---

## Files in This Directory

- **`day-02-work.ipynb`** — Main Jupyter notebook with all examples and exercises

---

## Key Learning Points

✓ Always start exploratory data analysis with `head()` and `tail()`  
✓ Use `info()` to understand data types and identify missing values  
✓ Use `describe()` to get statistical insights about numerical data  
✓ Handle encoding issues when reading CSV files  
✓ These methods are your first line of defense in data quality checks

---

## Key Methods

| Method | Purpose | Output |
|--------|---------|--------|
| `df.head()` | View first N rows | DataFrame preview |
| `df.tail()` | View last N rows | DataFrame preview |
| `df.info()` | Get DataFrame information | Column types, null counts, memory |
| `df.describe()` | Get statistical summary | Count, mean, std, min, max, quartiles |

---

## Practice Exercises

Try applying these techniques to your own dataset:

1. Load your CSV file with `pd.read_csv()`
2. Use `head()` to see the first few rows
3. Use `tail()` to see the last few rows
4. Run `info()` to check for missing values and data types
5. Run `describe()` to understand the distribution of numerical columns

**Challenge:** Find a dataset with missing values and practice identifying them using `info()`!
