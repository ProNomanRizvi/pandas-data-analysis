# ➕ Day 04: Adding Columns and Updating Data

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 04 focuses on manipulating DataFrames by adding new columns and updating existing data values. These are essential operations for data transformation and feature engineering.

## Topics Covered

### 1. **Adding Columns**

Learn how to add new columns to a DataFrame using different methods.

#### Method 1: Using Square Brackets
```python
# Add a new column with calculated values
df["Bonus"] = df["Salary"] * 0.1
df["TotalSalary"] = df["Salary"] + df["Bonus"]
```

**Key Points:**
- Simple and straightforward approach
- Add columns based on calculations from existing columns
- New column is appended at the end
- Most commonly used method

**Example:**
```python
# Creating derived columns
df["Full_Name"] = df["First_Name"] + " " + df["Last_Name"]
df["Annual_Salary"] = df["Monthly_Salary"] * 12
```

---

#### Method 2: Using `insert()` Method
```python
# Insert column at specific position
df.insert(0, 'EmpID', emp_id)
df.insert(4, 'Country', country)
```

**Key Points:**
- Control the position where the column is inserted
- Syntax: `df.insert(position, column_name, values)`
- Position is 0-indexed (0 = first column)
- Useful when you need columns in a specific order

**Example:**
```python
# Insert ID column at the beginning
employee_ids = [1001, 1002, 1003, 1004]
df.insert(0, 'EmployeeID', employee_ids)

# Insert country column at position 4
countries = ['Pakistan', 'Pakistan', 'Pakistan', 'Pakistan']
df.insert(4, 'Country', countries)
```

---

### 2. **Updating Data**

Update existing values in a DataFrame using `loc[]`.

```python
# Update specific row and column
df.loc[3, "Salary"] = 80000

# Update multiple cells
df.loc[0, "Department"] = "Engineering"
df.loc[2, "Age"] = 28
```

**Key Points:**
- Use `loc[]` for label-based indexing
- Syntax: `df.loc[row_index, column_name]`
- Access specific rows and columns precisely
- Modify individual cell values or multiple values at once

**Example:**
```python
# Update salary for a specific employee
df.loc[df['Name'] == 'Ali', 'Salary'] = 45000

# Update multiple columns for a row
df.loc[5, ['Salary', 'Department']] = [55000, 'IT']

# Conditional updates
df.loc[df['Age'] < 25, 'Experience'] = 'Junior'
```

---

## Practical Examples

### Example 1: Employee Bonus Calculation
```python
import pandas as pd

# Sample employee data
data = {
    'Name': ['Ali', 'Sara', 'Ahmed', 'Fatima'],
    'Salary': [30000, 45000, 35000, 50000],
    'Department': ['IT', 'HR', 'Finance', 'IT']
}
df = pd.DataFrame(data)

# Add bonus column (10% of salary)
df['Bonus'] = df['Salary'] * 0.10

# Add total compensation
df['Total_Compensation'] = df['Salary'] + df['Bonus']
```

### Example 2: Adding ID and Country Columns
```python
# Insert employee IDs at the beginning
emp_ids = [1001, 1002, 1003, 1004]
df.insert(0, 'EmployeeID', emp_ids)

# Insert country column
countries = ['Pakistan'] * len(df)
df.insert(3, 'Country', countries)
```

---

## Files in This Directory

- **`day-04-work.ipynb`** — Main notebook with all exercises and examples
- **`practice.ipynb`** — Additional practice problems
- **`student_results.csv`** — Sample data file for practice
- **`EmployeeID_Department.csv`** — Employee data for practice exercises

---

## Key Concepts

| Method | Purpose | When to Use |
|--------|---------|-------------|
| `df['new_col'] = values` | Add column at end | Most common, simple additions |
| `df.insert(pos, name, values)` | Add column at specific position | When column order matters |
| `df.loc[row, col] = value` | Update specific cell | Modify existing data |
| `df.loc[condition, col] = value` | Conditional updates | Update based on criteria |

---

## Best Practices

✓ Use square brackets for simple column additions  
✓ Use `insert()` when column order is important  
✓ Use `loc[]` for precise data updates  
✓ Ensure new column values match DataFrame length  
✓ Use vectorized operations for calculated columns  
✓ Be careful with data types when adding columns

---

## Common Patterns

```python
# Create calculated column
df['Total'] = df['Quantity'] * df['Price']

# Create conditional column
df['Category'] = df['Age'].apply(lambda x: 'Senior' if x > 60 else 'Adult')

# Insert at beginning
df.insert(0, 'ID', range(1, len(df) + 1))

# Update based on condition
df.loc[df['Score'] > 90, 'Grade'] = 'A'
```

---

## Practice Exercises

1. Create a DataFrame with employee names and salaries
2. Add a "Bonus" column (15% of salary)
3. Add a "Tax" column (10% of salary)
4. Calculate "Net_Salary" (Salary + Bonus - Tax)
5. Insert an "EmployeeID" column at the beginning
6. Update a specific employee's salary using `loc[]`
7. Update all salaries in a specific department

**Challenge:** Create a grading system that updates letter grades based on numerical scores!
