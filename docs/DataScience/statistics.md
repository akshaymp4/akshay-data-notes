<div class="aws-hero">
  <div class="aws-chip">Data Science | Statistics | Inference</div>
  <h1>Statistics</h1>
  <p>
    Statistics is the subject of collecting, organizing, analyzing, and interpreting data.
    It covers how data is summarized, how uncertainty is measured, how conclusions are drawn from samples,
    and how relationships between variables are studied.
  </p>
</div>

## 1.1 What Is Statistics? { .aws-h2 }

Statistics helps us understand data and make decisions using evidence instead of guesses.

In simple words:

- It helps summarize data
- It helps compare groups
- It helps test claims
- It helps estimate unknown values
- It helps study relationships between variables

Simple example:

- A company wants to know whether customer satisfaction is improving
- Statistics helps summarize survey scores and test whether the change is real

**High-level tree:**

```text
Statistics
|
+-- Descriptive Statistics
|   +-- What happened in the data?
|   +-- Mean, Median, Mode
|   +-- Range, Variance, Standard Deviation
|   +-- Quartiles, Percentiles, Z-score
|   +-- Skewness, Kurtosis
|
+-- Inferential Statistics
    +-- What will happen or what can be concluded beyond the sample?
    +-- Sampling
    +-- Central Limit Theorem
    +-- Estimation
    +-- Confidence Interval
    +-- Hypothesis Testing
    +-- Correlation and Regression
```

## 1.2 Main Branches of Statistics { .aws-h2 }

### 1.2.1 Descriptive Statistics { .aws-h3 }

Descriptive statistics is used to summarize and present the data we already have.

In one line: descriptive statistics answers **what happened** in the data.

Used for:

- averages
- spread of data
- charts
- percentages
- summary tables

Example:

- Find the average salary of 100 employees
- Show the minimum, maximum, and median sales value

### 1.2.2 Inferential Statistics { .aws-h3 }

Inferential statistics is used to draw conclusions about a population using a sample.

In one line: inferential statistics answers **what will happen**, or more carefully, what is likely true beyond the sample data.

Used for:

- estimation
- confidence intervals
- hypothesis testing
- comparing groups
- prediction support

Example:

- A hospital studies 200 patients and uses that sample to estimate the recovery rate for all patients

## 1.3 Detailed Statistics Hierarchy Chart { .aws-h2 }

```text
Statistics
|
+-- Descriptive Statistics
|   |
|   +-- Central Tendency
|   |   +-- Mean
|   |   +-- Median
|   |   +-- Mode
|   |
|   +-- Dispersion
|   |   +-- Range
|   |   +-- Variance
|   |   +-- Standard Deviation
|   |   +-- IQR
|   |
|   +-- Position Measures
|   |   +-- Quartiles
|   |   +-- Percentiles
|   |   +-- Z-score
|   |
|   +-- Shape of Distribution
|       +-- Skewness
|       +-- Kurtosis
|
+-- Probability and Distributions
|   |
|   +-- Random Variable
|   |   +-- Discrete
|   |   +-- Continuous
|   |
|   +-- Distributions
|       +-- Bernoulli
|       +-- Binomial
|       +-- Poisson
|       +-- Uniform
|       +-- Normal
|
+-- Sampling and Estimation
|   |
|   +-- Population vs Sample
|   +-- Sampling Techniques
|   +-- Sampling Distribution
|   +-- Central Limit Theorem
|   +-- Point Estimation
|   +-- Interval Estimation
|   +-- Confidence Interval
|
+-- Hypothesis Testing
|   |
|   +-- Null and Alternative Hypothesis
|   +-- Type I and Type II Error
|   +-- P-value
|   +-- Z Test
|   +-- T Test
|   +-- Chi-Square Test
|   +-- ANOVA
|
+-- Relationship and Prediction
    |
    +-- Covariance
    +-- Correlation
    +-- Regression
```

## 1.4 Basic Terms You Must Know { .aws-h2 }

### 1.4.1 Data and Variable { .aws-h3 }

- **Data**: collection of values or observations
- **Variable**: a property that can change from one observation to another

Examples:

- age
- salary
- city
- exam marks

### 1.4.2 Types of Variables { .aws-h3 }

- **Categorical variable**: stores labels such as gender, city, payment type
- **Numerical variable**: stores numbers such as height, marks, income
- **Discrete variable**: countable values such as number of calls
- **Continuous variable**: measured values such as weight, time, speed

Example:

- Number of customers entering a store is discrete
- Waiting time of a customer is continuous

### 1.4.3 Population, Sample, Parameter, Statistic { .aws-h3 }

- **Population**: the complete group we want to study
- **Sample**: a smaller part selected from the population
- **Parameter**: a value describing the population
- **Statistic**: a value describing the sample

Example:

- All voters in a state = population
- 2,000 surveyed voters = sample

| Population Quantity | Sample Quantity |
|---|---|
| Mean `mu` | Mean `x_bar` |
| Variance `sigma^2` | Variance `s^2` |
| Standard deviation `sigma` | Standard deviation `s` |
| Proportion `p` | Sample proportion `p_hat` |

## 1.5 Descriptive Statistics { .aws-h2 }

### 1.5.1 Measures of Central Tendency { .aws-h3 }

Measures of central tendency describe the **center** or typical value of a dataset.

Common measures:

- **Mean**: arithmetic average
- **Median**: middle value
- **Mode**: most frequent value

#### Mean

**Definition:**

Mean is the average of all values.

**Formula:**

```text
Mean = Sum of all values / Number of values
x_bar = (x1 + x2 + ... + xn) / n
```

**Simple explanation:**

Add everything and divide by how many values you have.

**Example:**

Marks = 60, 70, 80

Mean = `(60 + 70 + 80) / 3 = 70`

**Real-world use:**

- average monthly sales
- average student marks
- average temperature

#### Median

**Definition:**

Median is the middle value after sorting the data.

**Formula:**

```text
First sort the data in ascending order.

If n is odd:
Median = value at position (n + 1) / 2

If n is even:
Median = [value at position n / 2 + value at position (n / 2) + 1] / 2
```

**Formula idea:**

- If `n` is odd: middle value
- If `n` is even: average of the two middle values

**Simple explanation:**

Median shows the center of the data without being heavily affected by extreme values.

**Example:**

Data = 10, 15, 20, 100

Median = `(15 + 20) / 2 = 17.5`

**Real-world use:**

- salary analysis where a few very high salaries can distort the mean

#### Mode

**Definition:**

Mode is the most frequently occurring value.

**Formula idea:**

```text
Mode = value with the highest frequency
```

If two values appear most often, the data is **bimodal**. If more than two values share the highest frequency, the data is **multimodal**.

**Simple explanation:**

It tells what value appears the most.

**Example:**

Data = 2, 3, 3, 5, 7

Mode = `3`

**Real-world use:**

- most common shirt size sold
- most used payment method

### 1.5.2 Measures of Variation or Dispersion { .aws-h3 }

Measures of variation, also called measures of dispersion, describe how much the data values are spread out.

Common measures:

- **Range**: total spread from smallest to largest value
- **Variance**: average squared distance from the mean
- **Standard deviation**: typical distance from the mean in the original unit
- **IQR**: spread of the middle 50% of the data

#### Range

**Definition:**

Range is the difference between the maximum and minimum values.

**Formula:**

```text
Range = Maximum - Minimum
```

**Simple explanation:**

It tells how wide the data is spread from smallest to largest.

**Example:**

Data = 12, 15, 20, 25

Range = `25 - 12 = 13`

#### Variance

**Definition:**

Variance measures how far data points are spread from the mean.

**Population formula:**

Use this when the data contains the full population.

```text
sigma^2 = Sum[(xi - mu)^2] / N
```

Where:

- `sigma^2` = population variance
- `xi` = each data value
- `mu` = population mean
- `N` = number of values in the population

**Sample formula:**

Use this when the data is only a sample from a larger population.

```text
s^2 = Sum[(xi - x_bar)^2] / (n - 1)
```

Where:

- `s^2` = sample variance
- `xi` = each sample value
- `x_bar` = sample mean
- `n` = number of values in the sample
- `n - 1` is used for sample variance because a sample usually underestimates population spread

**Simple explanation:**

Take each value, see how far it is from the average, square that distance, add all squared distances, and divide by `N` for population data or `n - 1` for sample data.

**Small example:**

Data = 2, 4, 6

Mean = `(2 + 4 + 6) / 3 = 4`

Squared gaps:

```text
(2 - 4)^2 = 4
(4 - 4)^2 = 0
(6 - 4)^2 = 4
```

Population variance = `(4 + 0 + 4) / 3 = 2.67`

Sample variance = `(4 + 0 + 4) / (3 - 1) = 4`

**Example use:**

- compare whether two stores have stable or unstable daily sales

#### Standard Deviation

**Definition:**

Standard deviation is the square root of variance.

Another common way to describe it is: standard deviation is the typical or average-like distance of observations from a central point, usually the mean.

**Formula:**

```text
Step 1: Find the mean
Step 2: Find how far each value is from the mean
Step 3: Square those differences
Step 4: Average them to get variance
Step 5: Take the square root

Standard deviation = sqrt(variance)
s = sqrt(s^2)
```

**Simple explanation:**

It tells the typical distance of values from the mean in the original unit.

**Relation with standard error of the mean:**

Standard deviation and standard error are related, but they are not the same.

- **Standard deviation (SD)** describes how individual data points are spread out
- **Standard error of the mean (SEM)** describes how sample means are spread out

```text
SEM = s / sqrt(n)
```

**Example:**

- If average delivery time is 30 minutes and standard deviation is 2 minutes, delivery times are usually close to 30

#### Quartiles and Percentiles

**Quartiles** divide sorted data into 4 equal parts.

- `Q1`: 25th percentile
- `Q2`: 50th percentile or median
- `Q3`: 75th percentile

**Percentiles** divide sorted data into 100 parts.

**IQR Formula:**

```text
IQR = Q3 - Q1
```

**Simple explanation:**

These measures show where a value stands inside the dataset.

**Real-world use:**

- exam rankings
- salary bands
- customer spend segmentation

### 1.5.3 Position Measures { .aws-h3 }

Position measures describe where a value stands compared with the rest of the data.

#### Z-Score

**Definition:**

Z-score tells how many standard deviations a value is away from the mean.

**Formula:**

```text
z = (x - mu) / sigma
```

**Simple explanation:**

- positive z-score means above average
- negative z-score means below average
- zero means exactly average

**Example:**

If mean score is 70, standard deviation is 10, and a student got 90:

`z = (90 - 70) / 10 = 2`

The student is 2 standard deviations above average.

**Difference between z-score and z-value:**

| Term | Meaning | Common use |
|---|---|---|
| **Z-score** | A standardized value calculated from one data point | Describing where one observation lies in a distribution |
| **Z-value** | A cutoff value from the standard normal distribution | Confidence intervals and hypothesis tests |

Example:

- A student's mark may have a **z-score** of `2`
- A 95% confidence interval often uses the **z-value** `1.96`

**Small reference to the Z table:**

A Z table gives the area or probability under the standard normal curve for a given z-value. For example, `z = 1.96` gives about `0.975` area to the left, which is why `1.96` is commonly used for two-sided 95% confidence intervals.

### 1.5.4 Shape of Distribution { .aws-h3 }

#### Skewness and Kurtosis

**Skewness** tells the direction of asymmetry.

- right skew: long tail on right
- left skew: long tail on left

**Kurtosis** tells how heavy or light the tails are.

**Simple explanation:**

- skewness helps understand shape
- kurtosis helps understand extreme values

**Real-world example:**

- income data is often right-skewed because a small number of people earn much more than the rest

```python
import numpy as np
from scipy import stats

values = np.array([10, 12, 15, 15, 18, 20, 24])
print("mean:", values.mean())
print("median:", np.median(values))
print("mode:", stats.mode(values, keepdims=False).mode)
print("variance:", values.var(ddof=1))
print("std:", values.std(ddof=1))
print("q1, q3:", np.percentile(values, [25, 75]))
```

## 1.6 Probability and Random Variables { .aws-h2 }

### 1.6.1 Random Experiment and Sample Space { .aws-h3 }

- **Random experiment**: an action with uncertain outcome
- **Sample space**: all possible outcomes

Example:

- Roll a die
- Sample space = `{1, 2, 3, 4, 5, 6}`

### 1.6.2 Random Variable { .aws-h3 }

A random variable is a numerical value assigned to an outcome of a random experiment.

Types:

- **Discrete random variable**: takes countable values
- **Continuous random variable**: takes values over a range

Examples:

- number of complaints in a day = discrete
- amount of rainfall = continuous

### 1.6.3 Probability Distribution { .aws-h3 }

Probability distribution tells how probabilities are assigned to values of a random variable.

Important forms:

- **PMF** for discrete variables
- **PDF** for continuous variables
- **CDF** for cumulative probability

**PMF: Probability Mass Function**

A PMF gives the probability of an exact value for a **discrete** random variable.

```text
PMF = P(X = x)
```

Example:

- probability of getting exactly 3 heads
- probability of receiving exactly 2 calls in one hour

**PDF: Probability Density Function**

A PDF describes the density of probability for a **continuous** random variable.

For continuous variables, the probability at one exact point is usually `0`, so we use area under the curve over an interval.

```text
P(a <= X <= b) = area under the PDF curve from a to b
```

Example:

- probability that height is between 160 cm and 170 cm
- probability that delivery time is between 25 and 30 minutes

**CDF: Cumulative Distribution Function**

A CDF gives the probability that a random variable is less than or equal to a value.

```text
CDF = P(X <= x)
```

Example:

- `P(X <= 3)` means probability that `X` is at most 3
- `norm.cdf(1.96)` means area under the standard normal curve to the left of `1.96`

For a **discrete random variable**, the distribution is written using probabilities assigned to each possible value. One important discrete distribution is the **binomial distribution**, but discrete distributions also include **Bernoulli**, **Poisson**, and **categorical** distributions.

**Categorical distribution in brief:**

Categorical distribution is used when one observation can fall into one of several categories.

Example:

- a user clicks an ad from **search**, **social**, **email**, or **display**

If the probabilities of these categories are `p1, p2, p3, ..., pk`, then the categorical distribution tells the probability of each category.

### 1.6.4 Expected Value and Variance of Random Variable { .aws-h3 }

**Expected value** is the long-run average.

**Formula for discrete case:**

```text
E(X) = x1 * P(X = x1) + x2 * P(X = x2) + ... + xn * P(X = xn)
```

**Variance formula:**

```text
Var(X) = Sum[(value - mean)^2 * probability of that value]
```

**Simple explanation:**

- expected value tells the average outcome in the long run
- variance tells how much outcomes move around that average

## 1.7 Common Probability Distributions { .aws-h2 }

```text
Probability Distributions
|
+-- Discrete Distributions
|   +-- Categorical
|   |   +-- Example: which ad channel did the user click from? search / social / email / display
|   +-- Bernoulli
|   |   +-- Example: did a user click an ad? yes or no
|   +-- Binomial
|   |   +-- Example: out of 100 users shown an ad, how many clicked?
|   +-- Poisson
|       +-- Example: how many ad clicks happened in one minute?
|
+-- Continuous Distributions
    +-- Uniform
    |   +-- Example: a random value chosen anywhere between 0 and 1 with equal chance
    +-- Normal
        +-- Example: average daily ad clicks across many days often cluster around a center
```

### 1.7.1 Categorical Distribution { .aws-h3 }

Used when one observation belongs to exactly one of several categories.

Examples:

- which ad channel a user clicked from
- preferred payment method of a customer
- blood group of a patient

**Simple probability idea:**

```text
P(X = category i) = pi
```

where all category probabilities add up to 1.

### 1.7.2 Bernoulli Distribution { .aws-h3 }

Used for one trial with only two outcomes.

Examples:

- pass or fail
- success or failure
- heads or tails

**Formula:**

```text
P(X = x) = p^x * (1-p)^(1-x), where x = 0 or 1
```

**Mean and variance:**

```text
Mean = p
Variance = p(1-p)
```

### 1.7.3 Binomial Distribution { .aws-h3 }

Used for the number of successes in `n` independent trials.

Examples:

- number of customers who click an ad out of 100 users
- number of defective bulbs in a batch sample

**Formula:**

```text
P(X = x) = nCx * p^x * (1-p)^(n-x)
```

Read it as:

```text
Probability of exactly x successes
= number of ways to choose x successes
  * (success probability)^x
  * (failure probability)^(remaining trials)
```

**Mean and variance:**

```text
Mean = np
Variance = np(1-p)
```

### 1.7.4 Poisson Distribution { .aws-h3 }

Used to model counts of events in a fixed interval.

Examples:

- number of calls received in an hour
- number of website errors per day

**Formula:**

```text
P(X = x) = (e^(-lambda) * lambda^x) / x!
```

Read it as:

```text
Probability of exactly x events in a fixed interval
when events occur at an average rate lambda
```

**Mean and variance:**

```text
Mean = lambda
Variance = lambda
```

### 1.7.5 Uniform Distribution { .aws-h3 }

All values in a range are equally likely.

Example:

- random number generated between 0 and 1

**Continuous uniform density:**

```text
f(x) = 1 / (b - a), for a <= x <= b
```

### 1.7.6 Normal Distribution { .aws-h3 }

Normal distribution is a bell-shaped, symmetric distribution.

Examples:

- exam scores
- IQ scores
- measurement errors

**Formula:**

```text
f(x) = [1 / (sigma * sqrt(2*pi))] * e^(-(x-mu)^2 / (2*sigma^2))
```

For first-time learning, the most useful idea is usually the shape:

- center is around `mu`
- spread is controlled by `sigma`
- values closer to the mean are more common

**Mean and variance:**

```text
Mean = mu
Variance = sigma^2
```

**Simple explanation:**

Most values stay near the center, and fewer values appear in the tails.

**Standard normal transformation:**

```text
z = (x - mu) / sigma
```

**Area within standard deviations of the mean:**

- from `mu - 1sigma` to `mu + 1sigma` = about `68.2%`
- from `mu - 2sigma` to `mu + 2sigma` = about `95.4%`
- from `mu - 3sigma` to `mu + 3sigma` = about `99.7%`

This is often called the **68-95-99.7 rule**.

### 1.7.7 When to Use Which Distribution { .aws-h3 }

| Situation | Distribution |
|---|---|
| One outcome from many named categories | Categorical |
| One trial with yes/no outcome | Bernoulli |
| Number of successes in a fixed number of trials | Binomial |
| Number of events in a fixed time or space interval | Poisson |
| Continuous value where all values in a range are equally likely | Uniform |
| Continuous bell-shaped data around a center | Normal |

Ad-click examples:

- Use **categorical** when tracking where the click came from: search, social, email, or display
- Use **Bernoulli** for one user impression: clicked or did not click
- Use **binomial** for a fixed campaign sample: how many clicks out of 100 shown ads
- Use **Poisson** for click counts in time: how many clicks in one minute
- Use **normal** when looking at averages, such as average daily clicks across many days

```python
from scipy.stats import bernoulli, binom, poisson, norm

print("Bernoulli:", bernoulli.pmf(1, p=0.7))
print("Binomial:", binom.pmf(3, n=5, p=0.4))
print("Poisson:", poisson.pmf(2, mu=3))
print("Normal CDF:", norm.cdf(1.96))
```

**Code explanation:**

- `bernoulli.pmf(1, p=0.7)` gives the probability of success (`1`) in one yes/no trial where success probability is `0.7`. The answer is `0.7`.
- `binom.pmf(3, n=5, p=0.4)` gives the probability of exactly `3` successes in `5` independent trials when each trial has success probability `0.4`.
- `poisson.pmf(2, mu=3)` gives the probability of exactly `2` events when the average event rate is `3`.
- `norm.cdf(1.96)` gives the probability that a standard normal value is less than or equal to `1.96`. The value is about `0.975`, meaning about `97.5%` of the area is to the left of `1.96`.

In short:

| Code value | Meaning |
|---|---|
| `p` | probability of success in Bernoulli or Binomial distribution |
| `n` | number of trials in Binomial distribution |
| `mu` | average rate or mean in Poisson distribution |
| `1.96` | z-value often used for a two-sided 95% confidence interval |

## 1.8 Sampling and Sampling Distribution { .aws-h2 }

### 1.8.1 Why Sampling Is Needed { .aws-h3 }

Studying the full population is often expensive, slow, or impossible.

Example:

- To estimate the average life of all bulbs produced in a factory, testing every bulb is not practical

### 1.8.2 Sampling Terms { .aws-h3 }

- **Sampling unit**: basic item that can be selected
- **Sampling frame**: full list of units
- **Sampling fraction**: ratio of sample size to population size

**Formula:**

```text
Sampling fraction = n / N
```

### 1.8.3 Simple Random Sampling { .aws-h3 }

In simple random sampling, each unit has an equal chance of selection.

Types:

- with replacement
- without replacement

### 1.8.4 Sampling Error { .aws-h3 }

Sampling error is the difference between a sample statistic and the true population parameter.

**Formula idea:**

```text
Sampling error = Statistic - Parameter
```

**Simple explanation:**

Different samples give slightly different answers.

### 1.8.5 Sampling Distribution { .aws-h3 }

Sampling distribution is the distribution of a statistic over many possible samples.

Important cases:

- sampling distribution of mean
- sampling distribution of proportion

### 1.8.6 Central Limit Theorem (CLT) { .aws-h3 }

For large samples, the sampling distribution of the sample mean becomes approximately normal.

**Formula:**

```text
Mean of sample means = mu
Standard deviation of sample means = sigma / sqrt(n)
```

**Simple explanation:**

Even if raw data is not perfectly normal, sample means from large samples behave normally.

This is true whether the original distribution is left-skewed, right-skewed, or not symmetric, as long as the sample is large enough and the observations are taken properly.

**Why it matters:**

- used in confidence intervals
- used in z-tests
- makes large-sample inference possible

```python
import random

population = list(range(1, 11))
print("without replacement:", random.sample(population, 4))
print("with replacement:", random.choices(population, k=4))
```

## 1.9 Estimation { .aws-h2 }

### 1.9.1 Point Estimation { .aws-h3 }

Point estimate is a single value used to estimate a population parameter.

Examples:

- sample mean estimates population mean
- sample proportion estimates population proportion

**Formula:**

```text
Population mean estimate = x_bar
Population proportion estimate = p_hat = x / n
```

### 1.9.2 Interval Estimation { .aws-h3 }

Interval estimation gives a range of likely values instead of a single value.

### 1.9.3 Confidence Interval { .aws-h3 }

A confidence interval gives a lower bound and upper bound for the parameter.

**General form:**

```text
Confidence Interval = Point Estimate +/- Margin of Error
```

**Mean CI formula using z-value:**

```text
x_bar +/- z(alpha/2) * sigma / sqrt(n)
```

**Proportion CI formula:**

```text
p_hat +/- z(alpha/2) * sqrt[(p_hat * (1-p_hat)) / n]
```

**Standard error vs margin of error:**

| Term | Meaning | Formula idea |
|---|---|---|
| **Standard Error (SE)** | Measures how much a sample statistic varies from sample to sample | `s / sqrt(n)` for a sample mean |
| **Margin of Error (ME)** | Maximum likely distance between the estimate and the true parameter at a chosen confidence level | `critical value * SE` |

Simple difference:

- **Standard error** measures uncertainty due to sampling
- **Margin of error** converts that uncertainty into a confidence interval width using a z-value or t-value

Example:

```text
If SE = 2 and z-value = 1.96:
Margin of Error = 1.96 * 2 = 3.92
```

### 1.9.4 Margin of Error { .aws-h3 }

**Formula:**

```text
Margin of Error = z(alpha/2) * sigma / sqrt(n)
```

**Simple explanation:**

It shows how far the estimate can be from the true value.

Margin of error depends on two things:

- the **standard error**, which comes from sample spread and sample size
- the **critical value**, such as `1.96` for a two-sided 95% confidence interval

**Real-world example:**

- A poll says a candidate has 52% support with a 3% margin of error
- Actual support is likely between 49% and 55%

```python
import numpy as np
from scipy.stats import norm

sample = np.array([49.8, 52.3, 51.0, 56.9, 54.8, 63.0, 58.2, 54.1])
mean = sample.mean()
se = sample.std(ddof=1) / np.sqrt(len(sample))
z = norm.ppf(0.975)
print("95% CI:", (mean - z * se, mean + z * se))
```

## 1.10 Hypothesis Testing Basics { .aws-h2 }

### 1.10.1 What Is a Hypothesis? { .aws-h3 }

A hypothesis is a claim about a population parameter.

### 1.10.2 Null and Alternative Hypothesis { .aws-h3 }

- **Null hypothesis (`H0`)**: default assumption
- **Alternative hypothesis (`H1`)**: what we want to test for

Example:

- `H0`: average delivery time is 60 minutes
- `H1`: average delivery time is not 60 minutes

### 1.10.3 Types of Tests { .aws-h3 }

- **Two-tailed**: checks for any difference
- **Left-tailed**: checks whether the value is smaller
- **Right-tailed**: checks whether the value is larger

### 1.10.4 Test Statistic { .aws-h3 }

A test statistic is a standardized number computed from sample data.

**Simple explanation:**

It tells how far the sample result is from the null hypothesis claim.

### 1.10.5 P-value { .aws-h3 }

P-value is the probability of seeing a result this extreme if `H0` is true.

In simple words:

- it measures how unusual the sample result is under the null hypothesis
- a small p-value means the observed result would be rare if `H0` were true

**Decision rule:**

- if `p-value <= alpha`, reject `H0`
- otherwise fail to reject `H0`

### 1.10.6 Type I and Type II Error { .aws-h3 }

- **Type I error**: reject a true null hypothesis
- **Type II error**: fail to reject a false null hypothesis

**Power of test:**

```text
Power = 1 - beta
```

### 1.10.7 Parametric vs Non-Parametric Tests { .aws-h3 }

- **Parametric tests**: assume a distribution and test parameters like mean or proportion
- **Non-parametric tests**: use fewer assumptions and are often used for categories or non-normal data

## 1.11 Assumption Checks { .aws-h2 }

### 1.11.1 Normality { .aws-h3 }

Some tests assume the data is approximately normal.

**Check using:**

- Shapiro-Wilk test

### 1.11.2 Equal Variance { .aws-h3 }

Some group comparison tests assume equal variances.

**Check using:**

- Levene's test

### 1.11.3 Independence { .aws-h3 }

Observations should not influence one another.

Example:

- marks of one student should not depend on another student's copied answers

```python
from scipy.stats import shapiro, levene

x = [13, 15, 14, 16, 12, 15]
y = [11, 12, 10, 14, 13, 11]
print("Shapiro p-value:", shapiro(x).pvalue)
print("Levene p-value:", levene(x, y).pvalue)
```

## 1.12 Z Tests for Large Samples { .aws-h2 }

### 1.12.1 One-Sample Z Test for Mean { .aws-h3 }

Used to test a population mean against a claimed value.

**Formula:**

```text
z = (x_bar - mu0) / (sigma / sqrt(n))
```

Where:

- `x_bar` = sample mean
- `mu0` = claimed population mean
- `sigma` = population standard deviation
- `n` = sample size

### 1.12.2 Two-Sample Z Test for Means { .aws-h3 }

Used to compare two independent population means.

**Formula:**

```text
z = [(x_bar1 - x_bar2) - d0] / sqrt[(sigma1^2 / n1) + (sigma2^2 / n2)]
```

### 1.12.3 One-Sample Z Test for Proportion { .aws-h3 }

Used to compare a sample proportion with a claimed population proportion.

**Formula:**

```text
z = (p_hat - p0) / sqrt[p0(1-p0)/n]
```

### 1.12.4 Two-Sample Z Test for Proportions { .aws-h3 }

Used to compare two population proportions.

**Formula:**

```text
z = (p_hat1 - p_hat2) / sqrt[p_hat(1-p_hat)(1/n1 + 1/n2)]
```

### 1.12.5 Real-World Examples { .aws-h3 }

- test whether average app response time is still 2 seconds
- compare conversion rates of two landing pages
- test whether defect rate exceeds the allowed limit

```python
from statsmodels.stats.weightstats import ztest
from statsmodels.stats.proportion import proportions_ztest

sample = [24.6, 24.2, 24.4, 24.8, 24.1, 24.3]
print("one-sample z-test:", ztest(sample, value=25))

counts = [78, 65]
obs = [100, 70]
print("two-proportion z-test:", proportions_ztest(counts, obs))
```

## 1.13 T Tests for Small Samples { .aws-h2 }

### 1.13.1 T Distribution { .aws-h3 }

T distribution is used when population variance is unknown and sample size is small.

**Simple explanation:**

It looks like the normal distribution but has heavier tails.

### 1.13.2 One-Sample T Test { .aws-h3 }

Used to compare a sample mean with a claimed population mean.

**Formula:**

```text
t = (x_bar - mu0) / (s / sqrt(n))
```

### 1.13.3 Two-Sample T Test for Unpaired Data { .aws-h3 }

Used to compare means of two independent groups.

**Formula idea:**

```text
t = [(x_bar1 - x_bar2) - d0] / Standard Error
```

### 1.13.4 Paired T Test { .aws-h3 }

Used when the same item or person is measured twice.

Examples:

- before training vs after training
- before medicine vs after medicine

**Formula:**

```text
t = d_bar / (sd / sqrt(n))
```

Where:

- `d_bar` = mean of paired differences
- `sd` = standard deviation of paired differences

```python
from scipy.stats import ttest_1samp, ttest_ind, ttest_rel

before = [8, 9, 7, 10, 6, 9]
after = [9, 10, 7, 11, 7, 10]

print("one-sample t-test:", ttest_1samp(before, popmean=8))
print("two-sample t-test:", ttest_ind(before, after, equal_var=True))
print("paired t-test:", ttest_rel(before, after))
```

## 1.14 Chi-Square Tests for Categorical Data { .aws-h2 }

### 1.14.1 Chi-Square Distribution { .aws-h3 }

Chi-square distribution is used in tests involving categorical frequency data.

### 1.14.2 Chi-Square Goodness-of-Fit Test { .aws-h3 }

Used to check whether observed frequencies match expected frequencies.

**Formula:**

```text
chi^2 = Sum[(Oi - Ei)^2 / Ei]
```

Where:

- `Oi` = observed frequency
- `Ei` = expected frequency

Example:

- test whether customer age groups match a claimed market distribution

### 1.14.3 Chi-Square Test of Independence { .aws-h3 }

Used to test whether two categorical variables are related.

Example:

- is customer satisfaction related to subscription plan
- is disease outcome related to blood group

**Expected frequency formula:**

```text
Eij = (Row Total * Column Total) / Grand Total
```

### 1.14.4 Minimum Expected Frequency Rule { .aws-h3 }

Expected frequencies should usually be at least 5 for reliable chi-square results.

```python
import numpy as np
from scipy.stats import chisquare, chi2_contingency

observed = np.array([42, 28, 20, 10])
expected = np.array([40, 30, 20, 10])
print("goodness-of-fit:", chisquare(observed, f_exp=expected))

table = np.array([[40, 20], [30, 35]])
print("independence:", chi2_contingency(table)[:2])
```

## 1.15 Analysis of Variance (ANOVA) { .aws-h2 }

### 1.15.1 Why ANOVA Is Needed { .aws-h3 }

ANOVA is used to compare the means of 3 or more groups.

Why not many t-tests?

- many t-tests increase the chance of Type I error

### 1.15.2 One-Way ANOVA { .aws-h3 }

Used when one categorical factor affects one numerical variable.

Example:

- compare average sales across 4 regions
- compare machine performance across 3 machines

**Hypothesis:**

- `H0`: all group means are equal
- `H1`: at least one group mean is different

### 1.15.3 ANOVA Variations { .aws-h3 }

- **Total variation**
- **Between-group variation**
- **Within-group variation**

**Relationship:**

```text
Total Variation = Between Variation + Within Variation
```

### 1.15.4 F Statistic { .aws-h3 }

**Formula:**

```text
F = Mean Square Between / Mean Square Within
```

**Simple explanation:**

If variation between groups is much larger than variation within groups, group means are likely not equal.

### 1.15.5 One-Way ANOVA Assumptions { .aws-h3 }

- groups are independent
- data in each group is approximately normal
- variances are approximately equal

### 1.15.6 Post-Hoc Tests { .aws-h3 }

If ANOVA rejects `H0`, post-hoc tests show which groups are different.

Common post-hoc tests:

- Tukey HSD
- Scheffe test

### 1.15.7 Two-Way ANOVA { .aws-h3 }

Two-way ANOVA studies the effect of two categorical factors on one numerical outcome.

Example:

- machine type and work shift affecting production output

```python
from scipy.stats import f_oneway

machine_a = [68.7, 75.4, 70.9]
machine_b = [62.7, 68.5, 63.1]
machine_c = [55.9, 56.1, 57.3]
machine_d = [80.7, 70.3, 80.9]

print("one-way ANOVA:", f_oneway(machine_a, machine_b, machine_c, machine_d))
```

```python
import pandas as pd
from statsmodels.stats.multicomp import pairwise_tukeyhsd

df = pd.DataFrame({
    "strength": machine_a + machine_b + machine_c + machine_d,
    "machine": (["A"] * 3) + (["B"] * 3) + (["C"] * 3) + (["D"] * 3),
})
print(pairwise_tukeyhsd(endog=df["strength"], groups=df["machine"], alpha=0.05))
```

## 1.16 Covariance, Correlation, and Regression { .aws-h2 }

### 1.16.1 Covariance { .aws-h3 }

Covariance shows whether two variables move together.

**Formula:**

```text
Cov(X,Y) = Sum[(Xi - X_bar)(Yi - Y_bar)] / (n - 1)
```

**Simple explanation:**

- positive covariance: both move together
- negative covariance: one rises while the other falls

### 1.16.2 Correlation { .aws-h3 }

Correlation gives the strength and direction of linear relationship.

**Formula:**

```text
r = Cov(X,Y) / (Sx * Sy)
```

**Range:**

```text
-1 <= r <= 1
```

**Simple explanation:**

- near `1`: strong positive relationship
- near `-1`: strong negative relationship
- near `0`: weak linear relationship

**Real-world example:**

- study hours and marks often show positive correlation

### 1.16.3 Linear Regression { .aws-h3 }

Regression models the relationship between a target and predictor variables.

**Simple linear regression formula:**

```text
Y = beta0 + beta1X + error
```

Where:

- `beta0` = intercept
- `beta1` = slope

**Simple explanation:**

Regression helps predict a value and measure how one variable changes with another.

### 1.16.4 R-Squared { .aws-h3 }

R-squared tells how much of the variation in `Y` is explained by the model.

**Formula:**

```text
R^2 = Explained Variation / Total Variation
```

**Real-world example:**

- predict house price using area
- predict sales using advertising spend

```python
import numpy as np
from scipy.stats import pearsonr
from sklearn.linear_model import LinearRegression

X = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)
y = np.array([2, 4, 5, 4, 6])
print("correlation:", pearsonr(X.ravel(), y))

model = LinearRegression().fit(X, y)
print("slope:", model.coef_[0], "intercept:", model.intercept_, "r2:", model.score(X, y))
```

## 1.17 When to Use What { .aws-h2 }

| Need | Method |
|---|---|
| Summarize data | Descriptive statistics |
| Model success/failure in one trial | Bernoulli |
| Count successes in fixed trials | Binomial |
| Count events in a time interval | Poisson |
| Model bell-shaped continuous data | Normal |
| Estimate unknown population value | Point estimate / confidence interval |
| Compare sample mean to claimed mean | One-sample z-test or t-test |
| Compare two means | Two-sample z-test or t-test |
| Compare before and after values | Paired t-test |
| Check fit of observed frequencies | Chi-square goodness-of-fit |
| Check relationship between categories | Chi-square independence |
| Compare 3 or more group means | ANOVA |
| Study relation between two variables | Correlation / regression |

## 1.18 Common Python Functions in Statistics { .aws-h2 }

| Topic | Common Python Function |
|---|---|
| Mean / variance / std | `numpy.mean()`, `numpy.var()`, `numpy.std()` |
| Percentiles | `numpy.percentile()` |
| Mode | `scipy.stats.mode()` |
| Binomial distribution | `scipy.stats.binom.pmf()`, `binom.cdf()` |
| Poisson distribution | `scipy.stats.poisson.pmf()` |
| Normal distribution | `scipy.stats.norm.cdf()`, `norm.sf()` |
| Random sampling | `random.sample()`, `random.choices()` |
| One-sample z-test | `statsmodels.stats.weightstats.ztest()` |
| Proportion z-test | `statsmodels.stats.proportion.proportions_ztest()` |
| One-sample t-test | `scipy.stats.ttest_1samp()` |
| Two-sample t-test | `scipy.stats.ttest_ind()` |
| Paired t-test | `scipy.stats.ttest_rel()` |
| Shapiro-Wilk test | `scipy.stats.shapiro()` |
| Levene's test | `scipy.stats.levene()` |
| Chi-square goodness of fit | `scipy.stats.chisquare()` |
| Chi-square independence | `scipy.stats.chi2_contingency()` |
| One-way ANOVA | `scipy.stats.f_oneway()` |
| Tukey HSD | `statsmodels.stats.multicomp.pairwise_tukeyhsd()` |
| Correlation | `scipy.stats.pearsonr()` |
| Regression | `sklearn.linear_model.LinearRegression()` |

## 1.19 Core Statistical Ideas { .aws-h2 }

- mean, median, and mode describe the center of data
- variance and standard deviation describe spread
- quartiles and percentiles describe position
- random variables can be discrete or continuous
- binomial, Poisson, and normal are the most common basic distributions
- sampling is used because full population study is often impractical
- confidence intervals give a likely range for a parameter
- p-value is used to decide whether to reject `H0`
- z-test is common for large samples
- t-test is common when variance is unknown and sample size is small
- chi-square is used for categorical frequency data
- ANOVA compares means across more than two groups
- correlation measures relationship, regression helps prediction

## 1.20 Statistical Workflow { .aws-h2 }

Statistics starts with understanding data and ends with making decisions from data.

The overall flow is usually:

1. describe the data
2. understand randomness using probability distributions
3. take samples and estimate unknown values
4. test claims using z, t, chi-square, or ANOVA
5. study relationships using correlation and regression

For data science and analytics roles, the most important topics to know strongly are:

- descriptive statistics
- probability distributions
- sampling and CLT
- confidence intervals
- hypothesis testing
- z-tests and t-tests
- chi-square tests
- ANOVA
- correlation and regression
