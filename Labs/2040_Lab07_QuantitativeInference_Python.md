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
<title>Lab: Quantitative Inference (Python)</title>
</head>

# Lab: Quantitative Inference (Python)
In this lab, you are a statistical consultant for an airline studying the timing of its ground operations. Every part of the lab uses the same dataset of 160 departing flights, found on the __Data__ sheet of the lab workbook.

| __Variable__            | Values                                   | Column name                   |
| :---------------------- | :--------------------------------------- | :---------------------------- |
| Hub                     | Salt Lake City, Denver, Phoenix, Seattle | `"Hub"`                       |
| Boarding Method         | Old, New                                 | `"Boarding Method"`           |
| Taxi-Out Time (min)     | Quantitative                             | `"Taxi-Out Time (min)"`       |
| Boarding Time (min)     | Quantitative                             | `"Boarding Time (min)"`       |
| Turnaround Time (min)   | Quantitative                             | `"Turnaround Time (min)"`     |

Every procedure in this lab has the same shape:
- A __confidence interval__ is $\text{estimate} \pm (\text{critical value})(\text{standard error})$.
- A __test statistic__ is $\dfrac{\text{estimate} - \text{null value}}{\text{standard error}}$. A small p-value (less than $\alpha = 0.05$) means we reject $H_0$.

__z or t?__ Use $z$ only when the population standard deviation $\sigma$ is given. When you calculate the sample standard deviation $s$ from the data, use $t$.

## Setup

```python
import numpy as np
import pandas as pd
from scipy import stats

df = pd.read_excel("Airline_Quantitative_Inference_Lab.xlsx", sheet_name="Data", usecols="A:F")
df.head()
```

Column names contain spaces and parentheses, so always use brackets: `df["Boarding Time (min)"]`.

## Summary Statistics with Python

| __Summary Statistics__                    | Python Command                                                          |
| :---------------------------------------- | :---------------------------------------------------------------------- |
| Sample size $n$                           | `df["Taxi-Out Time (min)"].count()`                                     |
| Sample mean $\bar{x}$                     | `df["Taxi-Out Time (min)"].mean()`                                      |
| Sample standard deviation $s$             | `df["Taxi-Out Time (min)"].std()`                                       |
| Keep only one group                       | `new = df.loc[df["Boarding Method"] == "New", "Boarding Time (min)"]`   |
| $n$, mean and $s$ for every group         | `df.groupby("Hub")["Turnaround Time (min)"].agg(["count", "mean", "std"])` |
| Square root                               | `np.sqrt(number)`                                                       |

pandas `.std()` divides by $n-1$ (the sample standard deviation, like `STDEV.S`). NumPy’s `np.std()` divides by $n$ unless you add `ddof=1`, so use the pandas version.

## The Standard Normal Distribution (σ known)

| __Standard Normal__                         | Python Command                             | Excel Equivalent            |
| :------------------------------------------ | :----------------------------------------- | :-------------------------- |
| Critical value $z^*$ for confidence $C$     | `stats.norm.ppf(1 - (1 - C)/2)`            | `=NORM.S.INV(1-(1-C)/2)`    |
| $z^*$ for 95% confidence                    | `stats.norm.ppf(0.975)` (gives 1.96)       | `=NORM.S.INV(0.975)`        |
| Left-tail probability $P(Z \le z)$          | `stats.norm.cdf(z)`                        | `=NORM.S.DIST(z, TRUE)`     |
| Right-tail probability $P(Z \ge z)$         | `stats.norm.sf(z)`                         | `=1-NORM.S.DIST(z, TRUE)`   |
| Two-sided p-value                           | `2 * stats.norm.sf(abs(z))`                | `=2*(1-NORM.S.DIST(ABS(z), TRUE))` |

## Part A: One-Sample z-Interval

$$\bar{x} \pm z^* \frac{\sigma}{\sqrt{n}}$$

Conditions: random sample, and the population is normal or $n \ge 30$.

```python
taxi = df["Taxi-Out Time (min)"]
n = taxi.count()
xbar = taxi.mean()
sigma = 4.5                      # given

C = 0.95
zstar = stats.norm.ppf(1 - (1 - C)/2)
SE = sigma / np.sqrt(n)
ME = zstar * SE
print(xbar, xbar - ME, xbar + ME)
```

## Part B: One-Sample z-Test

$$H_0: \mu = \mu_0 \qquad z = \frac{\bar{x}-\mu_0}{\sigma/\sqrt{n}}$$

```python
mu0 = 18
z = (xbar - mu0) / (sigma / np.sqrt(n))
p_value = 2 * stats.norm.sf(abs(z))     # two-sided
print(z, p_value)
```

## The t Distribution (σ unknown)
The $t$ distribution looks like the standard normal but has heavier tails, which accounts for the extra uncertainty from estimating $\sigma$ with $s$. Its shape depends on the __degrees of freedom__; for one sample, $df = n-1$.

| __t Distribution__                          | Python Command                             | Excel Equivalent             |
| :------------------------------------------ | :----------------------------------------- | :--------------------------- |
| Critical value $t^*$ for confidence $C$     | `stats.t.ppf(1 - (1 - C)/2, dof)`          | `=T.INV.2T(1-C, df)`         |
| Two-sided p-value                           | `2 * stats.t.sf(abs(t), dof)`              | `=T.DIST.2T(ABS(t), df)`     |
| One-sided p-value ($H_a$: $<$)              | `stats.t.cdf(t, dof)`                      | `=T.DIST(t, df, TRUE)`       |
| One-sided p-value ($H_a$: $>$)              | `stats.t.sf(t, dof)`                       | `=T.DIST.RT(t, df)`          |

Be careful not to name a variable `df` for degrees of freedom, since `df` already holds the data. This sheet uses `dof` instead.

## Part C: One-Sample t-Interval

$$\bar{x} \pm t^* \frac{s}{\sqrt{n}} \qquad df = n-1$$

Conditions: random sample, and the population is normal or $n \ge 30$ (with small samples, no strong skew or outliers).

```python
new = df.loc[df["Boarding Method"] == "New", "Boarding Time (min)"]
n = new.count()
xbar = new.mean()
s = new.std()
dof = n - 1

tstar = stats.t.ppf(1 - (1 - C)/2, dof)
SE = s / np.sqrt(n)
ME = tstar * SE
print(xbar, xbar - ME, xbar + ME)

# Check with scipy's built-in interval
stats.t.interval(C, dof, loc=xbar, scale=SE)
```

## Part D: One-Sample t-Test

$$H_0: \mu = \mu_0 \qquad t = \frac{\bar{x}-\mu_0}{s/\sqrt{n}} \qquad df = n-1$$

```python
mu0 = 30
t = (xbar - mu0) / (s / np.sqrt(n))
p_value = stats.t.cdf(t, dof)           # left-tailed: Ha is mu < 30
print(t, dof, p_value)

# Check with scipy's built-in test
stats.ttest_1samp(new, popmean=mu0, alternative="less")
```

`alternative` can be `"two-sided"` (the default), `"less"` or `"greater"`.

## Part E: Two-Sample t-Interval

$$(\bar{x}_1-\bar{x}_2) \pm t^* \sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}$$

The degrees of freedom come from the Welch formula. Let $a = s_1^2/n_1$ and $b = s_2^2/n_2$:

$$df = \frac{(a+b)^2}{\frac{a^2}{n_1-1}+\frac{b^2}{n_2-1}}$$

A conservative (smaller) alternative is $df = \min(n_1-1,\; n_2-1)$.

Conditions: independent random samples, and each population is normal or each $n \ge 30$.

```python
old = df.loc[df["Boarding Method"] == "Old", "Boarding Time (min)"]
n1, xbar1, s1 = new.count(), new.mean(), new.std()
n2, xbar2, s2 = old.count(), old.mean(), old.std()

a, b = s1**2 / n1, s2**2 / n2
SE = np.sqrt(a + b)
dof = (a + b)**2 / (a**2/(n1 - 1) + b**2/(n2 - 1))     # Welch
tstar = stats.t.ppf(1 - (1 - C)/2, dof)
ME = tstar * SE
diff = xbar1 - xbar2
print(diff, dof, diff - ME, diff + ME)
```

## Part F: Two-Sample t-Test

$$H_0: \mu_1 = \mu_2 \qquad t = \frac{\bar{x}_1-\bar{x}_2}{\sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}}$$

```python
t = diff / SE
p_value = 2 * stats.t.sf(abs(t), dof)    # two-sided
print(t, dof, p_value)

# Check with scipy's built-in test (equal_var=False means Welch)
result = stats.ttest_ind(new, old, equal_var=False)
print(result)
print(result.confidence_interval(C))     # also checks Part E
```

`equal_var=False` gives the Welch test. Leaving it out uses the pooled-variance test, which assumes the two groups have the same spread.

## The F Distribution
ANOVA compares the variability __between__ group means to the variability __within__ groups. The F statistic is a ratio of the two, and the p-value is always a __right-tail__ area.

| __F Distribution__              | Python Command                        | Excel Equivalent                 |
| :------------------------------ | :------------------------------------ | :------------------------------- |
| p-value                         | `stats.f.sf(F, df1, df2)`             | `=F.DIST.RT(F, df1, df2)`        |
| Critical value                  | `stats.f.isf(alpha, df1, df2)`        | `=F.INV.RT(alpha, df1, df2)`     |

## Part G: One-Way ANOVA
Do the means of $k$ groups differ? With $N$ total observations and grand mean $\bar{x}$:

$$H_0: \mu_1 = \mu_2 = \dots = \mu_k \qquad H_a: \text{at least one mean is different}$$

$$SSG = \sum n_i(\bar{x}_i-\bar{x})^2 \qquad SSE = \sum (n_i-1)s_i^2 \qquad F = \frac{SSG/(k-1)}{SSE/(N-k)}$$

Conditions: independent random samples, each group roughly normal (or large), and similar spreads: $\dfrac{\text{largest } s}{\text{smallest } s} < 2$.

```python
y = "Turnaround Time (min)"
summary = df.groupby("Hub")[y].agg(["count", "mean", "std"])
print(summary)
print("spread ratio:", summary["std"].max() / summary["std"].min())

grand_mean = df[y].mean()
N, k = len(df), len(summary)

SSG = (summary["count"] * (summary["mean"] - grand_mean)**2).sum()
SSE = ((summary["count"] - 1) * summary["std"]**2).sum()
MSG, MSE = SSG / (k - 1), SSE / (N - k)
F = MSG / MSE
p_value = stats.f.sf(F, k - 1, N - k)

anova_table = pd.DataFrame({"df": [k - 1, N - k, N - 1],
                            "SS": [SSG, SSE, SSG + SSE],
                            "MS": [MSG, MSE, np.nan],
                            "F":  [F, np.nan, np.nan],
                            "p-value": [p_value, np.nan, np.nan]},
                           index=["Groups (Hub)", "Error", "Total"])
print(anova_table)

# Check with scipy's built-in test (one array per group)
groups = [g[y] for _, g in df.groupby("Hub")]
stats.f_oneway(*groups)
```

ANOVA only tells you that __at least one__ mean differs; compare the group means in `summary` to describe which hubs stand out.

## Which Procedure Do I Use?

| __Question involves...__                                   | Procedure                    | Lab Part |
| :--------------------------------------------------------- | :--------------------------- | :------- |
| Estimating one mean, $\sigma$ known                        | One-sample z-interval        | A        |
| Testing one mean against a claimed value, $\sigma$ known   | One-sample z-test            | B        |
| Estimating one mean, $\sigma$ unknown                      | One-sample t-interval        | C        |
| Testing one mean against a claimed value, $\sigma$ unknown | One-sample t-test            | D        |
| Estimating the difference between two means                | Two-sample t-interval        | E        |
| Testing whether two means are equal                        | Two-sample t-test            | F        |
| Comparing the means of three or more groups                | One-way ANOVA                | G        |
