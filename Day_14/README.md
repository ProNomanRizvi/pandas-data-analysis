# 🔄 Day 14: Reshaping Data (Melt)

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 14 explores the **Melt** function in Pandas (`pd.melt()`). Melting is the process of transforming a DataFrame from a "wide" format (where variables are headers) to a "long" format (where variables are row values). This is essentially the reverse of pivoting.

## Topics Covered

### 1. **The Melt Function**

The `melt()` function unpivots a DataFrame, converting columns into rows. This is often necessary for preparing data for visualization libraries (like seaborn or altair) or machine learning models that expect tidy data.

### 2. **Basic Usage**

Suppose we have a DataFrame where cities are columns:

| day | chicago | chennai | berlin |
| :--- | :--- | :--- | :--- |
| Monday | 32 | 75 | 41 |

We want to reshape this so "city" becomes a variable (column).

```python
import pandas as pd

# Load data into DataFrame df
df = pd.read_csv("weather_data.csv")

# Melt the DataFrame
df_melted = pd.melt(df, id_vars=["day"], var_name="city", value_name="temperature")
```

### 3. **Parameters**

- **`id_vars`**: Columns to keep as identifier variables (preserve these columns).
- **`var_name`**: Name of the new column created from the old headers (e.g., "city").
- **`value_name`**: Name of the new column populated with the values (e.g., "temperature").

**Resulting Structure:**

| day | city | temperature |
| :--- | :--- | :--- |
| Monday | chicago | 32 |
| Monday | chennai | 75 |
| ... | ... | ... |

---

### 4. **Filtering Melted Data**

Once data is in long format, it's easy to filter for specific groups.

```python
# Select all data for Berlin
berlin_data = df_melted[df_melted['city'] == 'berlin']
```

---

## Files in This Directory

- **`day-14-work.ipynb`**: The tutorial notebook demonstrating the `melt` function.
- **`weather_data.csv`**: Sample dataset in wide format used for the examples.

---

## Key Concepts

| Concept | Description |
| :--- | :--- |
| **Wide Format** | Variables are spread across multiple columns (e.g., separate columns for each city). |
| **Long Format** | Variables are in a single column, with another column identifying the variable name (Tidy Data). |
| **Pivoting** | Long → Wide |
| **Melting** | Wide → Long |

---

## Best Practices

✅ **Use Meaningful Names**: Always specify `var_name` and `value_name` to make your reshaped DataFrame self-explanatory.  
✅ **Identify Keys**: Correctly choose your `id_vars`. These are the columns that define the entity (like ID, Date, Name) that the measurements belong to.  
✅ **Tidy Data**: Melting is a key step in "Tidying" your data (One observation per row, one variable per column).
