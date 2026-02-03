# Statistics Course Notes Summary

This document provides a comprehensive overview of the fundamental concepts and terms covered in the **Statistics Course Notes**. It is designed as a quick reference guide for both **Descriptive** and **Inferential Statistics**, including practical Excel applications.

---

## 1. Descriptive Statistics

Descriptive statistics focus on summarizing and describing the features of a dataset.

### Data Types and Measurement
| Category | Sub-type | Description | Examples |
| :--- | :--- | :--- | :--- |
| **Categorical** | Nominal | Categories with no inherent order. | Car brands, Seasons |
| | Ordinal | Categories with a logical order. | Meal ratings (Poor to Excellent) |
| **Numerical** | Discrete | Countable values. | Number of children, SAT scores |
| | Continuous | Infinite, measurable values. | Weight, Height, Time |

### Levels of Measurement
*   **Qualitative:** Nominal and Ordinal.
*   **Quantitative:** Interval (no true zero, e.g., Celsius) and Ratio (true zero, e.g., Kelvin, Length).

### Visualizing Data
*   **Categorical:** Bar Charts, Pie Charts, Pareto Diagrams (descending order with cumulative frequency curve).
*   **Numerical:** Histograms (bars touch to show continuity).
*   **Relationships:** Cross Tables (Contingency Tables), Side-by-side Bar Charts, and Scatter Plots (used to detect patterns like linearity).

### Measures of Central Tendency & Dispersion
*   **Mean:** The simple average (sensitive to outliers).
*   **Median:** The midpoint of an ordered dataset (robust to outliers).
*   **Mode:** The most frequent value.
*   **Skewness:** Measures asymmetry (Right/Positive vs. Left/Negative).
*   **Variance & Standard Deviation:** Measure data dispersion around the mean.
*   **Covariance & Correlation:** Measure joint variability between two variables. Correlation is standardized (-1 to 1).

---

## 2. Inferential Statistics

Inferential statistics use sample data to make generalizations about a larger population.

### Key Distributions
*   **Normal Distribution (Gaussian):** The "Bell Curve," defined by mean ($\mu$) and variance ($\sigma^2$).
*   **Standard Normal Distribution:** A normal distribution with $\mu=0$ and $\sigma=1$. Uses **Z-scores** for standardization.
*   **Student’s T Distribution:** Used for small samples or when population variance is unknown; has "fatter tails" to account for uncertainty.
*   **Others:** Binomial, Poisson, and Uniform distributions.

### The Central Limit Theorem (CLT)
The CLT states that the sampling distribution of the mean will approximate a normal distribution as the sample size ($n$) becomes large, regardless of the population's original distribution.

### Estimation
*   **Point Estimate:** A single value (e.g., sample mean).
*   **Confidence Interval (CI):** A range of values within which we expect the population parameter to fall, governed by the **Level of Confidence (1-$\alpha$)**.
*   **Margin of Error (ME):** The range added/subtracted from the point estimate.

---

## 3. Hypothesis Testing

A systematic method for testing claims about a population.

### Core Concepts
*   **Null Hypothesis ($H_0$):** The status-quo or statement to be tested (assumed true until proven otherwise).
*   **Alternative Hypothesis ($H_1$):** The new claim or innovation being tested.
*   **Significance Level ($\alpha$):** The probability of rejecting a true null hypothesis (Type I Error). Common levels: 0.01, 0.05, 0.10.
*   **P-value:** The smallest significance level at which $H_0$ can be rejected. A p-value < $\alpha$ typically leads to rejecting $H_0$.

### Statistical Errors
| Error Type | Name | Description |
| :--- | :--- | :--- |
| **Type I** | False Positive | Rejecting $H_0$ when it is actually true. |
| **Type II** | False Negative | Failing to reject $H_0$ when it is actually false. |

---

## 4. Excel Functions Reference

| Task | Excel Formula |
| :--- | :--- |
| **Central Tendency** | `=AVERAGE()`, `=MEDIAN()`, `=MODE.SNGL()` |
| **Dispersion** | `=VAR.S()`, `=STDEV.S()`, `=SKEW()` |
| **Relationships** | `=CORREL()`, `=COVARIANCE.S()` |
| **Counting** | `=COUNTIF()`, `=SUM()` |

---

> **Note:** For detailed formulas and step-by-step Excel tutorials, refer to the original course documentation and accompanying exercise files.
