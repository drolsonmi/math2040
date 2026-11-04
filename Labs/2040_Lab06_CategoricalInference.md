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
<title>Lab: Categorical Inference (Excel)</title>
</head>

# Lab: Categorical Inference (Excel)
In this lab, you are going to assume the role of a statistical consultant for an airline that is testing a new boarding process. The goal of this lab will be to perform a statistical inference to explore the data.

Remember the two kinds of inference:
- A __confidence interval__ *estimates* a parameter: $\text{estimate} \pm \text{margin of error}$
- A __hypothesis test__ asks whether the data give *evidence against* a claim ($H_0$). A small p-value (less than $\alpha = 0.05$) means we reject $H_0$.
    - __Chi-squared tests__ are like hypothesis tests but consider multiple categories for a single variable

## Counting with Excel
Everything in categorical inference starts with counting. The data have 400 rows (rows 2–401).

| __Counting__                              | Excel Command                                                     |
| :---------------------------------------- | :---------------------------------------------------------------- |
| Sample size $n$                           | `=COUNTA(Data!F2:F401)`                                           |
| Number of successes $x$                   | `=COUNTIF(Data!F2:F401, "Satisfied")`                             |
| Count in one group                        | `=COUNTIF(Data!C2:C401, "Domestic")`                              |
| Count matching two conditions             | `=COUNTIFS(Data!C2:C401, "Domestic", Data!F2:F401, "Satisfied")`  |
| Sample proportion $\hat{p} = x/n$         | `=x/n`                                                            |
| Square root                               | `=SQRT(number)`                                                   |
| Absolute value                            | `=ABS(number)`                                                    |

The text in quotes must match the data exactly, including spaces (for example, `"Premium Economy"`).

## The Standard Normal Distribution
Proportion procedures use $z$. Two Excel functions do almost all the work:

| __Standard Normal__                         | Excel Command                              |
| :------------------------------------------ | :----------------------------------------- |
| Critical value $z^*$ for confidence $C$     | `=NORM.S.INV(1-(1-C)/2)`                   |
| $z^*$ for 95% confidence                    | `=NORM.S.INV(0.975)` (gives 1.96)          |
| Left-tail probability $P(Z \le z)$          | `=NORM.S.DIST(z, TRUE)`                    |
| Two-sided p-value                           | `=2*(1-NORM.S.DIST(ABS(z), TRUE))`         |
| One-sided p-value ($H_a$: $>$)              | `=1-NORM.S.DIST(z, TRUE)`                  |
| One-sided p-value ($H_a$: $<$)              | `=NORM.S.DIST(z, TRUE)`                    |

- *Note*: The "TRUE" references in the command tell Excel that you are working with *cumulative probabilities*.

## Part A: One-Proportion Confidence Interval

$$\hat{p} \pm z^* \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$

Conditions: $n\hat{p} \ge 10$ and $n(1-\hat{p}) \ge 10$.

| __One-Proportion CI__        | Excel Command                          |
| :--------------------------- | :------------------------------------- |
| Standard error               | `=SQRT(phat*(1-phat)/n)`               |
| Margin of error              | `=zstar*SE`                            |
| Lower bound                  | `=phat-ME`                             |
| Upper bound                  | `=phat+ME`                             |

## Part B: One-Proportion Hypothesis Test

$$H_0: p = p_0 \qquad z = \frac{\hat{p}-p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$$

Conditions: $np_0 \ge 10$ and $n(1-p_0) \ge 10$. Notice the standard error uses $p_0$, not $\hat{p}$.

| __One-Proportion z-Test__    | Excel Command                              |
| :--------------------------- | :----------------------------------------- |
| Standard error under $H_0$   | `=SQRT(p0*(1-p0)/n)`                       |
| Test statistic               | `=(phat-p0)/SE`                            |
| Two-sided p-value            | `=2*(1-NORM.S.DIST(ABS(z), TRUE))`         |

## Part C: Two-Proportion Confidence Interval

$$(\hat{p}_1-\hat{p}_2) \pm z^* \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}+\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$$

Conditions: at least 10 successes and 10 failures in __each__ group. If the interval contains 0, there may be no difference between the groups.

| __Two-Proportion CI__        | Excel Command                                          |
| :--------------------------- | :----------------------------------------------------- |
| Proportion in group 1        | `=x1/n1`                                               |
| Difference                   | `=p1-p2`                                               |
| Standard error (unpooled)    | `=SQRT(p1*(1-p1)/n1 + p2*(1-p2)/n2)`                   |
| Lower / upper bounds         | `=(p1-p2)-zstar*SE` and `=(p1-p2)+zstar*SE`            |

## Part D: Two-Proportion Hypothesis Test

$$H_0: p_1 = p_2 \qquad \hat{p} = \frac{x_1+x_2}{n_1+n_2} \qquad z = \frac{\hat{p}_1-\hat{p}_2}{\sqrt{\hat{p}(1-\hat{p})\left(\frac{1}{n_1}+\frac{1}{n_2}\right)}}$$

Because $H_0$ says the proportions are equal, the test uses the __pooled__ proportion $\hat{p}$.

| __Two-Proportion z-Test__    | Excel Command                                          |
| :--------------------------- | :----------------------------------------------------- |
| Pooled proportion            | `=(x1+x2)/(n1+n2)`                                     |
| Standard error (pooled)      | `=SQRT(pp*(1-pp)*(1/n1+1/n2))`                         |
| Test statistic               | `=(p1-p2)/SE`                                          |
| Two-sided p-value            | `=2*(1-NORM.S.DIST(ABS(z), TRUE))`                     |

## Chi-Square Distributions
When a categorical variable has more than two categories, a single proportion no longer tells the whole story. Chi-square tests compare __observed__ counts ($O$) to __expected__ counts ($E$):

$$\chi^2 = \sum \frac{(O-E)^2}{E}$$

Conditions: all expected counts must be at least 5. The p-value is always a __right-tail__ area.

| __Chi-Square Distribution__     | Excel Command                                   |
| :------------------------------ | :---------------------------------------------- |
| p-value from $\chi^2$ and df    | `=CHISQ.DIST.RT(chi_square, df)`                |
| p-value directly from tables    | `=CHISQ.TEST(observed_range, expected_range)`   |
| Critical value                  | `=CHISQ.INV.RT(alpha, df)`                      |

## Part E: Chi-Square Goodness-of-Fit Test
Does one categorical variable follow a claimed distribution?

$$E = n \times (\text{hypothesized proportion}) \qquad df = k - 1$$

where $k$ is the number of categories.

| __Goodness-of-Fit__             | Excel Command                                   |
| :------------------------------ | :---------------------------------------------- |
| Observed count                  | `=COUNTIF(Data!D2:D401, "Economy")`             |
| Expected count                  | `=$B$18*C14` (n times the expected proportion)  |
| Contribution to $\chi^2$        | `=(O-E)^2/E`                                    |
| $\chi^2$ statistic              | `=SUM(contribution_range)`                      |
| Degrees of freedom              | `=k-1`                                          |
| p-value                         | `=CHISQ.DIST.RT(chi_square, df)`                |

On the Part E sheet, the Economy row is row 14 and the total $n$ is in cell B18. Use the dollar signs (`$B$18`) to lock the cell for $n$ so you can copy the expected-count formula down the column.

## Part F: Chi-Square Test of Independence
Are two categorical variables associated?

$$E = \frac{(\text{row total})(\text{column total})}{\text{grand total}} \qquad df = (r-1)(c-1)$$

| __Test of Independence__        | Excel Command                                                         |
| :------------------------------ | :-------------------------------------------------------------------- |
| Observed cell count             | `=COUNTIFS(Data!D2:D401, "Economy", Data!F2:F401, "Satisfied")`       |
| Row or column total             | `=SUM(range)`                                                         |
| Conditional (row) percentage    | `=cell/row_total`                                                     |
| Expected cell count             | `=$D14*B$18/$D$18` (row total × column total ÷ grand total)            |
| Contribution to $\chi^2$        | `=(O-E)^2/E`                                                          |
| Degrees of freedom              | `=(r-1)*(c-1)`                                                        |
| p-value                         | `=CHISQ.DIST.RT(chi_square, df)`                                      |
| Check your p-value              | `=CHISQ.TEST(observed_range, expected_range)`                         |

The expected-count example uses the cells of the Step 2 table on the Part F sheet (Economy in row 14, totals in row 18 and column D); if you build your expected table there, you can reference those cells directly. Mixed references like `$D14` (column locked) and `B$18` (row locked) let one formula fill the whole expected table.

## Which Procedure Do I Use?

| __Question involves...__                               | Procedure                        | Lab Part |
| :----------------------------------------------------- | :------------------------------- | :------- |
| Estimating one proportion                              | One-proportion z-interval        | A        |
| Testing one proportion against a claimed value         | One-proportion z-test            | B        |
| Estimating the difference between two proportions      | Two-proportion z-interval        | C        |
| Testing whether two proportions are equal              | Two-proportion z-test            | D        |
| One variable with 3+ categories vs. a claimed distribution | Chi-square goodness-of-fit   | E        |
| Association between two categorical variables          | Chi-square test of independence  | F        |