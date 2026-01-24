# Day 04: Adding Columns and Updating Data in Pandas

## Overview
This day focuses on manipulating DataFrames by adding new columns and updating existing data values in pandas.

## Topics Covered

### 1. Adding a Column
Learn how to add new columns to a DataFrame.

#### Method 1: Using Square Brackets
```python
df["Bonus"] = df["Salary"] * 0.1
df["TotalSalary"] = df["Salary"] + df["Bonus"]
```
- Simple and straightforward approach
- Add columns based on calculations from existing columns

#### Method 2: Using `insert()` Method
```python
df.insert(0, 'EmpID', emp_id)
df.insert(4, 'Country', country)
```
- Control the position where the column is inserted
- `insert()` takes parameters: position (index), column name, and values
- Useful when you need columns in a specific order

### 2. Updating Data
Update existing values in a DataFrame using `loc()`.

```python
df.loc[3, "Salary"] = 80000  # Update specific row and column
```
- Use `loc[]` for label-based indexing
- Access specific rows and columns with the syntax: `df.loc[row, column]`
- Modify individual cell values or multiple values at once

## Files in This Directory
- `day-04-work.ipynb` - Main notebook with all exercises and examples
- `practice.ipynb` - Additional practice problems
- `student_results.csv` - Sample data file for practice
- `EmployeeID_Department.csv` - Employee data for practice exercises

## Key Concepts
- DataFrame column operations
- Positional vs label-based indexing with `loc()`
- Data manipulation and transformation
- Working with calculated columns

## Practice Exercises
The `practice.ipynb` notebook contains additional exercises to reinforce these concepts.
