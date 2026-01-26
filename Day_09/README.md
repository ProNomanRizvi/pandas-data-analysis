# Day 09: Pandas Merging and Joining Operations

This directory contains learning materials for pandas merge operations, demonstrating different types of joins (inner, outer, left, right) using multiple datasets.

## 📚 Contents

### Jupyter Notebooks

#### `practice.ipynb`
Complete tutorial on pandas merging operations using customer and order datasets.

**Topics Covered:**
- Inner merge: Returns only matching records from both datasets
- Outer merge: Returns all records from both datasets with NaN for missing values
- Left merge: Keeps all records from left dataset with matching records from right
- Right merge: Keeps all records from right dataset with matching records from left

**Datasets Used:**
- `customers.csv`: Customer information (ID, name, email, region)
- `orders.csv`: Order information (order ID, customer ID, amount, date)

#### `practice2.ipynb`
Country data merging demonstration with popular tourist destinations and famous personalities.

**Topics Covered:**
- Inner, outer, left, and right merge operations
- Handling datasets with different numbers of records
- Managing NaN values in merged results

**Datasets Used:**
- `country_data_1.csv`: Countries and their popular tourist places
- `country_data_2.csv`: Countries and their famous historical figures

#### `day-09-work.ipynb`
Working notebook for practicing merge operations.

## 📊 Datasets

### Customer & Order Data
| File | Description | Columns |
|------|-------------|---------|
| `customers.csv` | Customer information with 5 records | customer_id, name, email, region |
| `orders.csv` | Order transactions with 5 records | order_id, customer_id, amount, date |

### Country Data
| File | Description | Columns |
|------|-------------|---------|
| `country_data_1.csv` | 20 countries with popular places | Country, Popular_Place |
| `country_data_2.csv` | 10 countries with famous persons | Country, Famous_Person |

## 🎯 Learning Objectives

1. **Understand Merge Types:**
   - Inner join: Intersection of datasets
   - Outer join: Union of datasets
   - Left join: All from left + matching from right
   - Right join: All from right + matching from left

2. **Key Concepts:**
   - Merging on common columns
   - Handling missing data (NaN values)
   - Preserving data based on join type
   - Understanding cardinality in merges

3. **Practical Applications:**
   - Combining customer and transaction data
   - Enriching datasets with additional information
   - Data integration from multiple sources

## 🚀 How to Use

1. **Start with `practice.ipynb`** to understand basic merge operations with customer/order data
2. **Practice with `practice2.ipynb`** using the country datasets
3. **Experiment in `day-09-work.ipynb`** with your own merge scenarios

## 💡 Key Takeaways

- **Inner Merge:** Use when you only want records that exist in both datasets
- **Outer Merge:** Use when you want to preserve all records from both datasets
- **Left Merge:** Use when your primary dataset is on the left and you want to enrich it
- **Right Merge:** Use when your primary dataset is on the right

## 📝 Example Usage

```python
import pandas as pd

# Load datasets
df1 = pd.read_csv("customers.csv")
df2 = pd.read_csv("orders.csv")

# Inner merge - only matching records
merged_inner = pd.merge(df1, df2, on="customer_id", how="inner")

# Outer merge - all records from both
merged_outer = pd.merge(df1, df2, on="customer_id", how="outer")

# Left merge - all from df1
merged_left = pd.merge(df1, df2, on="customer_id", how="left")

# Right merge - all from df2
merged_right = pd.merge(df1, df2, on="customer_id", how="right")
```

## 🔍 Common Use Cases

- **Customer Orders:** Matching customer information with their purchase history
- **Product Inventory:** Combining product details with stock levels
- **Geographic Data:** Merging location data with demographic information
- **Time Series:** Joining data from different time periods or sources

---

**Part of:** Pandas Data Analysis Learning Series  
**Day:** 09 - Merging and Joining Operations
