# 📊 Day 12: String Manipulation in Pandas

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 12 focuses on **String Manipulation** in Pandas. Text data often needs cleaning and formatting before analysis. Pandas provides the `.str` accessor, which allows you to apply string methods to entire columns efficiently (vectorized operations) without using loops.

## Topics Covered

### 1. **The `.str` Accessor**

To access string methods in Pandas, you must use `.str` before the method name. This tells Pandas to treat the column values as strings.

```python
# Correct way to apply string methods
df['Name'].str.lower()
```

---

### 2. **Changing Case**

Standardize text casing for consistency.

```python
# Convert to lowercase
df['Name'].str.lower()

# Convert to uppercase
df['Name'].str.upper()

# Convert to title case (Capitalize first letter of each word)
df['Name'].str.title()
```

---

### 3. **Cleaning Whitespace**

Remove unwanted spaces that often creep into data.

```python
# Remove leading and trailing spaces
df['Name'].str.strip()

# Remove only leading spaces (left)
df['Name'].str.lstrip()

# Remove only trailing spaces (right)
df['Name'].str.rstrip()
```

---

### 4. **Splitting and Replacing**

Modify strings by splitting them or replacing parts.

#### Replace Substrings
Useful for removing currency symbols, fixing typos, or standardizing values.

```python
# Remove '$' and ',' from price column
df['Price'] = df['Price'].str.replace('$', '').str.replace(',', '')

# Replace pattern
df['Email'] = df['Email'].str.replace('.com', '.org')
```

#### Split Strings
Break a single column into multiple columns.

```python
# Split 'Full Name' into 'First Name' and 'Last Name'
df[['First', 'Last']] = df['Full_Name'].str.split(' ', expand=True)
```
- `expand=True`: Returns a DataFrame instead of a list.

---

### 5. **Filtering with String Methods**

Filter rows based on text patterns using boolean indexing.

```python
# Contains specific text
managers = df[df['Job Title'].str.contains("Manager")]

# Starts with specific text
sales_dept = df[df['Department'].str.startswith("Sales")]

# Ends with specific text
pdf_files = df[df['File Name'].str.endswith(".pdf")]
```

---

## Files in This Directory

- **`day_12_work.ipynb`**: The main tutorial notebook covering all string manipulation concepts with examples.
- **`challenge.ipynb`**: A practical challenge to clean an employee salary dataset (removing currency symbols, converting units, and changing data types).
- **`practice_exercise.ipynb`**: Additional exercises to reinforce learning.

---

## Key Concepts

- **Vectorization**: Pandas string operations are vectorized, meaning they are much faster than iterating through rows with a loop.
- **Chaining**: You can chain multiple string methods together (e.g., `str.strip().str.lower()`).
- **Regular Expressions**: Many `.str` methods accept regex for powerful pattern matching (e.g., in `replace` or `contains`).

---

## Common String Methods Summary

| Method | Description |
|--------|-------------|
| `lower()` / `upper()` | Converts case |
| `strip()` | Removes whitespace |
| `split(delim)` | Splits string by delimiter |
| `replace(a, b)` | Replaces substring 'a' with 'b' |
| `contains(pat)` | Checks if pattern exists (returns boolean) |
| `startswith(pat)` | Checks if string starts with pattern |
| `endswith(pat)` | Checks if string ends with pattern |
| `len()` | Returns length of string |

---

## Best Practices

✅ **Always use `.str`**: `df['col'].lower()` will fail; `df['col'].str.lower()` is correct.  
✅ **Handle Missing Values**: String methods on `NaN` values result in `NaN`. Use param `na=False` in `contains()` to avoid errors in boolean indexing.  
✅ **Check Data Types**: Ensure your column is of type `object` or `string` before applying these methods.  
