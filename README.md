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
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
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
