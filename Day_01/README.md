# 🐼 Day 01: Pandas I/O examples

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

## Overview

This folder contains the Day 01 workbook and example data demonstrating basic Pandas input/output (I/O) operations: reading CSV/Excel/JSON files and exporting DataFrames.

## Files in this folder

- `day-01-work.ipynb` — Jupyter notebook with examples used below.
- `sample_data.csv` — example CSV used in the notebook.
- `sample_data.json` — example JSON exported in the notebook.
- `sample_data.xlsx` — example Excel exported in the notebook.

## Quick Summary of Examples

- Read a CSV (local):

```python
import pandas as pd
df = pd.read_csv("sample_data.csv")
print(df.head())
```

- Read an Excel file (adjust path if stored elsewhere):

```python
df = pd.read_excel("sample_data.xlsx")
print(df.head())
```

- Read a JSON file:

```python
df = pd.read_json("sample_data.json")
print(df.head())
```

- Create and save a DataFrame (examples from the notebook):

```python
import pandas as pd

data = {
    "Name": ["Noman", "Shah Nawaz", "Riaz Hussain", "Huzaifa Iqbal", "Haseeb Hassan", "Tayyab", "Samiullah", "Talha Fahad", "Saad"],
    "Age": [20, 21, 20, 22, 19, 20, 19, 20, 21],
}
df = pd.DataFrame(data)

# export to formats in this folder
df.to_csv("sample_data.csv", index=False)
df.to_excel("sample_data.xlsx", index=False)
df.to_json("sample_data.json", index=False)
```

## Notes

- The original notebook sometimes uses Google Drive absolute paths (for Colab). When running locally, use the relative file names above or update paths to your environment.
- Required packages:

```bash
pip install pandas openpyxl
```
