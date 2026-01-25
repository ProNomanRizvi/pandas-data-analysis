# Day 08: Grouping Data in Pandas

This directory contains exercises and examples related to grouping data in Pandas.

## Files

- **`day-08-work.ipynb`**: Introduction to `groupby` operations, covering:
    - Grouping by a single column.
    - Grouping by multiple columns.
    - Aggregating data (mean, max, etc.).
    - Uses `students_data.xlsx`.

- **`practice.ipynb`**: Practice exercises using sales data, including:
    - Calculating total sales by region.
    - Analyzing profit by product and sales.
    - Checking profit trends by date.
    - Uses `sales_data.csv`.

- **`sales_data.csv`**: Dataset containing sales records with fields for order ID, date, region, category, product, sales, quantity, and profit.

- **`students_data.xlsx`**: Dataset containing student information including ID, name, grade, DOB, gender, GPA, attendance, and enrollment status.

## Key Concepts
- **`groupby()`**: Splitting the data into groups based on some criteria.
- **Aggregation**: Computing a summary statistic (or statistics) for each group (e.g., `sum`, `mean`, `max`).
