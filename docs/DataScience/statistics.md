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
- **Harmonic mean**: useful for averaging rates and ratios
- **Geometric mean**: useful for averaging growth rates and multiplicative changes
- **Median**: middle value
- **Mode**: most frequent value

#### Arithmetic Mean

**Definition:**

Arithmetic mean is the usual average of all values.

**Formula:**

```text
Arithmetic Mean = Sum of all values / Number of values
x_bar = (x1 + x2 + ... + xn) / n
```

**Simple explanation:**

Add everything and divide by how many values you have.

**Example:**

Marks = 60, 70, 80

Arithmetic Mean = `(60 + 70 + 80) / 3 = 70`

**Real-world use:**

- average monthly sales
- average student marks
- average temperature

#### Harmonic Mean

**Definition:**

Harmonic mean is a type of average mainly used when the values are **rates**, **ratios**, or values measured per unit.

**Formula:**

```text
Harmonic Mean = n / [(1 / x1) + (1 / x2) + ... + (1 / xn)]
```

**Simple explanation:**

First take the reciprocal of each value, average those reciprocals, and then take the reciprocal again.

**Example:**

Speeds = 40 km/h and 60 km/h

```text
Harmonic Mean = 2 / [(1 / 40) + (1 / 60)]
              = 48 km/h
```

**Real-world use:**

- average speed over equal distances
- average price-to-earnings ratios
- average rates such as tasks per hour or units per minute

#### Geometric Mean

**Definition:**

Geometric mean is a type of average used when values are multiplied together or represent growth over time.

**Formula:**

```text
Geometric Mean = nth root of (x1 * x2 * ... * xn)
```

For two values:

```text
Geometric Mean = sqrt(x1 * x2)
```

**Simple explanation:**

Multiply all values together and take the root based on how many values are present.

**Example:**

Growth rates = 10%, 20%, and 30%

Convert them into growth factors:

```text
1.10, 1.20, 1.30
```

```text
Geometric Mean = cube root of (1.10 * 1.20 * 1.30)
               = 1.197
```

Average growth rate is approximately `19.7%`.

**Real-world use:**

- compound annual growth rate
- investment returns
- population growth
- percentage growth over multiple periods

#### Arithmetic Mean vs Harmonic Mean vs Geometric Mean

| Mean type | Best used for | Formula idea | Example use |
|---|---|---|---|
| Arithmetic mean | Normal values that are added together | Add values and divide by count | average marks, average sales |
| Harmonic mean | Rates and ratios | Average the reciprocals | average speed over equal distances |
| Geometric mean | Growth and multiplicative change | Multiply values and take nth root | average investment growth |

Important note:

- Arithmetic mean is most common
- Harmonic mean gives more weight to smaller values
- Geometric mean is better when values compound over time

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

#### Moving Average

**Definition:**

Moving average is an average calculated over a fixed number of recent values.

It is mainly used with time-based data to smooth short-term ups and downs.

**Formula idea:**

```text
Moving Average = Average of last k values
```

Here, `k` is the window size.

**Example:**

Daily sales:

```text
10, 12, 15, 14, 18
```

3-day moving averages:

```text
(10 + 12 + 15) / 3 = 12.33
(12 + 15 + 14) / 3 = 13.67
(15 + 14 + 18) / 3 = 15.67
```

**Real-world use:**

- smooth daily sales trends
- track stock prices
- understand website traffic patterns
- reduce noise in time series data

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

#### Coefficient of Variation

**Definition:**

Coefficient of Variation, also called **CV**, measures spread relative to the mean.

It is useful when comparing variability between datasets that have different units or very different average values.

**Formula:**

```text
CV = (Standard Deviation / Mean) * 100
CV = (s / x_bar) * 100
```

**Simple explanation:**

Standard deviation tells spread in the original unit, but coefficient of variation tells spread as a percentage of the mean.

Example:

```text
Dataset A: mean = 100, standard deviation = 10
CV = (10 / 100) * 100 = 10%

Dataset B: mean = 20, standard deviation = 5
CV = (5 / 20) * 100 = 25%
```

Even though Dataset B has a smaller standard deviation, it has higher relative variation.

**Real-world use:**

- compare risk of two investments with different average returns
- compare consistency of two machines with different average outputs
- compare variation in salaries across departments with different average salaries

**Important note:**

Coefficient of Variation is meaningful only when the mean is positive and not close to zero.

```python
import numpy as np

values = np.array([10, 12, 15, 15, 18, 20, 24])

mean = values.mean()
std = values.std(ddof=1)
cv = (std / mean) * 100

print("mean:", mean)
print("std:", std)
print("coefficient of variation:", cv)
```

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
print("cv:", (values.std(ddof=1) / values.mean()) * 100)
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

Statistical tests can be broadly grouped into **parametric** and **non-parametric** tests.

**Parametric tests** assume that the data follows a specific probability distribution, usually a normal distribution. These tests make assumptions about population parameters such as mean, variance, or proportion. They are powerful when their assumptions are satisfied.

Use parametric tests when:

- data is numerical and approximately normally distributed
- sample size is reasonably large, or normality is satisfied
- observations are independent
- variance assumptions are satisfied where required

Common parametric tests:

- **Z-test**: compares a sample mean or proportion with a known population value when population standard deviation is known or sample size is large
- **One-sample t-test**: compares one sample mean with a known or hypothesized mean
- **Independent two-sample t-test**: compares means of two independent groups
- **Paired t-test**: compares means of the same group measured twice, such as before and after treatment
- **ANOVA**: compares means across three or more groups
- **Pearson correlation**: measures linear relationship between two continuous variables
- **Linear regression**: models relationship between a continuous dependent variable and one or more independent variables

**Non-parametric tests** do not require the data to follow a specific distribution. They are often used when data is ordinal, skewed, has outliers, has a small sample size, or does not satisfy normality assumptions. These tests commonly work with ranks, medians, or frequencies instead of directly comparing means.

Use non-parametric tests when:

- data is ordinal or ranked
- data is not normally distributed
- sample size is small and normality is doubtful
- data contains strong outliers
- assumptions of parametric tests are violated

Common non-parametric tests:

- **Mann-Whitney U test**: compares two independent groups when data is not normally distributed
- **Wilcoxon signed-rank test**: compares two paired samples when normality is not satisfied
- **Kruskal-Wallis test**: compares three or more independent groups using ranks
- **Friedman test**: compares three or more related or repeated-measure groups
- **Chi-square test**: checks association between categorical variables
- **Fisher's exact test**: checks association between categorical variables, especially with small sample sizes
- **Spearman rank correlation**: measures monotonic relationship between two variables using ranks

Simple rule:

- If assumptions like normality and equal variance are satisfied, prefer a **parametric test**
- If assumptions are not satisfied, or data is ordinal/ranked/categorical, prefer a **non-parametric test**

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

alpha = 0.05

shapiro_p = shapiro(x).pvalue
levene_p = levene(x, y).pvalue

print("Shapiro p-value:", shapiro_p)
print("Levene p-value:", levene_p)

if shapiro_p > alpha:
    print("Data is approximately normal")
else:
    print("Data is not normally distributed")

if levene_p > alpha:
    print("Variances are equal")
else:
    print("Variances are not equal")
```

Interpretation:

- For **Shapiro-Wilk test**, if `p-value > 0.05`, data is approximately normal. If `p-value <= 0.05`, data is not normally distributed.
- For **Levene's test**, if `p-value > 0.05`, group variances are approximately equal. If `p-value <= 0.05`, group variances are not equal.

## 1.12 Z Tests for Large Samples { .aws-h2 }

Z tests are used when the sampling distribution is approximately normal and the standard error is known or can be reliably estimated. They are common for **large samples**, **known population standard deviation**, and **proportion tests**.

### 1.12.1 When to Use Z Test { .aws-h3 }

Use a z test when:

- sample size is large, usually `n >= 30`
- data is numerical and population standard deviation `sigma` is known
- or the test is about population proportion, such as conversion rate, pass rate, or defect rate
- observations are independent
- sampling distribution is approximately normal

For proportion z tests, normal approximation is usually acceptable when:

```text
np >= 5 and n(1-p) >= 5
```

### 1.12.2 How Decision is Made { .aws-h3 }

Steps:

1. Write null hypothesis `H0` and alternative hypothesis `H1`
2. Choose significance level, commonly `alpha = 0.05`
3. Calculate z statistic using the formula
4. Calculate p-value from the z statistic
5. Compare p-value with alpha

Decision rule:

- If `p-value <= alpha`, reject `H0`
- If `p-value > alpha`, fail to reject `H0`

Meaning:

- **Reject `H0`** means there is enough evidence against the claim
- **Fail to reject `H0`** means there is not enough evidence against the claim

### 1.12.3 One-Sample Z Test for Mean { .aws-h3 }

Used to test whether a population mean is different from a claimed value when population standard deviation is known or sample size is large.

Example:

A company claims average delivery time is `30` minutes. A sample of `36` deliveries has mean `32` minutes. Population standard deviation is known as `6` minutes.

**Formula:**

```text
z = (x_bar - mu0) / (sigma / sqrt(n))
```

Where:

- `x_bar` = sample mean
- `mu0` = claimed population mean
- `sigma` = population standard deviation
- `n` = sample size

Apply formula:

```text
z = (32 - 30) / (6 / sqrt(36))
z = 2 / 1
z = 2.0
```

Python:

```python
from math import sqrt
from scipy.stats import norm

x_bar = 32
mu0 = 30
sigma = 6
n = 36
alpha = 0.05

z = (x_bar - mu0) / (sigma / sqrt(n))
p_value = 2 * (1 - norm.cdf(abs(z)))  # two-tailed test

print("z statistic:", z)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: average delivery time is significantly different from 30")
else:
    print("Fail to reject H0: not enough evidence that average delivery time is different from 30")
```

### 1.12.4 Two-Sample Z Test for Means { .aws-h3 }

Used to compare means of two independent groups when population standard deviations are known or both sample sizes are large.

**Formula:**

```text
z = [(x_bar1 - x_bar2) - d0] / sqrt[(sigma1^2 / n1) + (sigma2^2 / n2)]
```

Where:

- `x_bar1`, `x_bar2` = sample means
- `sigma1`, `sigma2` = population standard deviations
- `n1`, `n2` = sample sizes
- `d0` = claimed difference, usually `0`

Python:

```python
from math import sqrt
from scipy.stats import norm

x_bar1 = 82
x_bar2 = 78
sigma1 = 10
sigma2 = 12
n1 = 50
n2 = 45
d0 = 0
alpha = 0.05

se = sqrt((sigma1**2 / n1) + (sigma2**2 / n2))
z = ((x_bar1 - x_bar2) - d0) / se
p_value = 2 * (1 - norm.cdf(abs(z)))

print("z statistic:", z)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: group means are significantly different")
else:
    print("Fail to reject H0: not enough evidence of difference between group means")
```

### 1.12.5 One-Sample Z Test for Proportion { .aws-h3 }

Used to compare a sample proportion with a claimed population proportion.

A proportion is a fraction or percentage of observations with a particular outcome.

Examples:

- percentage of users who clicked an ad
- proportion of students who passed an exam
- defect rate in manufactured items
- conversion rate of a landing page

Example:

A website claims its conversion rate is `50%`. Out of `100` users, `60` converted. Test whether the conversion rate is different from `50%`.

**Formula:**

```text
z = (p_hat - p0) / sqrt[p0(1-p0)/n]
```

Where:

- `p_hat = x / n` = sample proportion
- `x` = number of successes
- `n` = sample size
- `p0` = claimed population proportion

Apply formula:

```text
p_hat = 60 / 100 = 0.60
z = (0.60 - 0.50) / sqrt[0.50(1 - 0.50) / 100]
z = 0.10 / 0.05
z = 2.0
```

Python:

```python
from statsmodels.stats.proportion import proportions_ztest

successes = 60
n = 100
p0 = 0.50
alpha = 0.05

z_stat, p_value = proportions_ztest(count=successes, nobs=n, value=p0)

print("z statistic:", z_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: conversion rate is significantly different from 50%")
else:
    print("Fail to reject H0: not enough evidence that conversion rate is different from 50%")
```

### 1.12.6 Two-Sample Z Test for Proportions { .aws-h3 }

Used to compare two population proportions.

Example:

Landing Page A converted `78` out of `100` users. Landing Page B converted `65` out of `100` users. Test whether conversion rates are different.

**Formula:**

```text
z = (p_hat1 - p_hat2) / sqrt[p_hat(1-p_hat)(1/n1 + 1/n2)]
```

Where:

- `p_hat1 = x1 / n1`
- `p_hat2 = x2 / n2`
- `p_hat = (x1 + x2) / (n1 + n2)` = pooled proportion

Python:

```python
from statsmodels.stats.proportion import proportions_ztest

counts = [78, 65]
observations = [100, 100]
alpha = 0.05

z_stat, p_value = proportions_ztest(count=counts, nobs=observations)

print("z statistic:", z_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: conversion rates are significantly different")
else:
    print("Fail to reject H0: not enough evidence that conversion rates are different")
```

### 1.12.7 Real-World Examples { .aws-h3 }

- test whether average app response time is still 2 seconds
- compare conversion rates of two landing pages
- test whether defect rate exceeds the allowed limit

### 1.12.8 Z Test vs Proportion Z Test { .aws-h3 }

| Test | Used for | Data type | Example |
|---|---|---|---|
| Z test for mean | Compare average value | Numerical data | average salary, average delivery time |
| Z test for proportion | Compare percentage or rate | Binary/categorical outcome | pass/fail, converted/not converted, defective/not defective |

Main difference:

- Z test for mean works with sample mean `x_bar`
- Proportion z test works with sample proportion `p_hat`

### 1.12.9 Z Test vs T Test { .aws-h3 }

| Z Test | T Test |
|---|---|
| Used mostly for large samples | Used mostly for small samples |
| Population standard deviation `sigma` is known | Population standard deviation is unknown |
| Uses normal distribution | Uses t distribution |
| Common for proportion tests | Common for mean tests with sample standard deviation |

Simple rule:

- Use **z test** when `sigma` is known or sample size is large
- Use **t test** when `sigma` is unknown and sample size is small

```python
from statsmodels.stats.weightstats import ztest
from statsmodels.stats.proportion import proportions_ztest

sample = [24.6, 24.2, 24.4, 24.8, 24.1, 24.3] * 6
alpha = 0.05

z_stat, p_value = ztest(sample, value=25)
print("one-sample z-test:", z_stat, p_value)

if p_value <= alpha:
    print("Reject H0")
else:
    print("Fail to reject H0")

counts = [78, 65]
obs = [100, 70]
z_stat, p_value = proportions_ztest(counts, obs)
print("two-proportion z-test:", z_stat, p_value)
```

## 1.13 T Tests for Small Samples { .aws-h2 }

T tests are used to test hypotheses about means when the population standard deviation is unknown. They are especially useful for small samples.

### 1.13.1 T Distribution { .aws-h3 }

T distribution is used when population variance is unknown and sample size is small.

**Simple explanation:**

It looks like the normal distribution but has heavier tails.

### 1.13.2 When to Use T Test { .aws-h3 }

Use a t test when:

- data is numerical
- population standard deviation `sigma` is unknown
- sample size is small, usually `n < 30`
- data is approximately normally distributed
- observations are independent

For large samples, t test is also commonly used when population standard deviation is unknown because it becomes close to the z test.

### 1.13.3 How Decision is Made { .aws-h3 }

Steps:

1. Write null hypothesis `H0` and alternative hypothesis `H1`
2. Choose significance level, commonly `alpha = 0.05`
3. Calculate t statistic using the formula
4. Calculate p-value using t distribution and degrees of freedom
5. Compare p-value with alpha

Decision rule:

- If `p-value <= alpha`, reject `H0`
- If `p-value > alpha`, fail to reject `H0`

Meaning:

- **Reject `H0`** means there is enough evidence of a significant difference
- **Fail to reject `H0`** means the sample does not provide enough evidence of a significant difference

### 1.13.4 One-Sample T Test { .aws-h3 }

Used to compare a sample mean with a claimed population mean.

Example:

A teacher claims the average score is `8`. A small sample of students has scores `[8, 9, 7, 10, 6, 9]`. Test whether the average score is different from `8`.

**Formula:**

```text
t = (x_bar - mu0) / (s / sqrt(n))
```

Where:

- `x_bar` = sample mean
- `mu0` = claimed population mean
- `s` = sample standard deviation
- `n` = sample size
- degrees of freedom = `n - 1`

Python:

```python
from scipy.stats import ttest_1samp

scores = [8, 9, 7, 10, 6, 9]
alpha = 0.05

t_stat, p_value = ttest_1samp(scores, popmean=8)

print("t statistic:", t_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: average score is significantly different from 8")
else:
    print("Fail to reject H0: not enough evidence that average score is different from 8")
```

### 1.13.5 Two-Sample T Test for Unpaired Data { .aws-h3 }

Used to compare means of two independent groups.

Example:

Compare exam scores of two different groups of students.

**Formula idea:**

```text
t = [(x_bar1 - x_bar2) - d0] / Standard Error
```

Types:

- **Student's independent t-test**: use when variances are approximately equal
- **Welch's t-test**: use when variances are not equal

Python:

```python
from scipy.stats import ttest_ind

group_a = [8, 9, 7, 10, 6, 9]
group_b = [6, 7, 8, 7, 5, 6]
alpha = 0.05

t_stat, p_value = ttest_ind(group_a, group_b, equal_var=True)

print("t statistic:", t_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: group means are significantly different")
else:
    print("Fail to reject H0: not enough evidence that group means are different")
```

If Levene's test shows unequal variances, use Welch's t-test:

```python
t_stat, p_value = ttest_ind(group_a, group_b, equal_var=False)
```

### 1.13.6 Paired T Test { .aws-h3 }

Used when the same item or person is measured twice.

Examples:

- before training vs after training
- before medicine vs after medicine
- same users before and after a product change

**Formula:**

```text
t = d_bar / (sd / sqrt(n))
```

Where:

- `d_bar` = mean of paired differences
- `sd` = standard deviation of paired differences
- `n` = number of pairs

Python:

```python
from scipy.stats import ttest_rel

before = [8, 9, 7, 10, 6, 9]
after = [9, 10, 7, 11, 7, 10]
alpha = 0.05

t_stat, p_value = ttest_rel(before, after)

print("t statistic:", t_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: before and after values are significantly different")
else:
    print("Fail to reject H0: not enough evidence of difference between before and after")
```

### 1.13.7 Difference Between One-Sample, Two-Sample, and Paired T Tests { .aws-h3 }

| Test | Used when | Example |
|---|---|---|
| One-sample t-test | Compare one sample mean with a claimed mean | average score vs claimed score |
| Two-sample t-test | Compare means of two independent groups | class A vs class B |
| Paired t-test | Compare two measurements from the same subjects | before vs after training |

### 1.13.8 Z Test vs T Test Summary { .aws-h3 }

| Situation | Use |
|---|---|
| Population standard deviation is known | Z test |
| Population standard deviation is unknown | T test |
| Sample size is small and data is numerical | T test |
| Testing proportions such as conversion rate or pass rate | Z test for proportion |
| Comparing means of two small independent samples | Two-sample t-test |
| Comparing before and after values for same people/items | Paired t-test |

```python
from scipy.stats import ttest_1samp, ttest_ind, ttest_rel

before = [8, 9, 7, 10, 6, 9]
after = [9, 10, 7, 11, 7, 10]
alpha = 0.05

t_stat, p_value = ttest_1samp(before, popmean=8)
print("one-sample t-test:", t_stat, p_value)

if p_value <= alpha:
    print("Reject H0")
else:
    print("Fail to reject H0")

t_stat, p_value = ttest_ind(before, after, equal_var=True)
print("two-sample t-test:", t_stat, p_value)

t_stat, p_value = ttest_rel(before, after)
print("paired t-test:", t_stat, p_value)
```

## 1.14 Chi-Square Tests for Categorical Data { .aws-h2 }

Chi-square tests are used for **categorical data** and **frequency counts**.

They answer questions like:

- Does the observed distribution match an expected distribution?
- Are two categorical variables related?
- Are two categorical variables independent?

Important point:

- Chi-square tests work with **counts**, not means
- They are used for categories like male/female, pass/fail, plan type, blood group, region, satisfaction level

### 1.14.1 Chi-Square Distribution { .aws-h3 }

Chi-square distribution is used in tests involving categorical frequency data.

Properties:

- values are always non-negative
- shape depends on degrees of freedom
- commonly used to compare observed counts with expected counts

The chi-square statistic becomes large when observed counts are very different from expected counts.

### 1.14.2 When to Use Chi-Square Test { .aws-h3 }

Use chi-square test when:

- data is categorical
- data is in frequency/count form
- observations are independent
- expected frequency in each cell is usually at least 5

Do not use chi-square test directly for:

- continuous numerical data like salary, age, height, marks
- percentages without actual counts
- dependent/repeated observations

### 1.14.3 Chi-Square Goodness-of-Fit Test { .aws-h3 }

Used to check whether observed frequencies match expected frequencies.

It is used for **one categorical variable**.

Example question:

- Are customers equally distributed across four age groups?
- Does actual product preference match expected market share?

Hypothesis:

- `H0`: observed distribution matches expected distribution
- `H1`: observed distribution does not match expected distribution

**Formula:**

```text
chi^2 = Sum[(Oi - Ei)^2 / Ei]
```

Where:

- `Oi` = observed frequency
- `Ei` = expected frequency

Example:

- A company expects customers to be distributed as `[40, 30, 20, 10]` across four age groups
- Actual observed customers are `[42, 28, 20, 10]`

Apply formula idea:

```text
chi^2 = ((42-40)^2/40) + ((28-30)^2/30) + ((20-20)^2/20) + ((10-10)^2/10)
```

Python:

```python
import numpy as np
from scipy.stats import chisquare

observed = np.array([42, 28, 20, 10])
expected = np.array([40, 30, 20, 10])
alpha = 0.05

chi2_stat, p_value = chisquare(observed, f_exp=expected)

print("chi-square statistic:", chi2_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: observed distribution is significantly different from expected distribution")
else:
    print("Fail to reject H0: observed distribution is not significantly different from expected distribution")
```

### 1.14.4 Chi-Square Test of Independence { .aws-h3 }

Used to test whether two categorical variables are related.

It is used for **two categorical variables** arranged in a contingency table.

Example:

- is customer satisfaction related to subscription plan
- is disease outcome related to blood group

Hypothesis:

- `H0`: the two categorical variables are independent
- `H1`: the two categorical variables are related

**Expected frequency formula:**

```text
Eij = (Row Total * Column Total) / Grand Total
```

Example contingency table:

| Plan | Satisfied | Not Satisfied |
|---|---:|---:|
| Basic | 40 | 20 |
| Premium | 30 | 35 |

Question:

- Is satisfaction related to subscription plan?

Python:

```python
import numpy as np
from scipy.stats import chi2_contingency

table = np.array([
    [40, 20],
    [30, 35]
])
alpha = 0.05

chi2_stat, p_value, dof, expected = chi2_contingency(table)

print("chi-square statistic:", chi2_stat)
print("p-value:", p_value)
print("degrees of freedom:", dof)
print("expected frequencies:")
print(expected)

if p_value <= alpha:
    print("Reject H0: subscription plan and satisfaction are related")
else:
    print("Fail to reject H0: not enough evidence that subscription plan and satisfaction are related")
```

Interpretation:

- If p-value is small, the variables are likely related
- If p-value is large, there is not enough evidence of a relationship

### 1.14.5 Degrees of Freedom { .aws-h3 }

Degrees of freedom depend on the type of chi-square test.

For goodness-of-fit:

```text
df = number of categories - 1
```

For test of independence:

```text
df = (number of rows - 1) * (number of columns - 1)
```

Example:

For a `2 x 2` table:

```text
df = (2 - 1) * (2 - 1) = 1
```

### 1.14.6 How Decision is Made { .aws-h3 }

Steps:

1. Write `H0` and `H1`
2. Choose significance level, usually `alpha = 0.05`
3. Calculate expected frequencies
4. Calculate chi-square statistic
5. Calculate p-value
6. Compare p-value with alpha

Decision rule:

- If `p-value <= alpha`, reject `H0`
- If `p-value > alpha`, fail to reject `H0`

Meaning:

- In goodness-of-fit, rejecting `H0` means observed counts do not match expected counts
- In independence test, rejecting `H0` means the two categorical variables are related

### 1.14.7 Minimum Expected Frequency Rule { .aws-h3 }

Expected frequencies should usually be at least 5 for reliable chi-square results.

Why this matters:

- Chi-square test uses an approximation
- Very small expected counts can make the p-value unreliable

If expected counts are too small:

- combine similar categories if it makes business sense
- use Fisher's exact test for small `2 x 2` tables
- collect more data if possible

### 1.14.8 Goodness-of-Fit vs Independence Test { .aws-h3 }

| Test | Number of categorical variables | Purpose | Example |
|---|---:|---|---|
| Chi-square goodness-of-fit | 1 | Compare observed distribution with expected distribution | actual age-group distribution vs expected age-group distribution |
| Chi-square test of independence | 2 | Check whether two categorical variables are related | subscription plan vs satisfaction |

Simple difference:

- **Goodness-of-fit** checks whether one categorical variable follows an expected pattern
- **Independence test** checks whether two categorical variables are associated

```python
import numpy as np
from scipy.stats import chisquare, chi2_contingency

observed = np.array([42, 28, 20, 10])
expected = np.array([40, 30, 20, 10])
alpha = 0.05

chi2_stat, p_value = chisquare(observed, f_exp=expected)
print("goodness-of-fit:", chi2_stat, p_value)

if p_value <= alpha:
    print("Reject H0")
else:
    print("Fail to reject H0")

table = np.array([[40, 20], [30, 35]])
chi2_stat, p_value, dof, expected = chi2_contingency(table)
print("independence:", chi2_stat, p_value)
print("degrees of freedom:", dof)
print("expected frequencies:")
print(expected)
```

## 1.15 Analysis of Variance (ANOVA) { .aws-h2 }

### 1.15.1 Why ANOVA Is Needed { .aws-h3 }

ANOVA is used to compare the means of 3 or more groups.

Why not many t-tests?

- many t-tests increase the chance of Type I error

### 1.15.2 One-Way ANOVA { .aws-h3 }

Used when **one categorical factor** affects **one numerical variable**.

Use case:

- You want to compare the average value across three or more groups
- There is only one grouping variable

Example:

- compare average sales across 4 regions
- compare machine performance across 3 machines
- compare average exam score across 3 teaching methods

**Hypothesis:**

- `H0`: all group means are equal
- `H1`: at least one group mean is different

Decision rule:

- If `p-value <= 0.05`, reject `H0`
- If `p-value > 0.05`, fail to reject `H0`

Python:

```python
from scipy.stats import f_oneway

machine_a = [68.7, 75.4, 70.9]
machine_b = [62.7, 68.5, 63.1]
machine_c = [55.9, 56.1, 57.3]
machine_d = [80.7, 70.3, 80.9]
alpha = 0.05

f_stat, p_value = f_oneway(machine_a, machine_b, machine_c, machine_d)

print("F statistic:", f_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: at least one machine has a different average performance")
else:
    print("Fail to reject H0: machine averages are not significantly different")
```

Explanation:

- Here, **machine type** is the categorical factor
- **performance/strength** is the numerical outcome
- ANOVA checks whether all machine means are equal or at least one machine mean is different

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

Example using Tukey HSD after one-way ANOVA:

```python
import pandas as pd
from statsmodels.stats.multicomp import pairwise_tukeyhsd

machine_a = [68.7, 75.4, 70.9]
machine_b = [62.7, 68.5, 63.1]
machine_c = [55.9, 56.1, 57.3]
machine_d = [80.7, 70.3, 80.9]

df = pd.DataFrame({
    "strength": machine_a + machine_b + machine_c + machine_d,
    "machine": (["A"] * 3) + (["B"] * 3) + (["C"] * 3) + (["D"] * 3),
})

print(pairwise_tukeyhsd(endog=df["strength"], groups=df["machine"], alpha=0.05))
```

Use this after ANOVA rejects `H0`, because ANOVA tells that at least one group is different, but Tukey HSD tells which specific groups are different.

### 1.15.7 Two-Way ANOVA { .aws-h3 }

Two-way ANOVA studies the effect of two categorical factors on one numerical outcome.

Use case:

- You want to study the effect of two factors at the same time
- You also want to check whether the combination of both factors creates an interaction effect

Example:

- machine type and work shift affecting production output
- teaching method and gender affecting exam score
- diet type and exercise plan affecting weight loss

Two-way ANOVA can answer three questions:

- Does factor 1 affect the outcome?
- Does factor 2 affect the outcome?
- Do factor 1 and factor 2 interact with each other?

Example scenario:

- machine type and work shift affecting production output

```python
import pandas as pd
import statsmodels.api as sm
from statsmodels.formula.api import ols

df = pd.DataFrame({
    "output": [68, 70, 72, 75, 77, 78, 60, 62, 64, 66, 67, 69],
    "machine": ["A", "A", "A", "A", "A", "A", "B", "B", "B", "B", "B", "B"],
    "shift": ["Morning", "Morning", "Morning", "Night", "Night", "Night",
              "Morning", "Morning", "Morning", "Night", "Night", "Night"],
})

model = ols("output ~ C(machine) + C(shift) + C(machine):C(shift)", data=df).fit()
anova_table = sm.stats.anova_lm(model, typ=2)

print(anova_table)
```

Formula meaning:

- `C(machine)` checks whether machine type affects output
- `C(shift)` checks whether shift affects output
- `C(machine):C(shift)` checks interaction between machine and shift

Interpretation:

- If p-value for `C(machine)` is `<= 0.05`, machine type has a significant effect
- If p-value for `C(shift)` is `<= 0.05`, shift has a significant effect
- If p-value for `C(machine):C(shift)` is `<= 0.05`, the effect of machine depends on shift

Simple difference:

| One-Way ANOVA | Two-Way ANOVA |
|---|---|
| One categorical factor | Two categorical factors |
| One numerical outcome | One numerical outcome |
| Checks group mean difference for one factor | Checks two factor effects and interaction |
| Example: machine type affects output | Example: machine type and shift affect output |

## 1.16 A/B Testing { .aws-h2 }

A/B testing is a controlled experiment used to compare two versions of something.

Usually:

- **A** = control version, or existing version
- **B** = treatment version, or new version

The goal is to check whether version B performs significantly better or differently than version A.

Common examples:

- compare two landing pages
- compare two email subject lines
- compare two app button colors
- compare old recommendation model vs new recommendation model

### 1.16.1 What A/B Testing Checks { .aws-h3 }

A/B testing checks whether the observed difference between A and B is likely real or could have happened due to random chance.

Example:

```text
Version A conversion rate = 10%
Version B conversion rate = 12%
```

The question is not only whether B is higher. The real question is:

```text
Is the 2% difference statistically significant?
```

### 1.16.2 Hypothesis in A/B Testing { .aws-h3 }

For a two-sided test:

- `H0`: there is no difference between A and B
- `H1`: there is a difference between A and B

For a one-sided test:

- `H0`: B is not better than A
- `H1`: B is better than A

Decision rule:

- If `p-value <= alpha`, reject `H0`
- If `p-value > alpha`, fail to reject `H0`

Usually:

```text
alpha = 0.05
```

### 1.16.3 A/B Test for Conversion Rate { .aws-h3 }

When the metric is a proportion, such as conversion rate, click-through rate, pass rate, or churn rate, use a **two-proportion z-test**.

Example:

```text
Version A: 100 conversions out of 1000 users
Version B: 130 conversions out of 1000 users
```

Conversion rates:

```text
A conversion rate = 100 / 1000 = 10%
B conversion rate = 130 / 1000 = 13%
```

Python:

```python
from statsmodels.stats.proportion import proportions_ztest

conversions = [100, 130]
visitors = [1000, 1000]
alpha = 0.05

z_stat, p_value = proportions_ztest(count=conversions, nobs=visitors)

print("z statistic:", z_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: conversion rates are significantly different")
else:
    print("Fail to reject H0: not enough evidence that conversion rates are different")
```

Interpretation:

- If p-value is small, the difference between A and B is statistically significant
- If p-value is large, the observed difference may be due to random variation

### 1.16.4 A/B Test for Average Value { .aws-h3 }

When the metric is numerical, such as revenue, time spent, order value, or marks, use a **two-sample t-test**.

Example:

```text
Version A average order values: [210, 220, 205, 230, 215]
Version B average order values: [225, 235, 240, 230, 245]
```

Python:

```python
from scipy.stats import ttest_ind

group_a = [210, 220, 205, 230, 215]
group_b = [225, 235, 240, 230, 245]
alpha = 0.05

t_stat, p_value = ttest_ind(group_a, group_b, equal_var=False)

print("t statistic:", t_stat)
print("p-value:", p_value)

if p_value <= alpha:
    print("Reject H0: average values are significantly different")
else:
    print("Fail to reject H0: not enough evidence that average values are different")
```

Here `equal_var=False` applies Welch's t-test, which is safer when group variances may be different.

### 1.16.5 Important A/B Testing Concepts { .aws-h3 }

**Random assignment:**

Users should be randomly assigned to A or B so that groups are comparable.

**Sample size:**

Small samples can give unreliable results. Larger samples provide more stable estimates.

**Primary metric:**

Decide the main metric before running the test, such as conversion rate or average order value.

**Statistical significance:**

Statistical significance means the observed difference is unlikely to be due to random chance.

**Practical significance:**

A result can be statistically significant but still too small to matter in business terms.

Example:

```text
Conversion improves from 10.00% to 10.05%
```

This may be statistically significant with a very large sample, but may not be practically useful.

### 1.16.6 Which Test to Use in A/B Testing { .aws-h3 }

| Metric type | Example metric | Test to use |
|---|---|---|
| Proportion | conversion rate, click-through rate, churn rate | Two-proportion z-test |
| Numerical average | revenue, order value, time spent | Two-sample t-test |
| Categorical distribution | plan selected, satisfaction category | Chi-square test |

Simple rule:

- Use **proportion z-test** when the result is yes/no
- Use **t-test** when comparing average numerical values
- Use **chi-square test** when comparing categorical frequency distributions

### 1.16.7 Common Mistakes in A/B Testing { .aws-h3 }

- stopping the test too early after seeing a good result
- testing too many metrics without adjustment
- changing the experiment while it is running
- not checking sample size
- confusing statistical significance with business impact
- using t-test for conversion rate instead of proportion z-test

## 1.17 Covariance, Correlation, and Regression { .aws-h2 }

### 1.17.1 Covariance { .aws-h3 }

Covariance shows whether two variables move together.

It checks the direction of relationship between two variables:

- when `X` increases, does `Y` also increase?
- when `X` increases, does `Y` decrease?
- or is there no clear movement together?

**Formula:**

```text
Cov(X,Y) = Sum[(Xi - X_bar)(Yi - Y_bar)] / (n - 1)
```

Where:

- `Xi` = each value of variable `X`
- `Yi` = each value of variable `Y`
- `X_bar` = mean of `X`
- `Y_bar` = mean of `Y`
- `n` = number of paired observations

Formula explanation:

1. Find the mean of `X` and mean of `Y`
2. For each pair, calculate how far `Xi` is from `X_bar`
3. For each pair, calculate how far `Yi` is from `Y_bar`
4. Multiply both deviations
5. Add all multiplied deviations
6. Divide by `n - 1` for sample covariance

**Simple explanation:**

- positive covariance: both move together
- negative covariance: one rises while the other falls
- covariance close to zero: no clear linear movement together

Important note:

- covariance tells direction, but its value depends on the units of variables
- because of this, covariance is not easy to compare across different datasets

Python:

```python
import numpy as np

study_hours = np.array([1, 2, 3, 4, 5])
marks = np.array([40, 50, 60, 70, 80])

cov_matrix = np.cov(study_hours, marks, ddof=1)
covariance = cov_matrix[0, 1]

print("covariance matrix:")
print(cov_matrix)
print("covariance:", covariance)
```

Output idea:

- positive covariance means students who study more hours generally score higher marks

### 1.17.2 Correlation { .aws-h3 }

Correlation gives the strength and direction of linear relationship.

It is a standardized version of covariance, so it is easier to interpret.

**Formula:**

```text
r = Cov(X,Y) / (Sx * Sy)
```

Where:

- `r` = Pearson correlation coefficient
- `Cov(X,Y)` = covariance between `X` and `Y`
- `Sx` = standard deviation of `X`
- `Sy` = standard deviation of `Y`

Formula explanation:

1. Calculate covariance between `X` and `Y`
2. Calculate standard deviation of `X`
3. Calculate standard deviation of `Y`
4. Divide covariance by the product of both standard deviations

This standardizes the relationship and keeps correlation between `-1` and `1`.

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

Python:

```python
import numpy as np
from scipy.stats import pearsonr

study_hours = np.array([1, 2, 3, 4, 5])
marks = np.array([40, 50, 60, 70, 80])

corr_matrix = np.corrcoef(study_hours, marks)
correlation, p_value = pearsonr(study_hours, marks)

print("correlation matrix:")
print(corr_matrix)
print("Pearson correlation:", correlation)
print("p-value:", p_value)
```

Interpretation:

- `correlation` tells strength and direction of linear relationship
- `p-value` tells whether the correlation is statistically significant

### 1.17.3 Linear Regression { .aws-h3 }

Linear regression models the relationship between an input variable and a numerical output variable.

It is used when we want to:

- predict a numerical value
- understand how much `Y` changes when `X` changes
- fit a straight line through data

**Simple linear regression formula:**

```text
Y = beta0 + beta1X + error
```

Where:

- `beta0` = intercept
- `beta1` = slope or coefficient
- `X` = input or independent variable
- `Y` = output or dependent variable
- `error` = difference between actual value and predicted value

**Simple explanation:**

Regression finds the best-fit line that predicts `Y` from `X`.

- **Intercept** tells the predicted value of `Y` when `X = 0`
- **Slope** tells how much `Y` changes when `X` increases by 1 unit

Example:

- predict marks using study hours
- predict house price using area
- predict sales using advertising spend

Python:

```python
import numpy as np
from sklearn.linear_model import LinearRegression

study_hours = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)
marks = np.array([40, 50, 60, 70, 80])

model = LinearRegression()
model.fit(study_hours, marks)

slope = model.coef_[0]
intercept = model.intercept_

predicted_marks = model.predict(np.array([[6]]))

print("slope:", slope)
print("intercept:", intercept)
print("predicted marks for 6 study hours:", predicted_marks[0])
```

Interpretation:

- if slope is positive, `Y` increases as `X` increases
- if slope is negative, `Y` decreases as `X` increases
- predicted value is calculated using the regression line

## 1.18 When to Use What { .aws-h2 }

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
| Compare A/B conversion rates | Two-proportion z-test |
| Compare A/B average numerical metric | Two-sample t-test |
| Study relation between two variables | Correlation / regression |

## 1.19 Common Python Functions in Statistics { .aws-h2 }

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
| A/B testing conversion rate | `statsmodels.stats.proportion.proportions_ztest()` |
| A/B testing average metric | `scipy.stats.ttest_ind()` |
| Correlation | `scipy.stats.pearsonr()` |
| Regression | `sklearn.linear_model.LinearRegression()` |

## 1.20 Core Statistical Ideas { .aws-h2 }

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
- A/B testing compares two versions using hypothesis testing
- correlation measures relationship, regression helps prediction

## 1.21 Statistical Workflow { .aws-h2 }

Statistics starts with understanding data and ends with making decisions from data.

The overall flow is usually:

1. describe the data
2. understand randomness using probability distributions
3. take samples and estimate unknown values
4. test claims using z, t, chi-square, or ANOVA
5. compare experiments using A/B testing
6. study relationships using correlation and regression

For data science and analytics roles, the most important topics to know strongly are:

- descriptive statistics
- probability distributions
- sampling and CLT
- confidence intervals
- hypothesis testing
- z-tests and t-tests
- chi-square tests
- ANOVA
- A/B testing
- correlation and regression
