# 🧹 Day 05: Dropping Data and Handling Missing Values

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 05 focuses on data cleaning techniques including removing unwanted data and managing missing values in DataFrames. These are critical skills for preparing real-world data for analysis.

## Topics Covered

### 1. **Drop Data**

Remove columns from a DataFrame using the `drop()` method.

```python
# Drop a single column
df_sales = df_sales.drop(columns=['Date'])

# Drop multiple columns
df_sales = df_sales.drop(columns=['Units_Sold', 'Revenue'])
```

**Key Points:**
- Use `columns` parameter to specify which columns to drop
- Returns a new DataFrame by default
- Use `inplace=True` to modify the original DataFrame

**Example:**
```python
# Drop columns without modifying original
df_new = df.drop(columns=['Column1', 'Column2'])

# Drop columns and modify original
df.drop(columns=['Column1', 'Column2'], inplace=True)
```

---

## 2. **Handle Missing Data**

### Detect Missing Data

Identify missing values in your DataFrame:

```python
# Check which cells have missing values
print(df.isnull())

# Count missing values per column
print(df.isnull().sum())

# Get percentage of missing values
print((df.isnull().sum() / len(df)) * 100)
```

---

### Drop Missing Values (Not Recommended)

Remove rows with any missing values:

```python
df.dropna(inplace=True)
```

**⚠️ Warning:** This approach removes entire rows and may lose valuable data.

**When to use:**
- Very small percentage of missing data
- Missing data is random and not informative
- You have plenty of data to spare

---

### Fill Missing Values (Recommended)

#### Method 1: Fill with Default Value
```python
df.fillna(0, inplace=True)
```

#### Method 2: Replace Specific Values
```python
df['Age'] = df['Age'].replace('?', 0)
df['Salary'] = df['Salary'].replace('N/A', 0)
```

#### Method 3: Fill with Mean Value
```python
# Calculate mean from valid data
mean_age = df['Age'].mean()

# Replace missing values with mean
df['Age'].fillna(mean_age, inplace=True)
```

#### Method 4: Fill with Median or Mode
```python
# For skewed data, median is often better
median_salary = df['Salary'].median()
df['Salary'].fillna(median_salary, inplace=True)

# For categorical data, use mode
mode_department = df['Department'].mode()[0]
df['Department'].fillna(mode_department, inplace=True)
```

#### Method 5: Manual Updates
```python
# Update specific cells
df.loc[row_index, "column_name"] = new_value

# Update based on condition
df.loc[df['Age'] == 0, 'Age'] = 25
```

---

## 3. **Data Type Conversion**

Convert column data types when needed:

```python
# Convert to integer
df['Age'] = df['Age'].astype(int)

# Convert to float
df['Salary'] = df['Salary'].astype(float)

# Convert to string
df['ID'] = df['ID'].astype(str)

# Check data types
df.info()
```

---

## Workflow Example

1. **Load data** and identify missing values
   ```python
   df = pd.read_csv('customer_data.csv')
   print(df.isnull().sum())
   ```

2. **Replace placeholder values** (like '?') with 0
   ```python
   df.replace('?', 0, inplace=True)
   ```

3. **Convert data types** to appropriate types
   ```python
   df['Age'] = df['Age'].astype(int)
   ```

4. **Calculate statistics** (mean, median, etc.)
   ```python
   mean_age = df[df['Age'] > 0]['Age'].mean()
   ```

5. **Fill missing values** with appropriate values
   ```python
   df.loc[df['Age'] == 0, 'Age'] = mean_age
   ```

6. **Manually correct** specific cells if needed
   ```python
   df.loc[5, 'Age'] = 30
   ```

7. **Verify results** using `info()` and `head()`
   ```python
   df.info()
   print(df.head())
   ```

---

## Files in This Directory

- **`day-05-work.ipynb`** — Main notebook with all exercises
- **`practice.ipynb`** — Additional practice problems
- **`customer_data.csv`** — Sample customer data with missing values
- **`practice_data.csv`** — Additional practice dataset

---

## Best Practices

✅ Use `fillna()` to preserve data when possible  
✅ Calculate statistics (mean, median) from valid data only  
✅ Understand the source of missing data  
✅ Use `inplace=True` to modify the original DataFrame  
✅ Use median for skewed distributions  
✅ Use mode for categorical variables  
❌ Avoid blindly dropping rows with missing values  
❌ Don't use inappropriate default values for filling  
❌ Don't calculate statistics including placeholder values (like 0 or '?')

---

## Key Methods

| Method | Purpose | When to Use |
|--------|---------|-------------|
| `df.isnull()` | Detect missing values | Check for NaN values |
| `df.dropna()` | Remove rows/columns with missing values | When missing data is minimal |
| `df.fillna()` | Fill missing values | Preserve data |
| `df.replace()` | Replace specific values | Clean placeholder values |
| `df.astype()` | Convert data types | Ensure correct types |
| `df.loc[]` | Update specific cells | Manual corrections |

---

## Common Strategies

```python
# Strategy 1: Fill numeric with mean
df['Age'].fillna(df['Age'].mean(), inplace=True)

# Strategy 2: Fill categorical with mode
df['Category'].fillna(df['Category'].mode()[0], inplace=True)

# Strategy 3: Forward fill (use previous value)
df['Status'].fillna(method='ffill', inplace=True)

# Strategy 4: Backward fill (use next value)
df['Status'].fillna(method='bfill', inplace=True)

# Strategy 5: Fill with specific value
df['Score'].fillna(0, inplace=True)
```

---

## Practice Exercises

1. Load a dataset with missing values
2. Count missing values in each column
3. Replace placeholder values ('?', 'N/A') with NaN
4. Calculate mean/median for numeric columns
5. Fill missing numeric values with mean
6. Fill missing categorical values with mode
7. Verify no missing values remain using `isnull().sum()`

**Challenge:** Create a dataset with various types of missing data and implement different strategies for each column!
