# Descriptive Statistics & Shape Characteristics

## Table of Contents
- [Project Overview](#project-overview)
- [Key Concepts](#key-concepts)
  - [Measures of Central Tendency](#measures-of-central-tendency)
  - [Measures of Location](#measures-of-location)
  - [Measures of Dispersion](#measures-of-dispersion)
  - [Shape Characteristics](#shape-characteristics)
- [Methodology](#methodology)
- [Analysis and Results](#analysis-and-results)
- [Visualizations](#visualizations)
- [Example Code](#example-code)
- [Conclusion](#conclusion)
- [Usage](#usage)
- [Dependencies](#dependencies)

## Project Overview
This Jupyter Notebook provides a comprehensive analysis of descriptive statistics and shape characteristics using a real-world dataset, specifically the "Amazon Sale Report.csv". The primary goal is to demonstrate the application and interpretation of various statistical measures to understand the distribution and properties of data.

## Key Concepts

### Measures of Central Tendency
Measures of central tendency help identify the 'center' or typical value of a dataset.

- **Mean:** The arithmetic average of all values. It is sensitive to outliers.
- **Median:** The middle value when the data is ordered. It is robust to outliers.
- **Mode:** The most frequently occurring value in the dataset. Useful for categorical data.

### Measures of Location
Measures of location help understand the position of specific values within the data distribution.

- **Quartiles:** Divide the data into four equal parts (Q1: 25th percentile, Q2: 50th percentile/Median, Q3: 75th percentile).
- **Deciles:** Divide the data into ten equal parts.
- **Percentiles:** Indicate the percentage of values in a dataset that are below a particular value.

### Measures of Dispersion
Measures of dispersion describe the spread or variability of the data.

- **Range:** The difference between the maximum and minimum values.
- **Variance:** The average of the squared differences from the mean. It quantifies how much the data points deviate from the mean.
- **Standard Deviation:** The square root of the variance. It provides a measure of spread in the same units as the data.
- **Coefficient of Variation (CV):** The ratio of the standard deviation to the mean, expressed as a percentage. It is useful for comparing the relative variability between datasets with different units or scales.

### Shape Characteristics
Shape characteristics describe the form of the data distribution.

- **Skewness:** Measures the asymmetry of the probability distribution. 
  - **Positive Skew (> 0):** The tail on the right side is longer, indicating more extreme high values.
  - **Negative Skew (< 0):** The tail on the left side is longer, indicating more extreme low values.
  - **Zero Skew (≈ 0):** The distribution is roughly symmetrical.

- **Kurtosis:** Measures the 'tailedness' of the distribution, indicating how concentrated the data is around the mean and the heaviness of the tails.
  - **Leptokurtic (> 0):** Heavier tails and a sharper peak than a normal distribution, indicating more extreme values.
  - **Platykurtic (< 0):** Lighter tails and a flatter peak than a normal distribution, indicating fewer extreme values.
  - **Mesokurtic (≈ 0):** Similar tail behavior and peak shape to a normal distribution.

## Methodology
The notebook follows these steps:
1.  **Library and Data Loading:** Imports necessary libraries (pandas, numpy, seaborn, matplotlib, scipy, statsmodels) and loads the `Amazon Sale Report.csv` dataset.
2.  **Initial Data Exploration:** Displays basic information about the dataset, including `df.head()`, `df.info()`, `df.shape`, and `df.columns` to understand its structure and identify potential issues.
3.  **Missing Values and Duplicates:** Checks for missing values across columns and identifies duplicate rows.
4.  **Central Tendency and Location Calculation:** Calculates mean, median, mode, quartiles (Q1, Q3), deciles, and percentiles for the 'Amount' column.
5.  **Dispersion Calculation:** Computes standard deviation, variance, and coefficient of variation for the 'Amount' column.
6.  **Shape Characteristics Calculation:** Determines the skewness and kurtosis of the 'Amount' column.
7.  **Visualizations:** Generates a histogram of the 'Amount' column to visually inspect its distribution.

## Analysis and Results

**Dataset Information:**
- The dataset contains 128,975 entries and 24 columns.
- Columns like `Courier Status`, `currency`, `Amount`, `ship-city`, `ship-state`, `ship-postal-code`, `ship-country`, `promotion-ids`, `fulfilled-by`, and `Unnamed: 22` contain missing values.
- No duplicate rows were found.

**Measures for 'Amount' Column:**
- **Mean:** 648.56
- **Median:** 605.0
- **Mode:** 399.0
- **Q1 (25th Percentile):** 449.0
- **Q3 (75th Percentile):** 788.0
- **Deciles:** [358.1, 406.0, 475.0, 533.0, 605.0, 690.0, 758.0, 837.0, 1068.0]
- **10th Percentile:** 358.1
- **90th Percentile:** 1068.0
- **Standard Deviation:** 281.21
- **Variance:** 79079.0
- **Coefficient of Variation:** 43.36%

**Shape Characteristics for 'Amount' Column:**
- **Skewness:** 0.885 (Positive Skew)
- **Kurtosis:** 3.003 (Leptokurtic)

## Visualizations
The notebook includes a histogram of the 'Amount' column, which visually confirms the positive skewness and the presence of a longer tail towards higher values. The `kde=True` argument in `sns.histplot` also overlays a Kernel Density Estimate to smooth the distribution curve.

## Example Code

Here are some key code snippets from the Jupyter Notebook demonstrating the analysis:

### Loading Libraries and Data
```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats
import statsmodels.api as sm

df = pd.read_csv("Amazon Sale Report.csv")
```

### Initial Data Exploration
```python
df.head()
df.info()
df.shape
df.columns
```

### Measures of Central Tendency, Location, and Dispersion for 'Amount' Column
```python
mean_amount = df["Amount"].mean()
median_amount = df["Amount"].median()
mode_amount = df["Amount"].mode()[0]

q1_amount = df["Amount"].quantile(0.25)
q3_amount = df["Amount"].quantile(0.75)
deciles_amount = df["Amount"].quantile([.10, .20, .30, 0.40, 0.50, 0.60, 0.70, 0.80, 0.90])
percentiles_amount = df["Amount"].quantile([0.10, 0.90])

std_amount = df["Amount"].std()
var_amount = df["Amount"].var()
cv_amount = (std_amount / mean_amount) * 100

print(f"Mean: {mean_amount}, Median: {median_amount}, Mode: {mode_amount}")
print(f"Q1: {q1_amount}, Q3: {q3_amount}")
print(f"Deciles: {deciles_amount.values}")
print(f"Percentiles (10% & 90%): {percentiles_amount.values}")
print(f"Standard Deviation: {std_amount}")
print(f"Variance: {var_amount}")
print(f"Coefficient of Variation: {cv_amount:.2f}%")
```

### Shape Characteristics (Skewness and Kurtosis)
```python
skewness_amount = stats.skew(df["Amount"].dropna())
kurtosis_amount = stats.kurtosis(df["Amount"].dropna())

print(f"Skewness: {skewness_amount}, Kurtosis: {kurtosis_amount}")
```

### Histogram Visualization
```python
sns.histplot(df['Amount'], kde=True, stat='density')
plt.title('Histogram of Amount')
plt.show()
```

## Conclusion
The analysis of the 'Amount' column reveals a positively skewed distribution, indicating that there are more sales with smaller amounts, but also a tail of significantly larger sales. The leptokurtic nature suggests that the data has heavier tails and a sharper peak than a normal distribution, implying a higher likelihood of extreme values (outliers) in the sales amounts. These insights are crucial for understanding sales patterns and can inform business decisions, such as inventory management or marketing strategies.

## Usage
To run this notebook, ensure you have Jupyter Notebook or JupyterLab installed. You will also need the `Amazon Sale Report.csv` file in the same directory as the notebook. Execute the cells sequentially to reproduce the analysis.

## Dependencies
- `pandas`
- `numpy`
- `seaborn`
- `matplotlib`
- `scipy`
- `statsmodels`
