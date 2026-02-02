# 📊 Day 16: Crosstab (Contingency Tables)

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 16 introduces **Crosstabs** (Cross-Tabulation). The `pd.crosstab()` function is used to compute a simple frequency table of two (or more) factors. It essentially counts the number of occurrences of combinations of values, making it ideal for analyzing the relationship between categorical variables.

## Topics Covered

### 1. **Basic Crosstab**

The simplest usage involves passing two Series: one for the index (rows) and one for the columns.

```python
import pandas as pd

# Count occurances of Handedness by Nationality
pd.crosstab(df.Nationality, df.Handedness)
```

**Result:** A table showing how many Left/Right-handed people are in each Nationality.

### 2. **Margins (Subtotals)**

You can add row and column subtotals by calculating margins.

```python
# Add 'All' row/column containing totals
pd.crosstab(df.Nationality, df.Handedness, margins=True)
```

### 3. **Multi-Level Crosstab**

You can pass a list of multiple columns to create a hierarchical table.

```python
# Breakdown by Sex AND Nationality
pd.crosstab(df.Sex, [df.Handedness, df.Nationality])
```

### 4. **Normalization (Percentages)**

Instead of raw counts, you can view the data as percentages (probabilities).

*   `normalize='index'`: Row percentages (rows sum to 100%).
*   `normalize='columns'`: Column percentages.
*   `normalize='all'`: Percentage of the grand total.

```python
# Show percentage distribution across rows
pd.crosstab(df.Sex, df.Handedness, normalize='index')
```

---

## Files in This Directory

-   **`day-16-work.ipynb`**: The tutorial notebook demonstrating various `crosstab` examples.
-   **`demographics.xlsx`**: Sample dataset containing Nationality, Sex, Age, and Handedness data.

---

## Key Concepts

| Feature | Description |
| :--- | :--- |
| **Frequency Table** | A table that displays the frequency of various outcomes in a sample. |
| **Contingency Table** | Another name for a cross-tabulation table. |
| **Pivot Table vs Crosstab** | `pivot_table` is more general and can handle aggregation of values. `crosstab` is specialized for counting/frequencies (though it can assume `pivot_table` functionality with `values` and `aggfunc`). |

---

## Best Practices

✅ **Use for Categorical Data**: Crosstab is best suited for analyzing variables with a limited set of unique values (e.g., Yes/No, Low/Med/High).  
✅ **Check Margins**: Always use `margins=True` when you need to understand the sample size context of your segments.  
✅ **Normalize for Comparison**: Use `normalize` when comparing groups of different sizes to see the *relative* distribution.
