<head>
<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
    displayMath: [['$$', '$$'], ['\\[', '\\]']]
  }
};
</script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<title>Lab: Categorical Inference (Python)</title>
</head>

# Lab: Categorical Inference (Python)
In this lab, you are going to assume the role of a statistical consultant for an airline that is testing a new boarding process. The goal of this lab will be to perform a statistical inference to explore the data.

Remember the two kinds of inference:
- A __confidence interval__ *estimates* a parameter: $\text{estimate} \pm \text{margin of error}$
- A __hypothesis test__ asks whether the data give *evidence against* a claim ($H_0$). A small p-value (less than $\alpha = 0.05$) means we reject $H_0$.
    - __Chi-squared tests__ are like hypothesis tests but consider multiple categories for a single variable

## Setup
We use `pandas` for the data and `scipy.stats` for the normal and chi-square distributions.

```python
import numpy as np
import pandas as pd
from scipy import stats

df = pd.read_excel("Airline_Categorical_Inference_Lab.xlsx", sheet_name="Data")
df.head()
```

Column names contain spaces, so always use brackets: `df["Seat Class"]`, never `df.Seat Class`.

## Counting with Python
Everything in this lab starts with counting.

| __Counting__                              | Python Command                                                             |
| :---------------------------------------- | :------------------------------------------------------------------------- |
| Sample size $n$                           | `len(df)`                                                                  |
| Number of successes $x$                   | `(df["Satisfaction"] == "Satisfied").sum()`                                |
| Count in one group                        | `(df["Flight Type"] == "Domestic").sum()`                                  |
| Count matching two conditions             | `((df["Flight Type"] == "Domestic") & (df["Satisfaction"] == "Satisfied")).sum()` |
| Counts for every category                 | `df["Seat Class"].value_counts()`                                          |
| Proportions for every category            | `df["Seat Class"].value_counts(normalize=True)`                            |
| Two-way table of counts                   | `pd.crosstab(df["Seat Class"], df["Satisfaction"])`                        |
| Sample proportion $\hat{p} = x/n$         | `x / n`                                                                    |
| Square root                               | `np.sqrt(number)`                                                          |
| Absolute value                            | `abs(number)`                                                              |

The text in quotes must match the data exactly, including spaces (for example, `"Premium Economy"`).

## The Standard Normal Distribution
Proportion procedures use $z$. In `scipy.stats`, `norm` is the standard normal by default.

| __Standard Normal__                         | Python Command                             | Excel Equivalent            |
| :------------------------------------------ | :----------------------------------------- | :-------------------------- |
| Critical value $z^*$ for confidence $C$     | `stats.norm.ppf(1 - (1 - C)/2)`            | `=NORM.S.INV(1-(1-C)/2)`    |
| $z^*$ for 95% confidence                    | `stats.norm.ppf(0.975)` (gives 1.96)       | `=NORM.S.INV(0.975)`        |
| Left-tail probability $P(Z \le z)$          | `stats.norm.cdf(z)`                        | `=NORM.S.DIST(z, TRUE)`     |
| Right-tail probability $P(Z \ge z)$         | `stats.norm.sf(z)`                         | `=1-NORM.S.DIST(z, TRUE)`   |
| Two-sided p-value                           | `2 * stats.norm.sf(abs(z))`                | `=2*(1-NORM.S.DIST(ABS(z), TRUE))` |

## Part A: One-Proportion Confidence Interval

$$\hat{p} \pm z^* \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$

Conditions: $n\hat{p} \ge 10$ and $n(1-\hat{p}) \ge 10$.

```python
n = len(df)
x = (df["Satisfaction"] == "Satisfied").sum()
phat = x / n

C = 0.95
zstar = stats.norm.ppf(1 - (1 - C)/2)
SE = np.sqrt(phat * (1 - phat) / n)
ME = zstar * SE
print(phat, phat - ME, phat + ME)
```

## Part B: One-Proportion Hypothesis Test

$$H_0: p = p_0 \qquad z = \frac{\hat{p}-p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$$

Conditions: $np_0 \ge 10$ and $n(1-p_0) \ge 10$. Notice the standard error uses $p_0$, not $\hat{p}$.

```python
p0 = 0.80
SE0 = np.sqrt(p0 * (1 - p0) / n)
z = (phat - p0) / SE0
p_value = 2 * stats.norm.sf(abs(z))      # two-sided
print(z, p_value)
```

## Part C: Two-Proportion Confidence Interval

$$(\hat{p}_1-\hat{p}_2) \pm z^* \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}+\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$$

Conditions: at least 10 successes and 10 failures in __each__ group. If the interval contains 0, there may be no difference between the groups.

```python
sat = df["Satisfaction"] == "Satisfied"
dom = df["Flight Type"] == "Domestic"
intl = df["Flight Type"] == "International"

n1, x1 = dom.sum(), (dom & sat).sum()
n2, x2 = intl.sum(), (intl & sat).sum()
p1, p2 = x1 / n1, x2 / n2

SE = np.sqrt(p1*(1 - p1)/n1 + p2*(1 - p2)/n2)    # unpooled
ME = zstar * SE
print(p1 - p2, (p1 - p2) - ME, (p1 - p2) + ME)
```

A shortcut that computes $\hat{p}$ for every group at once:

```python
df.groupby("Flight Type")["Satisfaction"].apply(lambda s: (s == "Satisfied").mean())
```

## Part D: Two-Proportion Hypothesis Test

$$H_0: p_1 = p_2 \qquad \hat{p} = \frac{x_1+x_2}{n_1+n_2} \qquad z = \frac{\hat{p}_1-\hat{p}_2}{\sqrt{\hat{p}(1-\hat{p})\left(\frac{1}{n_1}+\frac{1}{n_2}\right)}}$$

Because $H_0$ says the proportions are equal, the test uses the __pooled__ proportion $\hat{p}$.

```python
new = df["Boarding Method"] == "New"
old = df["Boarding Method"] == "Old"

n1, x1 = new.sum(), (new & sat).sum()
n2, x2 = old.sum(), (old & sat).sum()
p1, p2 = x1 / n1, x2 / n2

pp = (x1 + x2) / (n1 + n2)                        # pooled proportion
SE = np.sqrt(pp * (1 - pp) * (1/n1 + 1/n2))
z = (p1 - p2) / SE
p_value = 2 * stats.norm.sf(abs(z))
print(pp, z, p_value)
```

## Chi-Square Distributions
When a categorical variable has more than two categories, a single proportion no longer tells the whole story. Chi-square tests compare __observed__ counts ($O$) to __expected__ counts ($E$):

$$\chi^2 = \sum \frac{(O-E)^2}{E}$$

Conditions: all expected counts must be at least 5. The p-value is always a __right-tail__ area.

| __Chi-Square Distribution__     | Python Command                                | Excel Equivalent                       |
| :------------------------------ | :-------------------------------------------- | :------------------------------------- |
| p-value from $\chi^2$ and df    | `stats.chi2.sf(chi_square, df)`               | `=CHISQ.DIST.RT(chi_square, df)`       |
| Critical value                  | `stats.chi2.isf(alpha, df)`                   | `=CHISQ.INV.RT(alpha, df)`             |
| Goodness-of-fit test            | `stats.chisquare(f_obs=O, f_exp=E)`           | `=CHISQ.TEST(observed, expected)`      |
| Test of independence            | `stats.chi2_contingency(table)`               | `=CHISQ.TEST(observed, expected)`      |

Be careful not to name a variable `df` for degrees of freedom, since `df` already holds the data. This sheet uses `dof` instead.

## Part E: Chi-Square Goodness-of-Fit Test
Does one categorical variable follow a claimed distribution?

$$E = n \times (\text{hypothesized proportion}) \qquad df = k - 1$$

where $k$ is the number of categories.

```python
order = ["Economy", "Premium Economy", "Business", "First"]
O = df["Seat Class"].value_counts().reindex(order)   # keep categories in order
expected_pct = np.array([0.55, 0.20, 0.15, 0.10])
E = O.sum() * expected_pct

contrib = (O - E)**2 / E
chi_square = contrib.sum()
dof = len(order) - 1
p_value = stats.chi2.sf(chi_square, dof)

print(pd.DataFrame({"Observed": O, "Expected": E, "Contribution": contrib}))
print(chi_square, dof, p_value)

# Check with scipy's built-in test
stats.chisquare(f_obs=O, f_exp=E)
```

`value_counts()` sorts from most to least common, so `.reindex(order)` makes sure the observed counts line up with the expected percentages.

## Part F: Chi-Square Test of Independence
Are two categorical variables associated?

$$E = \frac{(\text{row total})(\text{column total})}{\text{grand total}} \qquad df = (r-1)(c-1)$$

```python
table = pd.crosstab(df["Seat Class"], df["Satisfaction"]).reindex(order)
print(table)

# Conditional (row) percentages
print(pd.crosstab(df["Seat Class"], df["Satisfaction"], normalize="index").reindex(order))

# By hand: expected counts, statistic, df, p-value
row_tot = table.sum(axis=1).to_numpy()
col_tot = table.sum(axis=0).to_numpy()
E = np.outer(row_tot, col_tot) / table.to_numpy().sum()
chi_square = ((table.to_numpy() - E)**2 / E).sum()
dof = (table.shape[0] - 1) * (table.shape[1] - 1)
p_value = stats.chi2.sf(chi_square, dof)
print(chi_square, dof, p_value)

# Check with scipy's built-in test
result = stats.chi2_contingency(table, correction=False)
print(result.statistic, result.dof, result.pvalue)
print(result.expected_freq)
```

| __Test of Independence__        | Python Command                                                         |
| :------------------------------ | :--------------------------------------------------------------------- |
| Observed table                  | `pd.crosstab(df["Seat Class"], df["Satisfaction"])`                     |
| Table with totals               | `pd.crosstab(df["Seat Class"], df["Satisfaction"], margins=True)`       |
| Conditional (row) percentages   | `pd.crosstab(..., normalize="index")`                                   |
| Expected counts                 | `np.outer(row_tot, col_tot) / grand_total`                              |
| Full test                       | `stats.chi2_contingency(table, correction=False)`                       |

`correction=False` turns off the Yates continuity correction. It only matters for 2×2 tables, but including it makes `chi2_contingency` match the hand calculation every time.

## Which Procedure Do I Use?

| __Question involves...__                               | Procedure                        | Lab Part |
| :----------------------------------------------------- | :------------------------------- | :------- |
| Estimating one proportion                              | One-proportion z-interval        | A        |
| Testing one proportion against a claimed value         | One-proportion z-test            | B        |
| Estimating the difference between two proportions      | Two-proportion z-interval        | C        |
| Testing whether two proportions are equal              | Two-proportion z-test            | D        |
| One variable with 3+ categories vs. a claimed distribution | Chi-square goodness-of-fit   | E        |
| Association between two categorical variables          | Chi-square test of independence  | F        |
