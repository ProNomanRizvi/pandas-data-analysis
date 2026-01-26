# 🔍 Day 03: Data Shape, Columns, Selection & Filtering

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 03 covers fundamental techniques for understanding the structure of your data and selecting/filtering specific subsets. These skills are essential for data exploration and manipulation.

## Topics Covered

### 1. **Shape of Data - `shape` Attribute**

The `shape` attribute returns a tuple with two values:

```python
print(f"Shape of Data: {df.shape}")
# Output: (4, 4)  # 4 rows, 4 columns
```

- **First value**: Number of rows
- **Second value**: Number of columns

**Why is this important?**
- Quick way to understand data dimensions
- Useful for validating data after filtering or merging
- Helps detect missing rows or unexpected data changes

---

### 2. **Column Names - `columns` Attribute**

Access all column names in your DataFrame:

```python
print(f"Columns Name: {df.columns}")
# Output: Index(['Name', 'Age', 'Salary', 'Department'], dtype='object')
```

**Use cases:**
- Review all available columns
- Check for typos or unexpected column names
- Reference columns programmatically
- Validate data structure

---

## 3. **Selecting Columns**

Pandas provides multiple ways to select columns, and the choice affects whether you get a **Series** (1D) or **DataFrame** (2D).

### **Return a Series (1D)**

#### Bracket Notation
```python
# Select a single column as a Series
customer_names = df['Customer Name']
```

#### Dot Notation
```python
# Alternative syntax (works only if column name has no spaces)
customer_names = df.column_name
```

**⚠️ Limitations of Dot Notation:**
- Cannot use if column name contains spaces
- Cannot use if name conflicts with DataFrame methods (e.g., `count`, `sum`, `mean`)

---

### **Return a DataFrame (2D)**

#### Double Bracket Notation (Multiple Columns)
```python
# Select multiple columns as a DataFrame
customer_data = df[['Customer Name', 'Country', 'City']]
```

#### Single Column as DataFrame
```python
# Single column but returned as DataFrame (not Series)
customer_data = df[['Customer Name']]
```

**Key Concept:** The outer brackets are for indexing, the inner brackets define a list of column names.

---

## 4. **Filtering Rows**

Filter rows based on conditions to extract specific subsets of your data.

### **Single Condition**

```python
# Select rows where City equals "Henderson"
customers = df[df["City"] == "Henderson"]
```

### **Multiple Conditions with AND (`&`)**

```python
# Find employees with Salary > 30000 AND Department = "IT"
high_salary_IT = df[(df["Salary"] > 30000) & (df["Department"] == "IT")]
```

⚠️ **Important:** Use `&` (not `and`), `|` (not `or`), and `~` (not `not`) for filtering

### **Multiple Conditions with OR (`|`)**

```python
# Find customers from either Karachi or Lahore
cities = df[(df["City"] == "Karachi") | (df["City"] == "Lahore")]
```

### **NOT Condition (`~`)**

```python
# Find all employees NOT in IT department
not_it = df[~(df["Department"] == "IT")]
```

---

## Practical Examples

### Example 1: Employee Data Structure
**Sample Data:**
- Name, Age, Salary, Department
- 4 employees

**Outputs:**
- Shape: (4, 4)
- Columns: Name, Age, Salary, Department

### Example 2: Superstore Dataset
**Sample Data:**
- Customer Name, Country, City, Sales, Profit, etc.
- Large dataset with hundreds of rows

**Tasks:**
- Check shape and columns
- Select specific columns (Customer Name, Country, City)
- Filter rows by City

### Example 3: Pakistan Employee Data
**Sample Data:**
```python
Name: ["Ali", "Bilal", "Ramzan", "Fatima", "Moosa"]
Salary: [20000, 40000, 50000, 20000, 30000]
Department: ["IT", "HR", "IT", "Finance", "IT"]
Age: [25, 30, 35, 40, 45]
Gender: ["Male", "Male", "Male", "Female", "Male"]
City: ["Karachi", "Lahore", "Islamabad", "Peshawar", "Quetta"]
Country: ["Pakistan", "Pakistan", "Pakistan", "Pakistan", "Pakistan"]
```

**Filtering Examples:**
- High salary employees (> 30000)
- High salary IT employees (salary > 30000 AND department = IT)
- Employees from specific cities (Karachi OR Lahore)
- Employees not in IT department

---

## Files in This Directory

- **`day-03-work.ipynb`** — Main Jupyter notebook with all exercises and examples
- **`PracticeOnRealData.ipynb`** — Additional practice with real datasets
- **`EmployeeID_Department.csv`** — Sample employee data for practice

---

## Key Learning Points

✓ Use `shape` to quickly understand data dimensions  
✓ Use `columns` to review all available columns  
✓ Use bracket notation `df['col']` for Series (1D)  
✓ Use double bracket notation `df[['col1', 'col2']]` for DataFrame (2D)  
✓ Use `&` for AND, `|` for OR, `~` for NOT when filtering  
✓ Always wrap multiple conditions in parentheses  
✓ Always use `&`, `|`, `~` instead of `and`, `or`, `not`

---

## Key Functions & Attributes

| Function/Attribute | Purpose |
|-------------------|---------|
| `df.shape` | Returns tuple (rows, columns) |
| `df.columns` | Returns all column names |
| `df['column_name']` | Select single column as Series |
| `df[['col1', 'col2']]` | Select multiple columns as DataFrame |
| `df[df['col'] == value]` | Filter rows by condition |
| `df[(cond1) & (cond2)]` | Filter with AND logic |
| `df[(cond1) \| (cond2)]` | Filter with OR logic |
| `df[~(condition)]` | Filter with NOT logic |

---

## Practice Exercises

1. Load your dataset
2. Print the shape and columns
3. Select 3-4 specific columns as a DataFrame
4. Filter rows with a single condition
5. Combine two conditions using AND
6. Combine two conditions using OR
7. Use NOT to exclude specific values

**Challenge:** Create a complex filter with 3+ conditions!
