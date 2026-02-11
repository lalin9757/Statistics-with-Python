# Statistics with Python: Sampling Methods and Probability Distributions

This repository contains educational materials and practical implementations for key statistical concepts used in Research and Data Science, specifically focusing on **Sampling Methods** and **Probability Distributions**.

## Table of Contents
1. [Importance of Sampling Methods](#importance-of-sampling-methods)
2. [Probability Sampling Methods](#probability-sampling-methods)
3. [Non-Probability Sampling Methods](#non-probability-sampling-methods)
4. [Probability Theory & Distributions](#probability-theory--distributions)
5. [Average vs. Weighted Average](#average-vs-weighted-average)
6. [Assignment: Proportionate Stratified Sampling](#assignment-proportionate-stratified-sampling)
7. [How to Run the Code](#how-to-run-the-code)

---

## Importance of Sampling Methods
In research and data science, it is often impossible or impractical to collect data from an entire population. **Sampling** is the process of selecting a subset of individuals from a population to estimate characteristics of the whole.

| Feature | Importance in Research |
| :--- | :--- |
| **Cost-Efficiency** | Reduces the financial resources required for data collection. |
| **Time-Saving** | Allows for faster data processing and analysis. |
| **Feasibility** | Makes it possible to study large or infinite populations. |
| **Accuracy** | Well-designed samples can provide highly accurate representations of the population. |

---

## Probability Sampling Methods
Probability sampling involves random selection, allowing for statistical inferences about the population.

*   **Simple Random Sampling (SRS):** Every member of the population has an equal chance of being selected.
*   **Stratified Random Sampling:** The population is divided into subgroups (strata), and samples are taken from each stratum.
*   **Cluster Sampling:** The population is divided into clusters (e.g., geographic areas), and entire clusters are randomly selected.
*   **Systematic Sampling:** Every $n^{th}$ individual is selected from a list after a random start.

---

## Non-Probability Sampling Methods
Non-probability sampling does not involve random selection and is often used for exploratory research.

*   **Convenience Sampling:** Selecting participants who are most accessible.
*   **Quota Sampling:** Ensuring specific subgroups are represented to a certain extent, but without random selection.
*   **Purposive Sampling:** Selecting participants based on the researcher's judgment and the study's purpose.
*   **Snowball Sampling:** Existing participants recruit future participants from among their acquaintances.

---

## Probability Theory & Distributions
**Probability Theory** is the mathematical framework for quantifying uncertainty. **Probability Distributions** describe how the values of a random variable are distributed.

### Common Distributions and Use Cases
| Distribution | Use Case Example |
| :--- | :--- |
| **Normal (Gaussian)** | Modeling heights, test scores, or measurement errors. |
| **Binomial** | Modeling the number of successes in a fixed number of Yes/No trials (e.g., coin flips). |
| **Poisson** | Modeling the number of events occurring in a fixed interval of time (e.g., customers arriving per hour). |
| **Bernoulli** | A single trial with two possible outcomes (Success/Failure). |

---

## Average vs. Weighted Average
Understanding the difference between these two measures of central tendency is crucial for accurate data representation.

> **Average (Arithmetic Mean):** The sum of all values divided by the total number of values. It treats all observations as equally important.
>
> **Weighted Average:** An average where each value is assigned a specific weight based on its importance or frequency.

### Example Comparison
Imagine a student's grades:
*   Assignment (Weight 20%): 90
*   Midterm (Weight 30%): 80
*   Final Exam (Weight 50%): 70

**Simple Average:** $(90 + 80 + 70) / 3 = 80$
**Weighted Average:** $(90 \times 0.2) + (80 \times 0.3) + (70 \times 0.5) = 18 + 24 + 35 = 77$

---

## Assignment: Proportionate Stratified Sampling
The following Python code demonstrates how to perform **Proportionate Stratified Sampling** on the `heart.csv` dataset. This method ensures that the sample maintains the same proportion of the target variable (`AHD` - Angiographic Heart Disease) as the original population.

```python
import pandas as pd
from sklearn.model_selection import train_test_split

# 1. Load the dataset
# Dataset source: Heart Disease dataset (heart.csv)
df = pd.read_csv('heart.csv', index_col=0)

# 2. Check original proportions of the target variable 'AHD'
print("Original Population Proportions:")
print(df['AHD'].value_counts(normalize=True))

# 3. Perform Proportionate Stratified Sampling
# We take a 20% sample (test_size=0.2)
# The 'stratify' parameter is key for proportionate sampling
stratified_sample, _ = train_test_split(
    df, 
    test_size=0.2, 
    stratify=df['AHD'], 
    random_state=42
)

# 4. Verify the sample proportions
print("\nStratified Sample Proportions:")
print(stratified_sample['AHD'].value_counts(normalize=True))

# 5. Save the sample
stratified_sample.to_csv('heart_stratified_sample.csv')
```

---

## How to Run the Code
1. Ensure you have Python installed.
2. Install the required library:
   ```bash
   pip install pandas scikit-learn
   ```
3. Place `heart.csv` in the same directory as the script.
4. Run the script to generate `heart_stratified_sample.csv`.
