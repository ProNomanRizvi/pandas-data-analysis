# 📈 Day 06: Data Interpolation in Pandas

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 06 explores various **Interpolation** techniques using Pandas. Interpolation is a crucial step in data preprocessing, primarily used to handle missing values (NaN) while preserving data integrity and maintaining trends. Unlike simple filling methods, interpolation estimates missing values mathematically based on surrounding data points.

## Why Interpolation?

Dealing with missing data is a common challenge in Data Science:
- **Dropping values** → Leads to data loss
- **Filling with mean/median** → Might distort the data distribution
- **Interpolation** → Provides a mathematical approach to estimate missing values based on other data points

### Key Objectives:
- **Preserve Data Integrity:** Estimate values without altering the overall structure
- **Smooth Trends:** Maintain the continuity of data, especially in time series
- **Avoid Data Loss:** Retain rows/columns that would otherwise be discarded

---

## Topics Covered

### 1. **Linear Interpolation**

The default method. It estimates missing values by connecting two known data points with a straight line.

```python
# Linear interpolation (default)
df.interpolate(method='linear', inplace=True)

# Or explicitly specify
df['Sales'].interpolate(method='linear', inplace=True)
```

**How it works:**
- Finds the nearest non-null values before and after
- Draws a straight line between them
- Estimates missing values along that line

**Best for:**
- Data that follows a generally linear trend
- Regularly spaced data points
- Simple, straightforward interpolation needs

---

### 2. **Time-Weighted Interpolation**

Crucial for time-series data where the gap between data points corresponds to time intervals.

```python
# Set datetime index first
df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

# Time-based interpolation
df.interpolate(method='time', inplace=True)
```

**How it works:**
- Takes into account the actual time intervals
- Weights interpolation based on temporal distance
- More accurate for irregularly spaced time data

**Best for:**
- Datasets with a Datetime index
- Financial data, weather logs, sensor data
- When time gaps between observations vary

---

### 3. **Nearest Neighbor Interpolation**

Fills the missing value with the value of the nearest valid data point. It does not calculate an average; it simply copies the closest neighbor.

```python
# Requires scipy
df.interpolate(method='nearest', inplace=True)
```

**How it works:**
- Finds the closest non-null value
- Copies that value to fill the gap
- No calculation or averaging

**Best for:**
- Categorical-like numerical data
- When you want to preserve exact values
- Step-like data where intermediate values don't make sense

**Note:** Requires `scipy` library

---

### 4. **Polynomial Interpolation**

Fits a curve (quadratic or cubic) to the data points rather than a straight line.

```python
# Quadratic interpolation (order=2)
df.interpolate(method='polynomial', order=2, inplace=True)

# Cubic interpolation (order=3)
df.interpolate(method='polynomial', order=3, inplace=True)
```

**How it works:**
- Fits a polynomial curve through known data points
- Order determines the degree of the polynomial
- Higher order = more complex curves

**Best for:**
- Real-world data that follows a curve or non-linear pattern
- Data with acceleration/deceleration trends
- When linear interpolation is too simplistic

**Warning:** High order polynomials can cause overfitting

---

### 5. **Padding Methods (Forward/Backward Fill)**

Propagates values forward or backward to fill gaps.

#### Forward Fill (ffill)
```python
# Forward fill - use previous value
df.ffill(inplace=True)
# or
df.fillna(method='ffill', inplace=True)
```

#### Backward Fill (bfill)
```python
# Backward fill - use next value
df.bfill(inplace=True)
# or
df.fillna(method='bfill', inplace=True)
```

**Best for:**
- Situations where the value is expected to remain constant until a change is recorded
- Sensor status data
- Categorical data
- Inventory levels

---

## Practical Examples

### Example 1: Linear Interpolation
```python
import pandas as pd
import numpy as np

# Sample data with missing values
data = {
    'Day': [1, 2, 3, 4, 5, 6, 7],
    'Temperature': [20, 22, np.nan, 26, np.nan, 30, 32]
}
df = pd.DataFrame(data)

# Linear interpolation
df['Temperature'].interpolate(method='linear', inplace=True)
```

### Example 2: Time-Series Interpolation
```python
# Time-series data
data = {
    'Date': pd.date_range('2024-01-01', periods=7),
    'Sales': [100, 150, np.nan, np.nan, 250, 300, 350]
}
df = pd.DataFrame(data)
df.set_index('Date', inplace=True)

# Time-weighted interpolation
df.interpolate(method='time', inplace=True)
```

### Example 3: Polynomial Interpolation
```python
# Data with curved trend
data = {
    'X': [0, 1, 2, 3, 4, 5],
    'Y': [0, 1, np.nan, 9, np.nan, 25]
}
df = pd.DataFrame(data)

# Polynomial interpolation
df['Y'].interpolate(method='polynomial', order=2, inplace=True)
```

---

## Files in This Directory

- **`day-06-work.ipynb`** — Main Jupyter notebook with interpolation examples and exercises

---

## Key Methods

| Method | Description | Use Case | Requires scipy |
|--------|-------------|----------|----------------|
| `linear` | Straight line between points | General use, regular spacing | No |
| `time` | Time-weighted interpolation | Time-series with datetime index | No |
| `nearest` | Copy nearest valid value | Step-like or categorical data | Yes |
| `polynomial` | Fit polynomial curve | Non-linear trends | Yes |
| `ffill` | Forward fill (previous value) | Constant until change | No |
| `bfill` | Backward fill (next value) | Constant until change | No |

---

## Installation Requirements

```bash
# Basic pandas
pip install pandas

# For advanced methods (nearest, polynomial)
pip install scipy
```

---

## Best Practices

✅ Choose interpolation method based on data characteristics  
✅ Visualize data before and after interpolation  
✅ Use time-based interpolation for time-series data  
✅ Use linear for simple, evenly-spaced data  
✅ Use polynomial for curved trends (but avoid high orders)  
✅ Consider the meaning of your data when choosing a method  
❌ Don't use high-order polynomials (overfitting risk)  
❌ Don't interpolate categorical data (use forward/backward fill)  
❌ Don't interpolate if gaps are too large

---

## Decision Guide

```
Is your data time-series with datetime index?
├─ Yes → Use method='time'
└─ No → Continue

Does your data follow a linear trend?
├─ Yes → Use method='linear'
└─ No → Continue

Does your data follow a curved pattern?
├─ Yes → Use method='polynomial' (order=2 or 3)
└─ No → Continue

Do you have categorical-like data?
├─ Yes → Use ffill, bfill, or method='nearest'
└─ Consider your data characteristics
```

---

## Practice Exercises

1. Create a DataFrame with missing values in a numeric column
2. Apply linear interpolation and observe the results
3. Create time-series data with irregular intervals
4. Apply time-weighted interpolation
5. Create data with a curved pattern
6. Apply polynomial interpolation with different orders
7. Compare the results of different interpolation methods

**Challenge:** Create a dataset with multiple columns using different interpolation strategies for each column based on their characteristics!