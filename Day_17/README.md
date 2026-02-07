# 🏋️ Day 17: Practice Exercises

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

Day 17 consolidates the reshaping and aggregation concepts from the previous lessons (Days 13-16). This practice session applies `pivot_table`, `melt`, and `crosstab` to real-world datasets.

## Topics Covered

### 1. **Pivot Table (Company Revenue)**

Aggregate quarterly revenue data by year.

```python
df.pivot_table(index="Year", columns="Quarter", values="Revenue", aggfunc="sum")
```

### 2. **Melt (Weather Data)**

Transform temperature data from wide format (columns per city) to long format.

```python
pd.melt(df_weather, id_vars=["Day"], var_name="City", value_name="Temperature")
```

### 3. **Crosstab (Employee Data)**

Analyze the distribution of employees by Occupation and Nationality.

```python
pd.crosstab(df_employee["Occupation"], df_employee["Nationality"], margins=True)
```

---

## Files in This Directory

-   **`practice.ipynb`**: The main practice notebook with all exercises.
-   **`company_revenue.csv`**: Quarterly revenue data for multiple companies.
-   **`weather_data.csv`**: Weekly temperature data for two cities.
-   **`employee_data.csv`**: Employee details including occupation and nationality.

---

## Key Concepts

| Function | Use Case |
| :--- | :--- |
| `pivot_table` | Summarize numerical data across categories. |
| `melt` | Unpivot wide data into long format. |
| `crosstab` | Create frequency tables for categorical data. |
