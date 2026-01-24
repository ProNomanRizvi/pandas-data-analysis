# Day 05: Dropping Data and Handling Missing Values

## Overview
This day focuses on data cleaning techniques including removing unwanted data and managing missing values in DataFrames.

## Topics Covered

### 1. Drop Data
Remove columns from a DataFrame using the `drop()` method.

```python
# Drop a single column
df_sales = df_sales.drop(columns=['Date'])

# Drop multiple columns
df_sales = df_sales.drop(columns=['Units_Sold'])
```

**Key Points:**
- Use `columns` parameter to specify which columns to drop
- Returns a new DataFrame by default
- Use `inplace=True` to modify the original DataFrame

---

## 2. Handle Missing Data

### Detect Missing Data
Identify missing values in your DataFrame:

```python
# Check which cells have missing values
print(df.isnull())

# Count missing values per column
print(df.isnull().sum())
```

### Drop Missing Values (Not Recommended)
Remove rows with any missing values:

```python
df.dropna(inplace=True)
```

**Warning:** This approach removes entire rows and may lose valuable data.

### Fill Missing Values (Recommended)

#### Method 1: Fill with Default Value
```python
df.fillna(default_value, inplace=True)
```

#### Method 2: Replace Specific Values
```python
df['Age'] = df['Age'].replace('?', 0)
```

#### Method 3: Fill with Mean Value
```python
mean_age = df['Age'].mean()
df['Age'].replace(0, mean_age, inplace=True)
```

#### Method 4: Manual Updates
```python
df.loc[row_index, "column_name"] = new_value
```

---

## 3. Data Type Conversion

Convert column data types when needed:

```python
# Convert to integer
df['Age'] = df['Age'].astype(int)

# Check data types
df.info()
```

---

## Workflow Example

1. **Load data** and identify missing values
2. **Replace placeholder values** (like '?') with 0
3. **Convert data types** to appropriate types (int, float, etc.)
4. **Calculate statistics** (mean, median, etc.)
5. **Fill missing values** with appropriate values
6. **Manually correct** specific cells if needed
7. **Verify results** using `info()` and `head()`

---

## Files in This Directory
- `day-05-work.ipynb` - Main notebook with all exercises
- `practice.ipynb` - Additional practice problems
- `customer_data.csv` - Sample customer data with missing values
- `practice_data.csv` - Additional practice dataset

## Best Practices
- ✅ Use `fillna()` to preserve data when possible
- ✅ Calculate statistics (mean, median) from valid data
- ✅ Understand the source of missing data
- ✅ Use `inplace=True` to modify the original DataFrame
- ❌ Avoid blindly dropping rows with missing values
- ❌ Don't use inappropriate default values for filling

## Key Methods
| Method | Purpose |
|--------|---------|
| `isnull()` | Detect missing values |
| `dropna()` | Remove rows/columns with missing values |
| `fillna()` | Fill missing values |
| `replace()` | Replace specific values |
| `astype()` | Convert data types |
| `loc[]` | Update specific cells |
