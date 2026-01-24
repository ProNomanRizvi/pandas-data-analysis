# Data Interpolation in Pandas (Day 06)

This Jupyter Notebook explores various **Interpolation** techniques using the Python Pandas library. Interpolation is a crucial step in data preprocessing, primarily used to handle missing values (`NaN`) while preserving data integrity and maintaining trends.

## 📄 Overview

Dealing with missing data is a common challenge in Data Science. Simply dropping missing values can lead to data loss, while filling them with a static mean or median might distort the data distribution. Interpolation provides a mathematical approach to estimate missing values based on other data points.

### Key Objectives:
- **Preserve Data Integrity:** Estimate values without altering the overall structure.
- **Smooth Trends:** Maintain the continuity of data, especially in time series.
- **Avoid Data Loss:** Retain rows/columns that would otherwise be discarded.

## 🛠️ Technologies Used

- **Python 3.x**
- **Pandas** (Data manipulation and analysis)
- **SciPy** (Required for advanced interpolation methods like `nearest` and `polynomial`)

## 📚 Concepts & Methods Covered

The notebook demonstrates the following interpolation strategies:

### 1. Linear Interpolation
The default method. It estimates missing values by connecting two known data points with a straight line.
- **Syntax:** `df.interpolate(method='linear')`
- **Best for:** Data that follows a generally linear trend.

### 2. Time-Weighted Interpolation
Crucial for time-series data where the gap between data points corresponds to time intervals.
- **Syntax:** `df.interpolate(method='time')`
- **Best for:** Datasets with a Datetime index (e.g., financial data, weather logs).

### 3. Nearest Neighbor Interpolation
Fills the missing value with the value of the nearest valid data point. It does not calculate an average; it simply copies the closest neighbor.
- **Syntax:** `df.interpolate(method='nearest')`
- **Note:** Requires `scipy`.

### 4. Polynomial Interpolation
Fits a curve (quadratic or cubic) to the data points rather than a straight line.
- **Syntax:** `df.interpolate(method='polynomial', order=2)`
- **Best for:** Real-world data that follows a curve or non-linear pattern.

### 5. Padding (Forward Fill)
Propagates the last valid observation forward to the next valid one.
- **Syntax:** `df.ffill()`
- **Best for:** Situations where the value is expected to remain constant until a change is recorded (e.g., sensor status).

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone <repository-url>