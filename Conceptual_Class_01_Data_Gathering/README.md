# Data Gathering in Statistics with Python

## Overview

This module focuses on the fundamental principles and practical techniques for **data gathering** within the context of **statistics using Python**. Effective data gathering is the cornerstone of any robust statistical analysis, ensuring the quality, relevance, and representativeness of the data used. This README provides a comprehensive guide to various data acquisition methods, essential Python libraries, and best practices for collecting data for statistical purposes.

## Table of Contents

- [Overview](#overview)
- [Key Concepts in Data Gathering](#key-concepts-in-data-gathering)
  - [1. Data Sources](#1-data-sources)
  - [2. Types of Data](#2-types-of-data)
  - [3. Sampling Techniques](#3-sampling-techniques)
  - [4. Ethical Considerations](#4-ethical-considerations)
- [Python Libraries for Data Gathering](#python-libraries-for-data-gathering)
- [Example Code](#example-code)
  - [Example 1: Reading Data from a CSV File with Pandas](#example-1-reading-data-from-a-csv-file-with-pandas)
  - [Example 2: Fetching Data from a Public API with Requests](#example-2-fetching-data-from-a-public-api-with-requests)
  - [Example 3: Basic Web Scraping with BeautifulSoup4](#example-3-basic-web-scraping-with-beautifulsoup4)
- [Collaboration Guidelines](#collaboration-guidelines)
- [References](#references)

## Key Concepts in Data Gathering

Before diving into practical implementation, it's crucial to understand the theoretical underpinnings of data gathering. This section outlines key concepts:

### 1. Data Sources

Data can originate from a multitude of sources, each with its own characteristics and implications for statistical analysis. Think of it as **P**rimary for **P**urpose-driven collection and **S**econdary for **S**urplus data.

| Data Source | Description | Examples | Mnemonic | 
| :---------- | :---------- | :------- | :------- |
| **Primary Data** | Collected directly by the researcher for a specific purpose. | Surveys, experiments, observations. | **P**urpose-driven | 
| **Secondary Data** | Data already collected by someone else for a different purpose. | Government publications, academic journals, public datasets, web data. | **S**urplus/Shared | 

### 2. Types of Data

Understanding data types is essential for appropriate statistical treatment. Remember **Q**uantitative for **Q**uantity (numbers) and **Qual**itative for **Qual**ity (descriptions).

| Data Type | Sub-Type | Description | Examples | Mnemonic | 
| :-------- | :------- | :---------- | :------- | :------- |
| **Quantitative** | **Discrete** | Numerical data that can only take specific, distinct values. | Number of children, counts of events. | **D**istinct **D**igits | 
| (Numerical) | **Continuous** | Numerical data that can take any value within a given range. | Height, weight, temperature. | **C**an **C**hange **C**ontinually | 
| **Qualitative** | **Nominal** | Categorical data without a natural order or ranking. | Gender, marital status, colors. | **N**o **O**rder | 
| (Categorical) | **Ordinal** | Categorical data with a meaningful order or ranking. | Education level (e.g., High School, Bachelor's), satisfaction ratings (e.g., Low, Medium, High). | **O**rder **R**anks | 

### 3. Sampling Techniques

When it's impractical to collect data from an entire population, sampling is used. The choice of sampling technique significantly impacts the generalizability of statistical findings. Think of **P**robability as **P**redictable chances and **N**on-**P**robability as **N**ot **P**redictable.

#### Probability Sampling (Random Selection - minimizes bias)

| Technique | Description | Mnemonic | 
| :-------- | :---------- | :------- |
| **Simple Random Sampling** | Every individual has an equal chance of selection. | **S**elect **R**andomly | 
| **Stratified Sampling** | Population divided into strata (subgroups), and random samples taken from each stratum. | **S**plit & **S**ample | 
| **Systematic Sampling** | Selecting every nth individual from a list. | **N**th **S**election | 
| **Cluster Sampling** | Population divided into clusters, and a random sample of clusters is selected. | **C**ut into **C**lusters | 

#### Non-Probability Sampling (Non-random Selection - prone to bias)

| Technique | Description | Mnemonic | 
| :-------- | :---------- | :------- |
| **Convenience Sampling** | Selecting individuals who are easily accessible. | **C**lose & **E**asy | 
| **Quota Sampling** | Selecting individuals based on specific characteristics until a quota is met. | **Q**uantity **Q**uota | 
| **Snowball Sampling** | Participants recruit other participants, often used for hard-to-reach populations. | **S**preading **S**election | 

### 4. Ethical Considerations

Ethical data gathering is paramount. Remember the acronym **IPBC** for **I**nformed Consent, **P**rivacy, **B**ias Mitigation, and **C**onfidentiality.

*   **Informed Consent**: Participants must be fully aware of the study's purpose, risks, and their rights before participating.
*   **Privacy and Confidentiality**: Protecting personal information and ensuring anonymity where appropriate. Data should be handled with care to prevent unauthorized access.
*   **Data Security**: Safeguarding collected data from unauthorized access, alteration, or misuse through appropriate technical and organizational measures.
*   **Bias Mitigation**: Designing data collection methods to minimize potential biases that could skew results or misrepresent populations.

## Python Libraries for Data Gathering

Python offers a rich ecosystem of libraries for various data gathering tasks. Here are some essential ones for statistical applications. Think of them as your **P**owerful **N**etwork **R**esources for **B**ig **S**tats **S**olutions (**PNRBSS**).

| Library | Primary Use | Mnemonic | 
| :------ | :---------- | :------- |
| **`pandas`** | Data manipulation, analysis, reading various file formats (CSV, Excel, SQL). | **P**owerful **A**nalysis & **N**umerical **D**ata **A**ccess | 
| **`numpy`** | Foundational numerical computing, array operations, mathematical functions. | **N**umerical **U**nderpinnings for **M**athematical **P**ython | 
| **`requests`** | Making HTTP requests, interacting with web APIs. | **R**etrieving **E**xternal **Q**ueries | 
| **`BeautifulSoup4` (`bs4`)** | Parsing HTML/XML, basic web scraping. | **B**eautiful **S**craping | 
| **`Scrapy`** | Advanced web scraping framework for complex projects. | **S**ophisticated **C**rawler | 
| **`sqlite3`** | Interacting with SQLite databases for local data storage. | **S**imple **Q**uery **L**ocal **I**nterface | 

## Example Code

This section provides practical examples of data gathering using Python.

### Example 1: Reading Data from a CSV File with Pandas

```python
import pandas as pd

# Create a dummy CSV file for demonstration
dummy_data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David'],
    'Age': [24, 27, 22, 32],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston'],
    'Score': [85, 92, 78, 88]
}
df_dummy = pd.DataFrame(dummy_data)
df_dummy.to_csv('students.csv', index=False)

# Read the CSV file into a Pandas DataFrame
try:
    df = pd.read_csv('students.csv')
    print("Data successfully loaded from students.csv:")
    print(df.head())
    print(f"\nShape of the DataFrame: {df.shape}")
except FileNotFoundError:
    print("Error: 'students.csv' not found. Please ensure the file exists.")
except Exception as e:
    print(f"An error occurred: {e}")
```

### Example 2: Fetching Data from a Public API with Requests

This example demonstrates how to fetch data from a public API (e.g., JSONPlaceholder for fake online REST API).

```python
import requests
import json

# Define the API endpoint
api_url = "https://jsonplaceholder.typicode.com/posts/1"

# Make a GET request to the API
try:
    response = requests.get(api_url)
    response.raise_for_status()  # Raise an HTTPError for bad responses (4xx or 5xx)

    # Parse the JSON response
    data = response.json()

    print(f"Data fetched from {api_url}:")
    print(json.dumps(data, indent=2))

    # Example of accessing specific data points
    print(f"\nTitle: {data['title']}")
    print(f"Body: {data['body'][:50]}...")

except requests.exceptions.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except requests.exceptions.ConnectionError as conn_err:
    print(f"Connection error occurred: {conn_err}")
except requests.exceptions.Timeout as timeout_err:
    print(f"Timeout error occurred: {timeout_err}")
except requests.exceptions.RequestException as req_err:
    print(f"An error occurred during the request: {req_err}")
except json.JSONDecodeError:
    print("Error: Could not decode JSON from response.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

### Example 3: Basic Web Scraping with BeautifulSoup4

This example shows how to extract a title from a simple HTML page. For more complex scraping, consider `Scrapy`.

```python
import requests
from bs4 import BeautifulSoup

# Define the URL to scrape
url = "https://www.example.com"

# Fetch the HTML content
try:
    response = requests.get(url)
    response.raise_for_status() # Raise an HTTPError for bad responses

    # Parse the HTML content
    soup = BeautifulSoup(response.text, 'html.parser')

    # Extract the title of the page
    title = soup.find('title').get_text() if soup.find('title') else 'No title found'

    print(f"Successfully scraped data from {url}:")
    print(f"Page Title: {title}")

    # Example: Find all paragraph texts
    paragraphs = [p.get_text() for p in soup.find_all('p')]
    if paragraphs:
        print("\nFirst paragraph:")
        print(paragraphs[0])
    else:
        print("\nNo paragraphs found.")

except requests.exceptions.RequestException as e:
    print(f"Error fetching URL {url}: {e}")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

## Collaboration Guidelines

We welcome contributions to enhance this module! Please follow these guidelines:

1.  **Fork the Repository**: Start by forking this repository to your GitHub account.
2.  **Create a New Branch**: Create a new branch for your feature or bug fix (e.g., `feature/add-new-sampling-method` or `bugfix/fix-api-example`).
3.  **Coding Standards**: Adhere to [PEP 8](https://www.python.org/dev/peps/pep-0008/) for Python code style. Use clear, concise variable names and add comments where necessary.
4.  **Documentation**: Ensure any new code or changes are well-documented. Update relevant sections of this README if new concepts or libraries are introduced.
5.  **Testing**: If applicable, add unit tests for new features or bug fixes.
6.  **Commit Messages**: Write clear and descriptive commit messages.
7.  **Pull Requests**: Submit a pull request to the `main` branch of this repository. Provide a detailed description of your changes and why they are necessary.
8.  **Issue Reporting**: If you find a bug or have a suggestion, please open an issue in the issue tracker.

## References

[1] Real Python. (2025, March 24). *Python Code Quality: Best Practices and Tools*. [https://realpython.com/python-code-quality/](https://realpython.com/python-code-quality/)
[2] Honeybear.ai. (2025, August 14). *9 Data Analysis Best Practices for Accurate, Fast Insights*. [https://www.honeybear.ai/blog/data-analysis-best-practices](https://www.honeybear.ai/blog/data-analysis-best-practices)
[3] Data Science PM. *15 Data Science Documentation Best Practices*. [https://www.datascience-pm.com/documentation-best-practices/](https://www.datascience-pm.com/documentation-best-practices/)
[4] Cornell Data Services. *Writing READMEs for Research Data*. [https://data.research.cornell.edu/data-management/sharing/readme/](https://data.research.cornell.edu/data-management/sharing/readme/)
[5] GeeksforGeeks. (2025, July 23). *Top 15 Python Libraries for Data Analytics*. [https://www.geeksforgeeks.org/blogs/python-libraries-for-data-analytics/](https://www.geeksforgeeks.org/blogs/python-libraries-for-data-analytics/)
[6] DataCamp. *Top 31 Python Libraries for Data Science in 2026*. [https://www.datacamp.com/blog/top-python-libraries-for-data-science](https://www.datacamp.com/blog/top-python-libraries-for-data-science)
[7] Statology. (2024, August 22). *Essential Python Libraries for Statistics: A Practical Guide*. [https://www.statology.org/essential-python-libraries-for-statistics-a-practical-guide/](https://www.statology.org/essential-python-libraries-for-statistics-a-practical-guide/)
[8] Medium. (2023, March 7). *How to write a good Readme for your Data Science project on GitHub*. [https://medium.datadriveninvestor.com/how-to-write-a-good-readme-for-your-data-science-project-on-github-ebb023d4a50e](https://medium.datadriveninvestor.com/how-to-write-a-good-readme-for-your-data-science-project-on-github-ebb023d4a50e)
[9] Python.org. *PEP 8 -- Style Guide for Python Code*. [https://www.python.org/dev/peps/pep-0008/](https://www.python.org/dev/peps/pep-0008/)
