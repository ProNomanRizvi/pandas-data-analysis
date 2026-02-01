# 🔄 Day 13: Advanced Reshaping (Pivot)

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 13 covers **Advanced Reshaping** techniques using `pivot()` and `pivot_table()`. These functions allow you to transform data from a "long" format (tidy data) to a "wide" format, making it easier to analyze relationships between variables and view data hierarchically.

## Topics Covered

### 1. **Basic Pivoting**

The `pivot()` function is used to reshape data based on index, columns, and values. It assumes there are **no duplicate values** for the specified index/column pairs.

```python
# Reshape so Dates are rows and Cities are columns
df.pivot(index="date", columns="city")

# Select specific values (e.g., only Humidity)
df.pivot(index="date", columns="city", values="humidity")
```

---

### 2. **Pivot Table (Handling Duplicates)**

When your data contains duplicate entries for the same index/column pair, `pivot()` will raise an error. Instead, use `pivot_table()`, which aggregates duplicate values.

```python
# Default aggregation is 'mean'
df.pivot_table(index="city", columns="date", values="humidity")
```

---

### 3. **Custom Aggregation**

You can specify how to aggregate data using the `aggfunc` parameter.

```python
# Sum of values
df.pivot_table(index="city", columns="date", aggfunc="sum")

# Count occurrences
df.pivot_table(index="city", columns="date", aggfunc="count")

# Multiple aggregations
df.pivot_table(index="city", columns="date", aggfunc=["sum", "mean"])
```

---

### 4. **Margins (Subtotals)**

Add a row and column for "All" (subtotals) using `margins=True`.

```python
df.pivot_table(index="city", columns="date", margins=True)
```

---

### 5. **Time-Series Grouping**

Use `pd.Grouper` inside a pivot table to aggregate data by frequency (e.g., Monthly) instead of individual dates.

```python
# Convert to datetime first
df['date'] = pd.to_datetime(df['date'])

# Group by Month End ('ME')
df.pivot_table(index=pd.Grouper(freq='ME', key='date'), columns='city')
```

---

## Files in This Directory

- **`day-13-work.ipynb`**: The main tutorial notebook covering pivot and pivot table techniques.
- **`weather_data.csv`**: A simplified dataset with unique date-city combinations for basic pivoting.
- **`weather_data_extended.csv`**: A dataset containing duplicate entries to demonstrate pivot tables.
- **`combined_weather.csv`**: A larger dataset used for time-series grouping examples.

---

## Key Concepts

| Function | Usage | Duplicates? | Default Aggregation |
| :--- | :--- | :--- | :--- |
| `pivot()` | Simple reshaping (Index/Column/Value) | **No** (Raises Error) | None |
| `pivot_table()` | Reshaping with aggregation | **Yes** | `mean` |
| `pd.Grouper()` | Time-based grouping inside pivot | N/A | N/A |

---

## Best Practices

✅ **Check for Duplicates**: Use `pivot()` only when you are certain your index/column pairs are unique. Defaults to `pivot_table()` otherwise.  
✅ **Datetime Conversion**: Always convert date columns to actual datetime objects (`pd.to_datetime`) before performing time-series analysis or grouping.  
✅ **Use Margins**: Enable `margins=True` to quickly see overall column and row averages/sums without extra code.  
✅ **Readable Data**: Pivoting is excellent for creating reports or heatmaps (e.g., using Seaborn) from your data.

---

## Practice Exercises

1.  Read `weather_data.csv` and pivot it to show **Temperature** by city.
2.  Read `weather_data_extended.csv` and find the **Max** humidity per city using `pivot_table`.
3.  Use `pd.Grouper` to calculate the **average temperature** by month for each city in `combined_weather.csv`.
4.  Create a pivot table that shows both the **sum** and **mean** of temperature for each city.
