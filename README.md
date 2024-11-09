# A/B Testing Project

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)
![A/B Testing](https://img.shields.io/badge/A%2FB-Testing-green.svg)

## Table of Contents

- [Introduction](#introduction)
- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Data Generation](#data-generation)
- [Statistical Tests](#statistical-tests)
  - [Chi-Squared Test](#chi-squared-test)
  - [Normal Distribution Analysis](#normal-distribution-analysis)
  - [Shapiro-Wilk Test](#shapiro-wilk-test)
  - [Levene’s Test for Equality of Variances](#levenes-test-for-equality-of-variances)
  - [Mann-Whitney U Test](#mann-whitney-u-test)
- [Results](#results)
- [Conclusion](#conclusion)
- [Project Structure](#project-structure)
- [License](#license)
- [Contact](#contact)

## Introduction

This project conducts an A/B test to compare the conversion rates of two groups, using statistical tests to determine if the difference in conversion rates is statistically significant. The project generates fake data to simulate different conversion rates between groups.

## Project Overview

Key steps in this project include:

1. **Data Generation**: Creating two datasets with different conversion rates.
2. **A/B Testing**:
   - Using **Chi-Squared Test** and **Normal Distribution Analysis** to evaluate conversion rate differences.
   - Running additional tests (Shapiro-Wilk, Levene, Mann-Whitney U) for validation and comparison.

## Technologies Used

- **Programming Language**: Python
- **Libraries**:
  - **Statistical Testing**: SciPy
  - **Data Handling**: Pandas, NumPy
  - **Visualization**: Matplotlib, Seaborn

## Data Generation

The project generates two synthetic datasets, each representing a different group with varied conversion rates. One group is designed to have a higher conversion rate to simulate a successful experiment.

### Example Code for Data Generation

```python
import numpy as np
import pandas as pd

# Generate data for control and test groups
np.random.seed(0)
control_group = np.random.binomial(1, 0.10, 1000)  # 10% conversion rate
test_group = np.random.binomial(1, 0.15, 1000)     # 15% conversion rate

# Create DataFrame
data = pd.DataFrame({
    'group': ['control'] * 1000 + ['test'] * 1000,
    'conversion': np.concatenate([control_group, test_group])
})
```
## Statistical Tests
### Chi-Squared Test
The Chi-Squared Test was used to test the independence between group membership and conversion outcome. This test helps determine if there’s a significant difference in conversion rates between the two groups.
```python
from scipy.stats import chi2_contingency

# Create contingency table
contingency_table = pd.crosstab(data['group'], data['conversion'])

# Chi-Squared Test
chi2, p, _, _ = chi2_contingency(contingency_table)
print(f"Chi2 Test Statistic: {chi2}, p-value: {p}")
```
### Normal Distribution Analysis
Using the Normal Distribution to approximate the difference in conversion rates. This test helps visualize and understand the distribution of conversion rates across both groups.
```python
from scipy.stats import norm

# Conversion rates
conversion_rate_control = control_group.mean()
conversion_rate_test = test_group.mean()
```
### Shapiro-Wilk Test
The Shapiro-Wilk Test checks for normality within each group’s conversion data, assessing if parametric assumptions hold.
```python
from scipy.stats import shapiro

# Shapiro-Wilk Test for normality
shapiro_control = shapiro(control_group)
shapiro_test = shapiro(test_group)
print("Shapiro Test for Control:", shapiro_control)
print("Shapiro Test for Test Group:", shapiro_test)
```
### Levene’s Test for Equality of Variances
The Levene’s Test checks for equality of variances between the two groups, helping validate assumptions for parametric testing.
```python
rom scipy.stats import levene

# Levene's Test
levene_test = levene(control_group, test_group)
print("Levene's Test:", levene_test)
```
### Mann-Whitney U Test
The Mann-Whitney U Test, a non-parametric test, was used as an alternative to compare the two groups without assuming normal distribution.
```python
from scipy.stats import mannwhitneyu

# Mann-Whitney U Test
mannwhitney_test = mannwhitneyu(control_group, test_group)
print("Mann-Whitney U Test:", mannwhitney_test)
```
## Results
The statistical tests show that:

- Chi-Squared Test: [Interpretation, e.g., “The test showed a significant difference between groups.”]
- Shapiro-Wilk and Levene Tests: [Interpretation, e.g., “The tests confirmed/disconfirmed normality and homogeneity of variances.”]
- Mann-Whitney U Test: [Interpretation, e.g., “This non-parametric test further validated the results.”]
### Summary of Test Results
| Test | Statistical value | p-value | Interpretation |
|------------------|------------------|-------------|---------------------|
| Chi-Squared Test |	...	 | ...	| Significant/Not Significant |
| Shapiro-Wilk |	...	| ...	| Normality Assumption Met/Violated |
| Levene’s Test z |	...	| ...	| Equal Variance Assumption Met/Violated |
| Mann-Whitney U Test |	... |	... |	Additional confirmation |

## Conclusion
The project demonstrates the application of A/B testing techniques to evaluate differences in conversion rates. The results suggest that the test group outperformed the control group in conversion, providing insights into the effectiveness of A/B testing in decision-making.
## Project Structure
```css
ab-testing/
│
├── data/
│   ├── control_group.csv
│   ├── test_group.csv
│
├── notebooks/
│   ├── Data_Generation.ipynb
│   ├── Statistical_Tests.ipynb
│
├── src/
│   ├── data_generation.py
│   ├── ab_test_analysis.py
│
├── README.md
└── LICENSE
```
## License
This project is licensed under the MIT License. See the LICENSE file for details.
## Contact
Mohammed Ammaruddin
md.ammaruddin2020@gmail.com
