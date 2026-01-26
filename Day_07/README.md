# 🔢 Day 07: Sorting & Aggregation

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 07 demonstrates sorting and basic aggregation techniques in Pandas. Learn how to organize your data in meaningful ways and compute summary statistics to gain insights from your datasets.

## Topics Covered

### 1. **Sorting Data**

Sort DataFrames by one or more columns to organize and analyze data effectively.

#### Sort by Single Column
```python
# Sort by EmployeeID (ascending)
df.sort_values(by='EmployeeID', inplace=True)

# Sort by Salary (descending)
df.sort_values(by='Salary', ascending=False, inplace=True)
```

**Key Points:**
- Use `by` parameter to specify the column
- `ascending=True` (default) for ascending order
- `ascending=False` for descending order
- Use `inplace=True` to modify the original DataFrame

---

#### Sort by Multiple Columns
```python
# Sort by Department, then by Salary (descending)
df.sort_values(by=['Department', 'Salary'], 
               ascending=[True, False], 
               inplace=True)

# Sort by FirstName, then LastName
df.sort_values(by=['FirstName', 'LastName'], inplace=True)
```

**Key Points:**
- Pass a list of column names to sort by multiple columns
- First column is the primary sort
- Subsequent columns break ties
- Can specify different sort orders for each column

---

#### Sort by Index
```python
# Sort by index (row labels)
df.sort_index(inplace=True)

# Sort by index in descending order
df.sort_index(ascending=False, inplace=True)
```

---

### 2. **Descriptive Statistics - `describe()` Method**

Get a comprehensive statistical summary of your DataFrame.

```python
# Summary statistics for all numeric columns
summary = df.describe()
print(summary)
```

**Output includes:**
- **count**: Number of non-null values
- **mean**: Average value
- **std**: Standard deviation (spread of data)
- **min**: Minimum value
- **25%**: First quartile (25th percentile)
- **50%**: Median (50th percentile)
- **75%**: Third quartile (75th percentile)
- **max**: Maximum value

---

### 3. **Column-Specific Aggregation**

Perform specific calculations on individual columns.

```python
# Salary column aggregations
salary_sum = df['Salary'].sum()
salary_mean = df['Salary'].mean()
salary_median = df['Salary'].median()
salary_std = df['Salary'].std()
salary_min = df['Salary'].min()
salary_max = df['Salary'].max()

# Print results
print(f"Total Salary: ${salary_sum:,.2f}")
print(f"Average Salary: ${salary_mean:,.2f}")
print(f"Median Salary: ${salary_median:,.2f}")
print(f"Salary Std Dev: ${salary_std:,.2f}")
print(f"Min Salary: ${salary_min:,.2f}")
print(f"Max Salary: ${salary_max:,.2f}")
```

---

## Practical Examples

### Example 1: Employee Data Sorting
```python
import pandas as pd

# Load employee data
df = pd.read_csv('unsorted_data.csv')

# Sort by EmployeeID
df.sort_values(by='EmployeeID', inplace=True)

# Sort by Salary (highest first)
df.sort_values(by='Salary', ascending=False, inplace=True)

# Sort by Department, then Salary
df.sort_values(by=['Department', 'Salary'], 
               ascending=[True, False], 
               inplace=True)
```

### Example 2: Date Sorting
```python
# Convert to datetime first
df['JoinDate'] = pd.to_datetime(df['JoinDate'])

# Sort by join date (earliest first)
df.sort_values(by='JoinDate', inplace=True)

# Sort by join date (most recent first)
df.sort_values(by='JoinDate', ascending=False, inplace=True)
```

### Example 3: Aggregation Analysis
```python
# Get overall statistics
print(df.describe())

# Analyze specific column
print(f"Total Employees: {len(df)}")
print(f"Average Salary: ${df['Salary'].mean():,.2f}")
print(f"Salary Range: ${df['Salary'].min():,.2f} - ${df['Salary'].max():,.2f}")
print(f"Median Salary: ${df['Salary'].median():,.2f}")
```

---

## Files in This Directory

- **`day-07-work.ipynb`** — Main Jupyter notebook with sorting and aggregation examples
- **`unsorted_data.csv`** — Sample dataset containing employee information (EmployeeID, FirstName, Salary, JoinDate, etc.)

---

## Key Methods

| Method | Purpose | Common Parameters |
|--------|---------|-------------------|
| `df.sort_values()` | Sort by column values | `by`, `ascending`, `inplace` |
| `df.sort_index()` | Sort by index | `ascending`, `inplace` |
| `df.describe()` | Statistical summary | None |
| `df['col'].sum()` | Calculate sum | None |
| `df['col'].mean()` | Calculate average | None |
| `df['col'].median()` | Calculate median | None |
| `df['col'].std()` | Calculate standard deviation | None |
| `df['col'].min()` | Find minimum | None |
| `df['col'].max()` | Find maximum | None |
| `df['col'].count()` | Count non-null values | None |

---

## Best Practices

✓ Use `inplace=True` to modify the original DataFrame  
✓ Use `ascending=False` to sort in descending order  
✓ Sort by multiple columns for better organization  
✓ Convert dates to datetime before sorting  
✓ Use `describe()` for quick statistical overview  
✓ Use specific aggregation methods for targeted analysis  
❌ Don't forget to set `inplace=True` if you want to modify the original  
❌ Don't assume data is sorted unless you explicitly sort it

---

## Common Patterns

```python
# Sort by date (most recent first)
df.sort_values(by='Date', ascending=False, inplace=True)

# Sort alphabetically
df.sort_values(by='Name', inplace=True)

# Multi-level sorting
df.sort_values(by=['Category', 'Price'], 
               ascending=[True, False], 
               inplace=True)

# Quick stats for a column
print(df['Sales'].describe())

# Multiple aggregations at once
stats = {
    'Total': df['Amount'].sum(),
    'Average': df['Amount'].mean(),
    'Count': df['Amount'].count()
}
print(stats)
```

---

## Understanding `inplace` Parameter

```python
# Without inplace (creates new DataFrame)
df_sorted = df.sort_values(by='Salary')
# Original df is unchanged, df_sorted has sorted data

# With inplace (modifies original)
df.sort_values(by='Salary', inplace=True)
# Original df is now sorted
```

---

## Practice Exercises

1. Load a dataset with employee or student information
2. Sort by a single column (ascending and descending)
3. Sort by multiple columns with different sort orders
4. Sort by a date column (after converting to datetime)
5. Use `describe()` to get overall statistics
6. Calculate sum, mean, median, min, and max for a numeric column
7. Compare sorted vs unsorted data to understand the impact

**Challenge:** Create a dataset with sales data and find the top 5 highest sales, bottom 5 lowest sales, and calculate average sales by category!