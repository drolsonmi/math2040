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
<title>Lab: Categorical Inference (R)</title>
</head>

# Lab: Categorical Inference (R)
In this lab, you are going to assume the role of a statistical consultant for an airline that is testing a new boarding process. The goal of this lab will be to perform a statistical inference to explore the data.

Remember the two kinds of inference:
- A __confidence interval__ *estimates* a parameter: $\text{estimate} \pm \text{margin of error}$
- A __hypothesis test__ asks whether the data give *evidence against* a claim ($H_0$). A small p-value (less than $\alpha = 0.05$) means we reject $H_0$.
    - __Chi-squared tests__ are like hypothesis tests but consider multiple categories for a single variable

## Setup
We use the `readxl` package to read the workbook. Everything else is built into R.

```r
# install.packages("readxl")   # run once if needed
library(readxl)

df <- read_excel("Airline_Categorical_Inference_Lab.xlsx", sheet = "Data")
head(df)
```

Column names contain spaces, so use double brackets: `df[["Seat Class"]]`. (Inside code you can also wrap the name in backticks after the dollar sign.)

## Counting with R
Everything in this lab starts with counting. In R, `TRUE` counts as 1, so `sum()` of a comparison counts the matches.

| __Counting__                              | R Command                                                                         |
| :---------------------------------------- | :-------------------------------------------------------------------------------- |
| Sample size $n$                           | `nrow(df)`                                                                        |
| Number of successes $x$                   | `sum(df[["Satisfaction"]] == "Satisfied")`                                        |
| Count in one group                        | `sum(df[["Flight Type"]] == "Domestic")`                                          |
| Count matching two conditions             | `sum(df[["Flight Type"]] == "Domestic" & df[["Satisfaction"]] == "Satisfied")`    |
| Counts for every category                 | `table(df[["Seat Class"]])`                                                       |
| Proportions for every category            | `prop.table(table(df[["Seat Class"]]))`                                           |
| Two-way table of counts                   | `table(df[["Seat Class"]], df[["Satisfaction"]])`                                 |
| Table with totals                         | `addmargins(tab)`                                                                 |
| Sample proportion $\hat{p} = x/n$         | `x / n`                                                                           |
| Square root                               | `sqrt(number)`                                                                    |
| Absolute value                            | `abs(number)`                                                                     |

The text in quotes must match the data exactly, including spaces (for example, `"Premium Economy"`).

## The Standard Normal Distribution
Proportion procedures use $z$. In R, `pnorm` and `qnorm` use the standard normal by default.

| __Standard Normal__                         | R Command                                  | Excel Equivalent            |
| :------------------------------------------ | :----------------------------------------- | :-------------------------- |
| Critical value $z^*$ for confidence $C$     | `qnorm(1 - (1 - C)/2)`                     | `=NORM.S.INV(1-(1-C)/2)`    |
| $z^*$ for 95% confidence                    | `qnorm(0.975)` (gives 1.96)                | `=NORM.S.INV(0.975)`        |
| Left-tail probability $P(Z \le z)$          | `pnorm(z)`                                 | `=NORM.S.DIST(z, TRUE)`     |
| Right-tail probability $P(Z \ge z)$         | `pnorm(z, lower.tail = FALSE)`             | `=1-NORM.S.DIST(z, TRUE)`   |
| Two-sided p-value                           | `2 * pnorm(abs(z), lower.tail = FALSE)`    | `=2*(1-NORM.S.DIST(ABS(z), TRUE))` |

## Part A: One-Proportion Confidence Interval

$$\hat{p} \pm z^* \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$

Conditions: $n\hat{p} \ge 10$ and $n(1-\hat{p}) \ge 10$.

```r
n <- nrow(df)
x <- sum(df[["Satisfaction"]] == "Satisfied")
phat <- x / n

C <- 0.95
zstar <- qnorm(1 - (1 - C)/2)
SE <- sqrt(phat * (1 - phat) / n)
ME <- zstar * SE
c(phat = phat, lower = phat - ME, upper = phat + ME)
```

## Part B: One-Proportion Hypothesis Test

$$H_0: p = p_0 \qquad z = \frac{\hat{p}-p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$$

Conditions: $np_0 \ge 10$ and $n(1-p_0) \ge 10$. Notice the standard error uses $p_0$, not $\hat{p}$.

```r
p0 <- 0.80
SE0 <- sqrt(p0 * (1 - p0) / n)
z <- (phat - p0) / SE0
p_value <- 2 * pnorm(abs(z), lower.tail = FALSE)   # two-sided
c(z = z, p_value = p_value)

# Check with R's built-in test (reports X-squared = z^2; same p-value)
prop.test(x, n, p = p0, correct = FALSE)
```

`prop.test` reports a chi-square statistic equal to $z^2$ and the same p-value as the z-test. Its confidence interval uses a different method (the Wilson interval), so it will not exactly match the interval from Part A.

## Part C: Two-Proportion Confidence Interval

$$(\hat{p}_1-\hat{p}_2) \pm z^* \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}+\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$$

Conditions: at least 10 successes and 10 failures in __each__ group. If the interval contains 0, there may be no difference between the groups.

```r
sat  <- df[["Satisfaction"]] == "Satisfied"
dom  <- df[["Flight Type"]] == "Domestic"
intl <- df[["Flight Type"]] == "International"

n1 <- sum(dom);  x1 <- sum(dom & sat)
n2 <- sum(intl); x2 <- sum(intl & sat)
p1 <- x1 / n1;   p2 <- x2 / n2

SE <- sqrt(p1*(1 - p1)/n1 + p2*(1 - p2)/n2)    # unpooled
ME <- zstar * SE
c(diff = p1 - p2, lower = (p1 - p2) - ME, upper = (p1 - p2) + ME)
```

A shortcut that computes $\hat{p}$ for every group at once:

```r
tapply(df[["Satisfaction"]] == "Satisfied", df[["Flight Type"]], mean)
```

## Part D: Two-Proportion Hypothesis Test

$$H_0: p_1 = p_2 \qquad \hat{p} = \frac{x_1+x_2}{n_1+n_2} \qquad z = \frac{\hat{p}_1-\hat{p}_2}{\sqrt{\hat{p}(1-\hat{p})\left(\frac{1}{n_1}+\frac{1}{n_2}\right)}}$$

Because $H_0$ says the proportions are equal, the test uses the __pooled__ proportion $\hat{p}$.

```r
new <- df[["Boarding Method"]] == "New"
old <- df[["Boarding Method"]] == "Old"

n1 <- sum(new); x1 <- sum(new & sat)
n2 <- sum(old); x2 <- sum(old & sat)
p1 <- x1 / n1;  p2 <- x2 / n2

pp <- (x1 + x2) / (n1 + n2)                       # pooled proportion
SE <- sqrt(pp * (1 - pp) * (1/n1 + 1/n2))
z <- (p1 - p2) / SE
p_value <- 2 * pnorm(abs(z), lower.tail = FALSE)
c(pooled = pp, z = z, p_value = p_value)

# Check with R's built-in test (X-squared = z^2; same p-value)
prop.test(c(x1, x2), c(n1, n2), correct = FALSE)
```

## Chi-Square Distributions
When a categorical variable has more than two categories, a single proportion no longer tells the whole story. Chi-square tests compare __observed__ counts ($O$) to __expected__ counts ($E$):

$$\chi^2 = \sum \frac{(O-E)^2}{E}$$

Conditions: all expected counts must be at least 5. The p-value is always a __right-tail__ area.

| __Chi-Square Distribution__     | R Command                                         | Excel Equivalent                       |
| :------------------------------ | :------------------------------------------------ | :------------------------------------- |
| p-value from $\chi^2$ and df    | `pchisq(chi_square, df, lower.tail = FALSE)`      | `=CHISQ.DIST.RT(chi_square, df)`       |
| Critical value                  | `qchisq(alpha, df, lower.tail = FALSE)`           | `=CHISQ.INV.RT(alpha, df)`             |
| Goodness-of-fit test            | `chisq.test(O, p = expected_pct)`                 | `=CHISQ.TEST(observed, expected)`      |
| Test of independence            | `chisq.test(tab, correct = FALSE)`                | `=CHISQ.TEST(observed, expected)`      |

Be careful not to name a variable `df` for degrees of freedom, since `df` already holds the data. This sheet uses `dof` instead.

## Part E: Chi-Square Goodness-of-Fit Test
Does one categorical variable follow a claimed distribution?

$$E = n \times (\text{hypothesized proportion}) \qquad df = k - 1$$

where $k$ is the number of categories.

```r
order <- c("Economy", "Premium Economy", "Business", "First")
O <- table(factor(df[["Seat Class"]], levels = order))   # keep categories in order
expected_pct <- c(0.55, 0.20, 0.15, 0.10)
E <- sum(O) * expected_pct

contrib <- (O - E)^2 / E
chi_square <- sum(contrib)
dof <- length(order) - 1
p_value <- pchisq(chi_square, dof, lower.tail = FALSE)

data.frame(Observed = as.vector(O), Expected = E, Contribution = as.vector(contrib), row.names = order)
c(chi_square = chi_square, dof = dof, p_value = p_value)

# Check with R's built-in test
chisq.test(O, p = expected_pct)
```

`table()` sorts categories alphabetically, so `factor(..., levels = order)` makes sure the observed counts line up with the expected percentages.

## Part F: Chi-Square Test of Independence
Are two categorical variables associated?

$$E = \frac{(\text{row total})(\text{column total})}{\text{grand total}} \qquad df = (r-1)(c-1)$$

```r
tab <- table(factor(df[["Seat Class"]], levels = order), df[["Satisfaction"]])
addmargins(tab)

# Conditional (row) percentages
prop.table(tab, margin = 1)

# By hand: expected counts, statistic, df, p-value
E <- outer(rowSums(tab), colSums(tab)) / sum(tab)
chi_square <- sum((tab - E)^2 / E)
dof <- (nrow(tab) - 1) * (ncol(tab) - 1)
p_value <- pchisq(chi_square, dof, lower.tail = FALSE)
c(chi_square = chi_square, dof = dof, p_value = p_value)

# Check with R's built-in test
result <- chisq.test(tab, correct = FALSE)
result
result$expected
```

| __Test of Independence__        | R Command                                                              |
| :------------------------------ | :--------------------------------------------------------------------- |
| Observed table                  | `table(df[["Seat Class"]], df[["Satisfaction"]])`                       |
| Table with totals               | `addmargins(tab)`                                                       |
| Conditional (row) percentages   | `prop.table(tab, margin = 1)`                                           |
| Expected counts                 | `outer(rowSums(tab), colSums(tab)) / sum(tab)`                          |
| Full test                       | `chisq.test(tab, correct = FALSE)`                                      |
| Expected counts from the test   | `chisq.test(tab)$expected`                                              |

`correct = FALSE` turns off the Yates continuity correction. It only matters for 2×2 tables, but including it makes `chisq.test` match the hand calculation every time.

## Which Procedure Do I Use?

| __Question involves...__                               | Procedure                        | Lab Part |
| :----------------------------------------------------- | :------------------------------- | :------- |
| Estimating one proportion                              | One-proportion z-interval        | A        |
| Testing one proportion against a claimed value         | One-proportion z-test            | B        |
| Estimating the difference between two proportions      | Two-proportion z-interval        | C        |
| Testing whether two proportions are equal              | Two-proportion z-test            | D        |
| One variable with 3+ categories vs. a claimed distribution | Chi-square goodness-of-fit   | E        |
| Association between two categorical variables          | Chi-square test of independence  | F        |
