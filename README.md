# Exercise 15 — Working with NumPy Operations

A practical NumPy exercise notebook covering **business analytics, education data analysis, mathematical operations, trigonometric series, and convergence**.

<p align="center">
<img src="./screenshots/screen 1.png" width="900">
</p>

## Overview

This exercise demonstrates how NumPy can be used to:

- Create and inspect one-dimensional numerical arrays
- Calculate totals and averages
- Apply percentage-based adjustments using vectorized operations
- Compare original and adjusted datasets
- Calculate deviations from a mean
- Square values and calculate sums
- Calculate standard deviation
- Convert angles from degrees to radians
- Generate numerical sequences with `np.arange()`
- Perform trigonometric calculations with `np.sin()`
- Build and sum series terms
- Investigate how increasing the number of terms affects an approximation

<p align="center">
<img src="./screenshots/screen 2.png" width="900">
</p>

---

## Technologies Used

- **Python**
- **NumPy**
- **Jupyter Notebook**

### Main Library

```python
import numpy as np
```

---

# Exercise 1 — Business Analytics: Sales Performance Calculator

## Objective

Analyze a firm's daily sales records using NumPy and calculate key sales metrics, including total sales, average sales, adjusted sales, and the difference between original and adjusted figures.

## Task 1 — Create the Dataset

The notebook creates a one-dimensional NumPy array containing seven daily sales records.

```python
daily_sales = np.array([
    125000, 150000, 175000, 140000,
    190000, 210000, 160000
])
```

### Dataset

| Day | Sales |
|---|---:|
| 1 | 125,000 |
| 2 | 150,000 |
| 3 | 175,000 |
| 4 | 140,000 |
| 5 | 190,000 |
| 6 | 210,000 |
| 7 | 160,000 |

The notebook confirms that `daily_sales` is a NumPy array:

```text
<class 'numpy.ndarray'>
```

## Task 2 — Calculate Total Sales

NumPy's `np.sum()` is used to calculate the cumulative sales.

```python
total_sales = np.sum(daily_sales)
```

### Result

**Total Sales: 1,150,000**

---

## Task 3 — Calculate Average Daily Sales

The average daily sales value is calculated with `np.mean()`.

```python
average_sales = np.mean(daily_sales)
```

### Result

**Average Sales: 164,285.71**

The notebook explains that the average provides a way for the business to compare its daily performance against an expected or fixed sales target.

---

## Task 4 — Apply a 10% Sales Adjustment

A 10% increment is calculated for every sales value and added to the original dataset.

```python
increment = daily_sales * (10 / 100)
adjusted_sales = daily_sales + increment
```

### Adjusted Sales

```text
[137500. 165000. 192500. 154000. 209000. 231000. 176000.]
```

This demonstrates NumPy's ability to perform arithmetic operations across an entire array without manually processing each value.

---

## Task 5 — Compare Original and Adjusted Sales

The difference between the adjusted and original sales records is calculated using array subtraction.

```python
sales_difference = adjusted_sales - daily_sales
```

### Result

```text
[12500. 15000. 17500. 14000. 19000. 21000. 16000.]
```

The result represents the estimated 10% increase for each corresponding daily sales value.

---

## Task 6 — Total Sales vs. Average Sales

The notebook distinguishes between the information provided by total sales and average sales:

- **Total sales** represents the cumulative sales generated over the recorded period.
- **Average daily sales** provides a per-day performance measure that can be compared with a daily or weekly sales target.

### Key Takeaway

> Total sales shows the overall amount generated, while average sales provides more context about typical daily performance.

---

# Exercise 2 — Education Analysis: Student Performance Analysis

## Objective

Use NumPy to analyze student scores, calculate the mean, determine deviations, square those deviations, calculate their sum, and use the results to obtain a standard deviation.

## Task 1 — Create and Inspect the Dataset

The notebook creates an array containing ten student scores.

```python
scores = np.array([
    62, 75, 81, 69, 88,
    94, 73, 85, 77, 91
])
```

### Scores

| Student | Score |
|---|---:|
| 1 | 62 |
| 2 | 75 |
| 3 | 81 |
| 4 | 69 |
| 5 | 88 |
| 6 | 94 |
| 7 | 73 |
| 8 | 85 |
| 9 | 77 |
| 10 | 91 |

The dataset is stored as a NumPy array:

```text
<class 'numpy.ndarray'>
```

---

## Task 2 — Calculate the Mean Score

The mean score is calculated with `np.mean()`.

```python
mean_score = np.mean(scores)
```

### Result

**Mean Score: 79.5**

---

## Task 3 — Calculate Each Student's Deviation

Each student's deviation from the mean is calculated by subtracting the mean score from each student's score.

```python
deviation = scores - mean_score
```

### Result

```text
[-17.5, -4.5, 1.5, -10.5, 8.5,
 14.5, -6.5, 5.5, -2.5, 11.5]
```

This demonstrates NumPy's element-wise subtraction.

---

## Task 4 — Identify Positive and Negative Deviations

The notebook explains deviations in relation to the reference threshold used in the exercise.

- A **positive deviation** indicates a score above the reference value.
- A **negative deviation** indicates a score below the reference value.
- A value **close to zero** indicates that the score is close to the reference value.

> In the notebook's calculation, the deviations are specifically computed from the **mean score of 79.5**.

---

## Task 5 — Square the Deviations

The deviations are squared using NumPy's element-wise exponentiation.

```python
squared_deviation = deviation ** 2
```

### Result

```text
[306.25, 20.25, 2.25, 110.25, 72.25,
 210.25, 42.25, 30.25, 6.25, 132.25]
```

Squaring converts negative deviation values into positive values because a negative number multiplied by itself produces a positive result.

---

## Task 6 — Calculate the Sum of Squared Deviations

The squared deviations are summed using `np.sum()`.

```python
sum_of_squared_deviations = np.sum(squared_deviation)
```

### Result

**932.5**

---

## Task 7 — Connect the Steps to Standard Deviation

The notebook follows this sequence:

```text
Calculate the mean
        ↓
Calculate deviations
        ↓
Square the deviations
        ↓
Sum the squared deviations
        ↓
Calculate the standard deviation
```

The number of recorded student scores is obtained using:

```python
N = len(scores)
```

The notebook then calculates standard deviation using:

```python
standard_deviation = np.sqrt(
    1 / (N - 1) * sum_of_squared_deviations
)
```

### Result

**Standard Deviation: 10.18**

The use of `N - 1` means the notebook is applying the **sample standard deviation** formula.

---

## Why Standard Deviation Matters

The notebook explains that the mean shows where the scores are centered, while standard deviation provides additional information about how the scores vary around that center.

A mean alone does not show whether:

- Scores are relatively close to one another
- Some students are performing substantially above the mean
- Other students are performing substantially below the mean

### Key Takeaway

> Looking beyond the average can provide additional information about the distribution and consistency of student performance.

---

# Exercise 3 — Engineering and Scientific Computing: Trigonometric Series and Convergence

## Objective

Use NumPy to convert an angle, generate a sequence of values, calculate a trigonometric component, construct series terms, calculate their sums, and investigate how the result changes as the number of terms increases.

## Task 1 — Define the Angle

The notebook begins with an angle of 30 degrees.

```python
theta = 30
theta_radians = np.radians(theta)
```

### Result

**Angle in radians: 0.5**

`np.radians()` converts the angle from degrees to radians.

---

## Task 2 — Create the Sequence of Terms

A sequence from 1 through 99 is generated with `np.arange()`.

```python
k = np.arange(1, 100, 1)
```

The sequence therefore contains:

- First value: `1`
- Last value: `99`
- Number of values: `99`

---

## Task 3 — Calculate the Trigonometric Component

The sine of the angle in radians is calculated with `np.sin()`.

```python
trigonometric_component = np.sin(theta_radians)
```

### Result

Approximately:

```text
0.5
```

---

## Task 4 — Build the Series Terms

The notebook constructs the terms using:

```python
terms = np.sin(theta_radians) / k
```

This produces an array where the sine component is divided by each value in the `k` sequence.

The first several terms are:

```text
0.5
0.25
0.16666667
0.125
0.1
...
```

---

## Task 5 — Calculate the Sum

The series terms are summed using:

```python
total_terms = np.sum(terms)
```

### Result

**Total Terms: 2.5886887588198104**

---

## Task 6 — Increase the Number of Terms

The notebook then changes the series expression to:

```python
terms = np.sin(k + theta_radians) / k
```

It evaluates the expression using three different sequence lengths.

### Results

| Number of Terms | Series Result |
|---:|---:|
| 99 | 0.939234003522875 |
| 999 | 0.9477794883282241 |
| 9,999 | 0.9484451042034616 |

### Code Pattern

```python
# K = 99
k = np.arange(1, 100, 1)
terms = np.sin(k + theta_radians) / k
total_terms1 = np.sum(terms)

# K = 999
k = np.arange(1, 1000, 1)
terms = np.sin(k + theta_radians) / k
total_terms2 = np.sum(terms)

# K = 9,999
k = np.arange(1, 10000, 1)
terms = np.sin(k + theta_radians) / k
total_terms3 = np.sum(terms)
```

---

## Task 7 — Investigate Convergence

The notebook compares the three results:

| Number of Terms | Result |
|---:|---:|
| 99 | 0.939234003522875 |
| 999 | 0.9477794883282241 |
| 9,999 | 0.9484451042034616 |

The notebook observes that the series result moves closer to **1** as the number of terms increases.

---

## Task 8 — Explain Convergence

The notebook's explanation can be summarized as follows:

1. With fewer terms, the approximation is farther from the observed limiting value.
2. Increasing the number of terms moves the result closer to the limiting value observed in the exercise.
3. Each additional term contributes to the total, while the contributions become smaller.
4. As the number of terms increases, the changes in the approximation become smaller.

### Key Concept

> Increasing the number of terms can improve a numerical approximation when the additional terms progressively contribute smaller changes to the result.

---

# NumPy Operations Demonstrated

The notebook provides practical examples of several NumPy functions and operations.

| Operation | NumPy / Python Feature | Purpose |
|---|---|---|
| Array creation | `np.array()` | Create numerical arrays |
| Sum | `np.sum()` | Calculate the total of array values |
| Mean | `np.mean()` | Calculate the arithmetic average |
| Element-wise multiplication | `array * value` | Apply a factor to every element |
| Element-wise addition | `array + array` | Add corresponding array elements |
| Element-wise subtraction | `array - array` | Calculate corresponding differences |
| Exponentiation | `array ** 2` | Square each element |
| Square root | `np.sqrt()` | Calculate square roots |
| Array length | `len()` | Count values in an array |
| Degree-to-radian conversion | `np.radians()` | Convert angles to radians |
| Sine | `np.sin()` | Calculate sine values |
| Sequence generation | `np.arange()` | Generate evenly spaced integer values |

---

# Concepts Practiced

## 1. NumPy Arrays

The exercises use one-dimensional `numpy.ndarray` objects to store numerical datasets.

## 2. Vectorized Operations

The notebook performs operations directly on complete arrays:

```python
adjusted_sales = daily_sales + daily_sales * 0.10
```

Instead of manually calculating each value, NumPy applies the operation element by element.

## 3. Descriptive Statistics

The student-performance section demonstrates:

- Mean
- Deviations from the mean
- Squared deviations
- Sum of squared deviations
- Sample standard deviation

## 4. Mathematical Functions

The notebook applies:

- Square roots
- Sine
- Degree-to-radian conversion

## 5. Numerical Series

The final section demonstrates how a numerical series can be constructed, summed, and evaluated with increasing numbers of terms.

## 6. Convergence

The exercise compares results at different sequence lengths to observe how the numerical approximation changes as more terms are included.

---

# Summary of Results

| Exercise | Calculation | Result |
|---|---|---:|
| Business Analytics | Total Sales | **1,150,000** |
| Business Analytics | Average Daily Sales | **164,285.71** |
| Student Analysis | Mean Score | **79.5** |
| Student Analysis | Sum of Squared Deviations | **932.5** |
| Student Analysis | Sample Standard Deviation | **10.18** |
| Scientific Computing | 30° in radians | **0.5** |
| Scientific Computing | `sin(30°)` | **≈ 0.5** |
| Scientific Computing | Initial series sum | **2.5886887588198104** |
| Convergence | 99 terms | **0.939234003522875** |
| Convergence | 999 terms | **0.9477794883282241** |
| Convergence | 9,999 terms | **0.9484451042034616** |

---

# Learning Outcomes

After completing this exercise, the following practical NumPy skills are demonstrated:

- Creating and inspecting NumPy arrays
- Performing vectorized arithmetic
- Calculating aggregate statistics
- Comparing numerical datasets
- Working with deviations and standard deviation
- Applying mathematical functions to arrays
- Generating numerical sequences
- Building and summing numerical series
- Observing changes in numerical approximations as the number of terms increases

---

# Project Structure

A suitable GitHub repository structure for this exercise is:

```text
.
├── Exercise 15-Working with NumPy Operations.ipynb
└── README.md
```

The Jupyter Notebook contains the original exercises, code, explanations, and displayed results, while this documentation provides a structured overview of what the notebook demonstrates.

---

# Notes

- The documentation above is based directly on the contents and outputs of the provided notebook.
- The notebook contains three major exercises covering business analytics, student performance, and scientific computing.
- In the convergence section, the series expression used for the larger-term comparison is `np.sin(k + theta_radians) / k`, which differs from the earlier expression `np.sin(theta_radians) / k`.
- The notebook ends with an additional code cell containing `S` without a displayed result. This appears to be an unfinished or stray cell in the provided notebook.

---

## Author

**Victor Ukachi Chiemela**

This exercise forms part of practical Python/NumPy learning and demonstrates the application of numerical computing concepts to real-world-style analytical problems.
