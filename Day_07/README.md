# Day 07 — Sorting & Aggregation

This folder contains `day-07-work.ipynb`, a short pandas notebook demonstrating sorting and basic aggregation techniques using the provided `unsorted_data.csv` dataset.

**Notebook:** [Day_07/day-07-work.ipynb](Day_07/day-07-work.ipynb)

## Overview
- Load `unsorted_data.csv` into a pandas DataFrame.
- Sort the DataFrame by single and multiple columns (examples: `EmployeeID`, `FirstName`, `Salary`, `JoinDate`).
- Compute summary statistics using `df.describe()`.
- Perform column-specific aggregation on the `Salary` column (sum, mean, median, std, min, max).

## Prerequisites
- Python 3.8+ (or any supported 3.x)
- pandas

Install dependencies:

```bash
python -m pip install --user pandas
```

## How to run
- Open the notebook with Jupyter Notebook or Jupyter Lab and run the cells:

```bash
jupyter notebook Day_07/day-07-work.ipynb
# or
jupyter lab Day_07/day-07-work.ipynb
```

- Or run selected cells in your preferred environment (VS Code, Colab, etc.).

## Key cells (what to look for)
- Loading data: reads `unsorted_data.csv` and prints the head.
- Sorting examples: `df.sort_values(...)` with `inplace=True` and `ascending` flags.
- Aggregation: `summary = df.describe()` and printed salary operations (sum, mean, median, std, min, max).

## Notes
- The notebook uses `inplace=True` in sorting; if you want to keep the original order, pass `inplace=False` and assign the result to a new DataFrame.
- Ensure the `unsorted_data.csv` file is present in the same folder when running the notebook.

If you want, I can also add a small example script that loads the CSV and prints the same summaries from the notebook. Want that?