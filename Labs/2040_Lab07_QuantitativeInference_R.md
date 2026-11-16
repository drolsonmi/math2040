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
<title>Lab: Quantitative Inference (R)</title>
</head>

# Lab: Quantitative Inference (R)
In this lab, you are a statistical consultant for an airline studying the timing of its ground operations. Every part of the lab uses the same dataset of 160 departing flights, found on the __Data__ sheet of the lab workbook.

| __Variable__            | Values                                   | Column name                         |
| :---------------------- | :--------------------------------------- | :---------------------------------- |
| Hub                     | Salt Lake City, Denver, Phoenix, Seattle | `df[["Hub"]]`                       |
| Boarding Method         | Old, New                                 | `df[["Boarding Method"]]`           |
| Taxi-Out Time (min)     | Quantitative                             | `df[["Taxi-Out Time (min)"]]`       |
| Boarding Time (min)     | Quantitative                             | `df[["Boarding Time (min)"]]`       |
| Turnaround Time (min)   | Quantitative                             | `df[["Turnaround Time (min)"]]`     |

Every procedure in this lab has the same shape:
- A __confidence interval__ is $\text{estimate} \pm (\text{critical value})(\text{standard error})$.
- A __test statistic__ is $\dfrac{\text{estimate} - \text{null value}}{\text{standard error}}$. A small p-value (less than $\alpha = 0.05$) means we reject $H_0$.

__z or t?__ Use $z$ only when the population standard deviation $\sigma$ is given. When you calculate the sample standard deviation $s$ from the data, use $t$.

## Setup
We use the `readxl` package to read the workbook. Everything else is built into R.

```r
# install.packages("readxl")   # run once if needed
library(readxl)

df <- read_excel("Airline_Quantitative_Inference_Lab.xlsx", sheet = "Data", range = "A1:F161")
head(df)
```

Column names contain spaces and parentheses, so use double brackets: `df[["Boarding Time (min)"]]`.

## Summary Statistics with R

| __Summary Statistics__                    | R Command                                                                   |
| :---------------------------------------- | :-------------------------------------------------------------------------- |
| Sample size $n$                           | `length(x)`                                                                 |
| Sample mean $\bar{x}$                     | `mean(x)`                                                                   |
| Sample standard deviation $s$             | `sd(x)`                                                                     |
| Keep only one group                       | `new <- df[["Boarding Time (min)"]][df[["Boarding Method"]] == "New"]`      |
| $n$ for every group                       | `tapply(y, group, length)`                                                  |
| Mean for every group                      | `tapply(y, group, mean)`                                                    |
| $s$ for every group                       | `tapply(y, group, sd)`                                                      |
| Square root                               | `sqrt(number)`                                                              |

R’s `sd()` divides by $n-1$, so it is the sample standard deviation (like `STDEV.S`).

## The Standard Normal Distribution (σ known)

| __Standard Normal__                         | R Command                                  | Excel Equivalent            |
| :------------------------------------------ | :----------------------------------------- | :-------------------------- |
| Critical value $z^*$ for confidence $C$     | `qnorm(1 - (1 - C)/2)`                     | `=NORM.S.INV(1-(1-C)/2)`    |
| $z^*$ for 95% confidence                    | `qnorm(0.975)` (gives 1.96)                | `=NORM.S.INV(0.975)`        |
| Left-tail probability $P(Z \le z)$          | `pnorm(z)`                                 | `=NORM.S.DIST(z, TRUE)`     |
| Right-tail probability $P(Z \ge z)$         | `pnorm(z, lower.tail = FALSE)`             | `=1-NORM.S.DIST(z, TRUE)`   |
| Two-sided p-value                           | `2 * pnorm(abs(z), lower.tail = FALSE)`    | `=2*(1-NORM.S.DIST(ABS(z), TRUE))` |

## Part A: One-Sample z-Interval

$$\bar{x} \pm z^* \frac{\sigma}{\sqrt{n}}$$

Conditions: random sample, and the population is normal or $n \ge 30$.

```r
taxi <- df[["Taxi-Out Time (min)"]]
n <- length(taxi)
xbar <- mean(taxi)
sigma <- 4.5                     # given

C <- 0.95
zstar <- qnorm(1 - (1 - C)/2)
SE <- sigma / sqrt(n)
ME <- zstar * SE
c(xbar = xbar, lower = xbar - ME, upper = xbar + ME)
```

## Part B: One-Sample z-Test

$$H_0: \mu = \mu_0 \qquad z = \frac{\bar{x}-\mu_0}{\sigma/\sqrt{n}}$$

```r
mu0 <- 18
z <- (xbar - mu0) / (sigma / sqrt(n))
p_value <- 2 * pnorm(abs(z), lower.tail = FALSE)   # two-sided
c(z = z, p_value = p_value)
```

Base R has no built-in z-test because $\sigma$ is so rarely known; the calculation above is all you need.

## The t Distribution (σ unknown)
The $t$ distribution looks like the standard normal but has heavier tails, which accounts for the extra uncertainty from estimating $\sigma$ with $s$. Its shape depends on the __degrees of freedom__; for one sample, $df = n-1$.

| __t Distribution__                          | R Command                                  | Excel Equivalent             |
| :------------------------------------------ | :----------------------------------------- | :--------------------------- |
| Critical value $t^*$ for confidence $C$     | `qt(1 - (1 - C)/2, dof)`                   | `=T.INV.2T(1-C, df)`         |
| Two-sided p-value                           | `2 * pt(abs(t), dof, lower.tail = FALSE)`  | `=T.DIST.2T(ABS(t), df)`     |
| One-sided p-value ($H_a$: $<$)              | `pt(t, dof)`                               | `=T.DIST(t, df, TRUE)`       |
| One-sided p-value ($H_a$: $>$)              | `pt(t, dof, lower.tail = FALSE)`           | `=T.DIST.RT(t, df)`          |

Be careful not to name a variable `df` for degrees of freedom, since `df` already holds the data. This sheet uses `dof` instead. Likewise, avoid naming a variable `t`: it works, but it hides R’s built-in transpose function `t()`. This sheet uses `t_stat`.

## Part C: One-Sample t-Interval

$$\bar{x} \pm t^* \frac{s}{\sqrt{n}} \qquad df = n-1$$

Conditions: random sample, and the population is normal or $n \ge 30$ (with small samples, no strong skew or outliers).

```r
new <- df[["Boarding Time (min)"]][df[["Boarding Method"]] == "New"]
n <- length(new)
xbar <- mean(new)
s <- sd(new)
dof <- n - 1

tstar <- qt(1 - (1 - C)/2, dof)
SE <- s / sqrt(n)
ME <- tstar * SE
c(xbar = xbar, lower = xbar - ME, upper = xbar + ME)

# Check with R's built-in t.test (the interval is part of the output)
t.test(new, conf.level = C)$conf.int
```

## Part D: One-Sample t-Test

$$H_0: \mu = \mu_0 \qquad t = \frac{\bar{x}-\mu_0}{s/\sqrt{n}} \qquad df = n-1$$

```r
mu0 <- 30
t_stat <- (xbar - mu0) / (s / sqrt(n))
p_value <- pt(t_stat, dof)               # left-tailed: Ha is mu < 30
c(t = t_stat, dof = dof, p_value = p_value)

# Check with R's built-in test
t.test(new, mu = mu0, alternative = "less")
```

`alternative` can be `"two.sided"` (the default), `"less"` or `"greater"`.

## Part E: Two-Sample t-Interval

$$(\bar{x}_1-\bar{x}_2) \pm t^* \sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}$$

The degrees of freedom come from the Welch formula. Let $a = s_1^2/n_1$ and $b = s_2^2/n_2$:

$$df = \frac{(a+b)^2}{\frac{a^2}{n_1-1}+\frac{b^2}{n_2-1}}$$

A conservative (smaller) alternative is $df = \min(n_1-1,\; n_2-1)$.

Conditions: independent random samples, and each population is normal or each $n \ge 30$.

```r
old <- df[["Boarding Time (min)"]][df[["Boarding Method"]] == "Old"]
n1 <- length(new); xbar1 <- mean(new); s1 <- sd(new)
n2 <- length(old); xbar2 <- mean(old); s2 <- sd(old)

a <- s1^2 / n1;  b <- s2^2 / n2
SE <- sqrt(a + b)
dof <- (a + b)^2 / (a^2/(n1 - 1) + b^2/(n2 - 1))     # Welch
tstar <- qt(1 - (1 - C)/2, dof)
ME <- tstar * SE
diff <- xbar1 - xbar2
c(diff = diff, dof = dof, lower = diff - ME, upper = diff + ME)
```

## Part F: Two-Sample t-Test

$$H_0: \mu_1 = \mu_2 \qquad t = \frac{\bar{x}_1-\bar{x}_2}{\sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}}$$

```r
t_stat <- diff / SE
p_value <- 2 * pt(abs(t_stat), dof, lower.tail = FALSE)   # two-sided
c(t = t_stat, dof = dof, p_value = p_value)

# Check with R's built-in test (Welch is the default; the output also checks Part E)
t.test(new, old)
```

`t.test` uses the Welch test by default. Adding `var.equal = TRUE` switches to the pooled-variance test, which assumes the two groups have the same spread.

## The F Distribution
ANOVA compares the variability __between__ group means to the variability __within__ groups. The F statistic is a ratio of the two, and the p-value is always a __right-tail__ area.

| __F Distribution__              | R Command                                      | Excel Equivalent                 |
| :------------------------------ | :--------------------------------------------- | :------------------------------- |
| p-value                         | `pf(F, df1, df2, lower.tail = FALSE)`          | `=F.DIST.RT(F, df1, df2)`        |
| Critical value                  | `qf(alpha, df1, df2, lower.tail = FALSE)`      | `=F.INV.RT(alpha, df1, df2)`     |

## Part G: One-Way ANOVA
Do the means of $k$ groups differ? With $N$ total observations and grand mean $\bar{x}$:

$$H_0: \mu_1 = \mu_2 = \dots = \mu_k \qquad H_a: \text{at least one mean is different}$$

$$SSG = \sum n_i(\bar{x}_i-\bar{x})^2 \qquad SSE = \sum (n_i-1)s_i^2 \qquad F = \frac{SSG/(k-1)}{SSE/(N-k)}$$

Conditions: independent random samples, each group roughly normal (or large), and similar spreads: $\dfrac{\text{largest } s}{\text{smallest } s} < 2$.

```r
y <- df[["Turnaround Time (min)"]]
hub <- df[["Hub"]]

ni <- tapply(y, hub, length)
means <- tapply(y, hub, mean)
sds <- tapply(y, hub, sd)
cbind(n = ni, mean = means, sd = sds)
max(sds) / min(sds)                      # spread ratio

grand_mean <- mean(y)
N <- length(y);  k <- length(ni)

SSG <- sum(ni * (means - grand_mean)^2)
SSE <- sum((ni - 1) * sds^2)
MSG <- SSG / (k - 1);  MSE <- SSE / (N - k)
F_stat <- MSG / MSE
p_value <- pf(F_stat, k - 1, N - k, lower.tail = FALSE)
c(SSG = SSG, SSE = SSE, F = F_stat, p_value = p_value)

# Check with R's built-in ANOVA
summary(aov(y ~ hub))
```

`aov(y ~ hub)` reads as “model `y` by `hub`.” In its output, the `hub` row holds SSG and the `Residuals` row holds SSE. ANOVA only tells you that __at least one__ mean differs; compare the group means to describe which hubs stand out.

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
