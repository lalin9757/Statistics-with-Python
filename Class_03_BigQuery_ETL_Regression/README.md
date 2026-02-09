# Statistics with Python - Class 03

## Python-BigQuery ETL Process, Correlation, Causality and Regression Analysis

This README provides a comprehensive overview of the topics covered in Class 03 of the 'Statistics with Python' module. We will explore the integration of Python with Google BigQuery for ETL processes, essential data manipulation techniques, statistical concepts like correlation and causality, and the application of multiple linear regression.

## Table of Contents

1.  [Python to BigQuery Integration Process and ETL Pipeline](#python-to-bigquery-integration-process-and-etl-pipeline)
2.  [Data Cleaning and Merging in Python](#data-cleaning-and-merging-in-python)
3.  [Creating a Dataset and Table in BigQuery and Uploading Data into that Table from Python](#creating-a-dataset-and-table-in-bigquery-and-uploading-data-into-that-table-from-python)
4.  [Stored Procedure to Remove Anomalies](#stored-procedure-to-remove-anomalies)
5.  [What is Correlation Analysis?](#what-is-correlation-analysis)
6.  [Positive, Negative and No Correlation](#positive-negative-and-no-correlation)
7.  [Correlation vs. Causality](#correlation-vs-causality)
8.  [Performing Multiple Linear Regression Model and Interpreting its Output](#performing-multiple-linear-regression-model-and-interpreting-its-output)

---

## 1. Python to BigQuery Integration Process and ETL Pipeline

This section covers the fundamental steps involved in setting up an Extract, Transform, Load (ETL) pipeline using Python to interact with Google BigQuery. This includes authentication, project setup, and basic data transfer concepts.

### Example Code: BigQuery Client Initialization

```python
from google.cloud import bigquery

# Initialize the BigQuery client
# Ensure your GOOGLE_APPLICATION_CREDENTIALS environment variable is set
client = bigquery.Client()

print("BigQuery client initialized successfully.")
```

---

## 2. Data Cleaning and Merging in Python

Effective data analysis begins with clean and well-structured data. This section focuses on common data cleaning techniques and how to merge different datasets using Python's pandas library.

### Example Code: Data Cleaning and Merging with Pandas

```python
import pandas as pd
import numpy as np

# Sample DataFrames
df1 = pd.DataFrame({
    'id': [1, 2, 3, 4],
    'name': ['Alice', 'Bob', 'Charlie', 'David'],
    'age': [24, 27, np.nan, 32],
    'city': ['New York', 'Los Angeles', 'Chicago', 'Houston']
})

df2 = pd.DataFrame({
    'id': [1, 2, 3, 5],
    'salary': [70000, 80000, 65000, 90000],
    'department': ['HR', 'IT', 'Finance', 'Marketing']
})

# Data Cleaning: Handling missing values
df1['age'].fillna(df1['age'].mean(), inplace=True)

# Data Cleaning: Removing duplicates (if any)
df1.drop_duplicates(inplace=True)

# Data Merging: Inner merge on 'id'
merged_df = pd.merge(df1, df2, on='id', how='inner')

print("Cleaned and Merged DataFrame:")
print(merged_df)
```

---

## 3. Creating a Dataset and Table in BigQuery and Uploading Data into that Table from Python

This section details the process of programmatically creating datasets and tables in Google BigQuery and then uploading data from a Python DataFrame directly into these tables.

### Example Code: Creating BigQuery Dataset, Table and Uploading Data

```python
from google.cloud import bigquery
import pandas as pd

client = bigquery.Client()

project_id = client.project
dataset_id = 'my_new_dataset'
table_id = 'my_new_table'

# 1. Create a Dataset
dataset = bigquery.Dataset(f"{project_id}.{dataset_id}")
dataset.location = "US"

try:
    dataset = client.create_dataset(dataset, timeout=30)  # Make an API request.
    print(f"Dataset {dataset.dataset_id} created.")
except Exception as e:
    if 'Already Exists' in str(e):
        print(f"Dataset {dataset.dataset_id} already exists.")
    else:
        raise e

# Sample DataFrame to upload
data_to_upload = pd.DataFrame({
    'name': ['Eve', 'Frank'],
    'age': [29, 35],
    'occupation': ['Engineer', 'Doctor']
})

# 2. Define Table Schema (optional, BigQuery can infer)
job_config = bigquery.LoadJobConfig(schema=[
    bigquery.SchemaField("name", "STRING"),
    bigquery.SchemaField("age", "INTEGER"),
    bigquery.SchemaField("occupation", "STRING"),
])

# 3. Upload DataFrame to BigQuery Table
job = client.load_table_from_dataframe(
    data_to_upload,
    f"{project_id}.{dataset_id}.{table_id}",
    job_config=job_config
)

job.result()  # Wait for the job to complete.

print(f"Loaded {job.output_rows} rows into {table_id}.")
```

---

## 4. Stored Procedure to Remove Anomalies

BigQuery allows the creation of stored procedures to encapsulate SQL logic, including data cleansing routines. This section discusses the concept of using a stored procedure to identify and remove anomalies from your data directly within BigQuery.

### Example SQL: Stored Procedure for Anomaly Detection (Conceptual)

```sql
CREATE OR REPLACE PROCEDURE `your_project.your_dataset.remove_anomalies`(
    table_name STRING,
    column_name STRING,
    threshold FLOAT64
)
BEGIN
    -- This is a conceptual example. Anomaly detection logic can vary.
    -- For instance, using Z-score or IQR to identify outliers.
    EXECUTE IMMEDIATE FORMAT(
        "DELETE FROM `your_project.your_dataset.%s` WHERE %s > (SELECT AVG(%s) + %F * STDDEV(%s) FROM `your_project.your_dataset.%s`)",
        table_name, column_name, column_name, threshold, column_name, table_name
    );
    -- More sophisticated anomaly detection might involve clustering, isolation forests, etc.
    -- which would typically be performed in Python and then updated in BigQuery.
END;
```

---

## 5. What is Correlation Analysis?

Correlation analysis is a statistical method used to evaluate the strength and direction of a linear relationship between two quantitative variables. It helps in understanding how changes in one variable are associated with changes in another.

---

## 6. Positive, Negative and No Correlation

This section elaborates on the different types of linear relationships observed in correlation analysis:

*   **Positive Correlation**: As one variable increases, the other variable also tends to increase.
*   **Negative Correlation**: As one variable increases, the other variable tends to decrease.
*   **No Correlation**: There is no consistent linear relationship between the two variables.

### Example: Scatter Plots

(Imagine scatter plots here illustrating positive, negative, and no correlation)

---

## 7. Correlation vs. Causality

It is crucial to distinguish between correlation and causality. While correlation indicates an association between variables, it does not imply that one variable causes the other. Causality suggests a cause-and-effect relationship, which requires more rigorous analysis and experimental design to establish.

> **"Correlation does not imply causation."** This fundamental principle reminds us that observed associations might be due to confounding variables, reverse causation, or pure chance.

---

## 8. Performing Multiple Linear Regression Model and Interpreting its Output

Multiple Linear Regression is a statistical technique used to predict the outcome of a dependent variable based on the values of two or more independent variables. This section demonstrates how to build and interpret such a model using Python.

### Example Code: Multiple Linear Regression with `statsmodels`

```python
import pandas as pd
import statsmodels.api as sm

# Sample Data
data = {
    'Y': [10, 12, 15, 13, 18, 20, 22, 25, 23, 28],
    'X1': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    'X2': [5, 4, 6, 5, 7, 6, 8, 7, 9, 8]
}
df = pd.DataFrame(data)

# Define dependent variable (Y) and independent variables (X)
Y = df['Y']
X = df[['X1', 'X2']]

# Add a constant to the independent variables for the intercept term
X = sm.add_constant(X)

# Create and fit the model
model = sm.OLS(Y, X)
results = model.fit()

# Print the regression summary
print("\nMultiple Linear Regression Model Summary:")
print(results.summary())

# Interpretation of Output (Key points):
# - R-squared: Proportion of variance in Y explained by X variables.
# - Adj. R-squared: Adjusted for the number of predictors.
# - Coeff (coefficients): The change in Y for a one-unit change in the corresponding X, holding other X's constant.
# - P>|t| (p-value): Indicates the statistical significance of each coefficient.
# - F-statistic (and its p-value): Tests the overall significance of the model.
```

---
