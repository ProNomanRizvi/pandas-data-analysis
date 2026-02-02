# 🧱 Day 15: Reshaping Data (Stack & Unstack)

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 15 handles **Hierarchical Data (MultiIndex)** reshaping using `stack()` and `unstack()`. These methods are essential when working with datasets that have multiple levels of headers or indices, allowing you to compress (stack) or expand (unstack) your data structure.

## Topics Covered

### 1. **Loading Multi-Level Data**

When reading Excel or CSV files with multiple header rows, use the `header` parameter.

```python
# Load data with 2 levels of headers
df = pd.read_excel("stock_data.xlsx", header=[0, 1])
```

### 2. **Stack()**

The `stack()` function moves the **innermost column headers** into the **rows** (index). This makes the DataFrame "taller".

*   **Usage**: Useful for normalizing data or creating a time-series friendly format.
*   **Parameters**: `level` (defaults to -1, the innermost level).

```python
# Move the "Company" level from columns to rows
df.stack(level=1)
```

### 3. **Unstack()**

The `unstack()` function is the inverse of `stack()`. It moves the **innermost row index** back into the **columns**. This makes the DataFrame "wider".

*   **Usage**: Useful for creating pivot-table style reports.

```python
# Move the inner index level back to columns
df.unstack()
```

---

## Files in This Directory

-   **`day-15-work.ipynb`**: The main tutorial notebook demonstrating stack and unstack operations.
-   **`stock_data.xlsx`**: A sample Excel file with 2-level headers (Metric, Company).
-   **`financial_data.xlsx`**: A complex sample Excel file with 3-level headers for advanced reshaping.

---

## Key Concepts

| Method | Direction | Effect | Analogy |
| :--- | :--- | :--- | :--- |
| **Stack** | Columns → Rows | Taller, Narrower | Compressing headers into data |
| **Unstack** | Rows → Columns | Shorter, Wider | Expanding data into a table |

---

## Best Practices

✅ **Check Header Levels**: Before stacking, inspect `df.columns` to understand your MultiIndex structure.
✅ **Handle NaNs**: Stacking/Unstacking may introduce `NaN` values if the data is not perfectly symmetrical; use `fillna()` if necessary.
✅ **Reset Index**: After stacking, you often want to use `reset_index()` to convert the MultiIndex into standard columns for further analysis.
