# Key Statistics Concepts in Python

Your go-to guide for essential statistics concepts, made easy to remember. This document covers **Sampling Methods**, **Probability**, and a practical Python assignment.

## Table of Contents
1. [Why Sample?](#why-sample)
2. [Types of Sampling](#types-of-sampling)
3. [Probability Basics](#probability-basics)
4. [Average vs. Weighted Average](#average-vs-weighted-average)
5. [Python Assignment: Stratified Sampling](#python-assignment-stratified-sampling)

---

## 1. Why Sample?
Sampling is taking a small part of a large group to learn about the whole group. It's important because it's:

*   **Cheaper:** Costs less than studying everyone.
*   **Faster:** Saves time on data collection and analysis.
*   **Practical:** Makes it possible to study huge populations.

---

## 2. Types of Sampling
There are two main approaches to sampling.

### Probability Sampling (Random)
Everyone has a fair chance of being picked. This is best for accurate results.

| Method | How It Works |
| :--- | :--- |
| **Simple Random** | Like drawing names from a hat. |
| **Stratified** | Divide into groups (strata), then pick randomly from each group. |
| **Cluster** | Divide into groups (clusters), then pick whole groups randomly. |
| **Systematic** | Pick every $n^{th}$ person from a list. |

### Non-Probability Sampling (Not Random)
Selection is based on convenience or judgment. It's easier but less accurate.

*   **Convenience:** Picking people who are easy to reach.
*   **Quota:** Filling a quota for certain groups.
*   **Purposive:** Picking people you think are good for the study.
*   **Snowball:** Asking people to refer others.

---

## 3. Probability Basics
**Probability** is the chance of something happening. A **Probability Distribution** shows the chances for all possible outcomes.

| Distribution | When to Use It |
| :--- | :--- |
| **Normal** | For things like heights, weights, and test scores. |
| **Binomial** | For a fixed number of "Yes/No" trials (e.g., 10 coin flips). |
| **Poisson** | For counting events over time (e.g., customers per hour). |

---

## 4. Average vs. Weighted Average
*   **Average:** Sum of all values divided by the count of values. Everyone gets an equal vote.
    *   Example: `(80 + 90 + 100) / 3 = 90`
*   **Weighted Average:** Each value is given a different level of importance (a "weight").
    *   Example: `(80 * 0.2) + (90 * 0.3) + (100 * 0.5) = 16 + 27 + 50 = 93`

---

## 5. Python Assignment: Stratified Sampling
This code performs **Proportionate Stratified Sampling** on the `heart.csv` dataset. It ensures our sample has the same percentage of people with and without heart disease as the full dataset.

### The Code
```python
import pandas as pd
from sklearn.model_selection import train_test_split

# Load the data
df = pd.read_csv("heart.csv", index_col=0)

# Split the data while keeping proportions the same
# The 'stratify' argument does the magic
stratified_sample, _ = train_test_split(
    df, 
    test_size=0.2, # We want a 20% sample
    stratify=df["AHD"], # Stratify by the heart disease column
    random_state=42
)

# Check the result
print("Original Proportions:\n", df["AHD"].value_counts(normalize=True))
print("\nSample Proportions:\n", stratified_sample["AHD"].value_counts(normalize=True))
```

### How to Run
1.  Make sure you have `pandas` and `scikit-learn` installed (`pip install pandas scikit-learn`).
2.  Save the code and `heart.csv` in the same folder.
3.  Run the Python script.
