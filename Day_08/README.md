# 📊 Day 08: Grouping Data in Pandas

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 08 introduces the powerful `groupby()` operation in Pandas. Learn how to split your data into groups, apply aggregation functions, and gain insights from categorical data. This is one of the most important techniques for data analysis and is fundamental to understanding patterns in your data.

## Topics Covered

### 1. **Basic GroupBy Operations**

Split data into groups based on column values and perform aggregations.

#### Group by Single Column
```python
# Group by a single column and calculate mean
df.groupby('Department').mean()

# Group by grade and get statistics
df.groupby('Grade').describe()
```

**How it works:**
- **Split**: Divide data into groups based on column values
- **Apply**: Perform an operation on each group
- **Combine**: Combine results into a new DataFrame

---

#### Group by Multiple Columns
```python
# Group by multiple columns
df.groupby(['Region', 'Category']).sum()

# Group by product and sales level
df.groupby(['Product', 'Sales_Level']).mean()
```

**Key Points:**
- First column creates main groups
- Second column creates subgroups within each main group
- Results in hierarchical/multi-level index

---

### 2. **Aggregation Functions**

Apply various statistical functions to grouped data.

#### Common Aggregation Methods
```python
# Sum of values in each group
df.groupby('Department')['Salary'].sum()

# Average (mean) for each group
df.groupby('Department')['Salary'].mean()

# Maximum value in each group
df.groupby('Category')['Sales'].max()

# Minimum value in each group
df.groupby('Category')['Sales'].min()

# Count items in each group
df.groupby('Region')['OrderID'].count()

# Standard deviation
df.groupby('Department')['GPA'].std()
```

---

#### Multiple Aggregations
```python
# Apply multiple aggregations
df.groupby('Region')['Sales'].agg(['sum', 'mean', 'count'])

# Different aggregations for different columns
df.groupby('Category').agg({
    'Sales': 'sum',
    'Quantity': 'mean',
    'Profit': ['sum', 'mean']
})
```

---

### 3. **Selecting Specific Columns**

Focus aggregation on specific columns.

```python
# Single column aggregation
df.groupby('Department')['Salary'].mean()

# Multiple column selection
df.groupby('Region')[['Sales', 'Profit']].sum()

# All numeric columns (default)
df.groupby('Category').mean()
```

---

## Practical Examples

### Example 1: Student Data Analysis
```python
import pandas as pd

# Load student data
df = pd.read_excel('students_data.xlsx')

# Average GPA by grade
avg_gpa_by_grade = df.groupby('Grade')['GPA'].mean()
print(avg_gpa_by_grade)

# Count students by gender
student_count = df.groupby('Gender')['StudentID'].count()
print(student_count)

# Average attendance by grade and gender
attendance = df.groupby(['Grade', 'Gender'])['Attendance'].mean()
print(attendance)
```

---

### Example 2: Sales Data Analysis
```python
# Load sales data
df = pd.read_csv('sales_data.csv')

# Total sales by region
total_sales = df.groupby('Region')['Sales'].sum()
print(total_sales)

# Average profit by product and category
avg_profit = df.groupby(['Category', 'Product'])['Profit'].mean()
print(avg_profit)

# Multiple statistics by region
sales_stats = df.groupby('Region')['Sales'].agg(['sum', 'mean', 'count', 'max', 'min'])
print(sales_stats)
```

---

### Example 3: Time-Series Grouping
```python
# Convert date column to datetime
df['Date'] = pd.to_datetime(df['Date'])

# Extract month and group
df['Month'] = df['Date'].dt.month
monthly_sales = df.groupby('Month')['Sales'].sum()
print(monthly_sales)

# Group by year and month
df['Year'] = df['Date'].dt.year
yearly_monthly = df.groupby(['Year', 'Month'])['Profit'].sum()
print(yearly_monthly)
```

---

## Files in This Directory

- **`day-08-work.ipynb`** — Introduction to `groupby` operations with student data examples
- **`practice.ipynb`** — Practice exercises using sales data with multiple grouping scenarios
- **`sales_data.csv`** — Dataset containing sales records (OrderID, Date, Region, Category, Product, Sales, Quantity, Profit)
- **`students_data.xlsx`** — Dataset containing student information (StudentID, Name, Grade, DOB, Gender, GPA, Attendance, Enrollment Status)

---

## Key Concepts

### The GroupBy Process

```
Original DataFrame
        ↓
    Split (by category)
        ↓
   Group 1 | Group 2 | Group 3
        ↓
   Apply (aggregation)
        ↓
  Result 1 | Result 2 | Result 3
        ↓
    Combine
        ↓
 Aggregated DataFrame
```

---

## Common Aggregation Functions

| Function | Purpose | Example |
|----------|---------|---------|
| `sum()` | Total of values | Total sales per region |
| `mean()` | Average value | Average salary per department |
| `median()` | Middle value | Median price per category |
| `count()` | Number of items | Number of orders per customer |
| `min()` | Minimum value | Lowest score per class |
| `max()` | Maximum value | Highest profit per product |
| `std()` | Standard deviation | Variability in grades |
| `var()` | Variance | Data spread |
| `agg()` | Multiple aggregations | Multiple stats at once |

---

## Best Practices

✅ Use `groupby()` to analyze categorical data  
✅ Choose aggregation functions based on your analysis goals  
✅ Use `agg()` for multiple aggregations simultaneously  
✅ Group by multiple columns for hierarchical analysis  
✅ Reset index if needed: `df.groupby('Col').sum().reset_index()`  
✅ Visualize grouped data for better insights  
❌ Don't forget numeric columns are aggregated by default  
❌ Don't group without a clear analytical question  
❌ Don't ignore the meaning of your aggregation in context

---

## Common Patterns

```python
# Basic group and aggregate
df.groupby('Category')['Sales'].sum()

# Multiple aggregations
df.groupby('Region').agg({
    'Sales': 'sum',
    'Profit': 'mean',
    'Quantity': 'count'
})

# Group with filtering
high_sales = df[df['Sales'] > 1000].groupby('Product')['Profit'].mean()

# Group and reset index for easier plotting
result = df.groupby('Month')['Sales'].sum().reset_index()

# Get top N groups
top_regions = df.groupby('Region')['Sales'].sum().nlargest(5)
```

---

## Advanced Techniques

### Custom Aggregation Functions
```python
# Define custom function
def range_calc(x):
    return x.max() - x.min()

# Apply custom function
df.groupby('Category')['Price'].agg(range_calc)
```

### Transform (Keep Original Shape)
```python
# Add group mean to each row
df['Dept_Avg_Salary'] = df.groupby('Department')['Salary'].transform('mean')
```

### Filter Groups
```python
# Keep only groups with more than 5 members
df.groupby('Department').filter(lambda x: len(x) > 5)
```

---

## Practice Exercises

1. Load a dataset with categorical variables (department, region, category, etc.)
2. Group by one column and calculate the mean of a numeric column
3. Group by one column and calculate sum, mean, count, max, and min
4. Group by multiple columns and analyze the hierarchical structure
5. Use `agg()` to apply multiple aggregations simultaneously
6. Create a pivot-like summary using `groupby()`
7. Group by date components (month, year) for time-series data

**Challenge:** 
- Find the top 3 products by total sales in each region
- Calculate the percentage contribution of each category to total sales
- Identify departments with above-average salaries and count employees in each!

---

## Real-World Applications

- **Sales Analysis**: Total revenue by product, region, or time period
- **HR Analytics**: Average salary by department, employee count by location
- **Student Performance**: Average grades by class, attendance by gender
- **E-commerce**: Customer purchase patterns, product popularity
- **Finance**: Portfolio performance by sector, risk analysis by category
