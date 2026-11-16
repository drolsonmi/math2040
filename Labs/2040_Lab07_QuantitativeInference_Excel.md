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
<title>Lab: Quantitative Inference (Excel)</title>
</head>

# Lab: Quantitative Inference (Excel)
In this lab, you are a statistical consultant for an airline studying the timing of its ground operations. Every part of the lab uses the same dataset of 160 departing flights, found on the __Data__ sheet (rows 2–161).

| __Variable__            | Values                                   | Column on Data sheet |
| :---------------------- | :--------------------------------------- | :------------------- |
| Hub                     | Salt Lake City, Denver, Phoenix, Seattle | B                    |
| Boarding Method         | Old, New                                 | C                    |
| Taxi-Out Time (min)     | Quantitative                             | D                    |
| Boarding Time (min)     | Quantitative                             | E                    |
| Turnaround Time (min)   | Quantitative                             | F                    |

Every procedure in this lab has the same shape:
- A __confidence interval__ is $\text{estimate} \pm (\text{critical value})(\text{standard error})$.
- A __test statistic__ is $\dfrac{\text{estimate} - \text{null value}}{\text{standard error}}$. A small p-value (less than $\alpha = 0.05$) means we reject $H_0$.

__z or t?__ Use $z$ only when the population standard deviation $\sigma$ is given. When you calculate the sample standard deviation $s$ from the data, use $t$.

## Summary Statistics with Excel

| __Summary Statistics__                    | Excel Command                                                     |
| :---------------------------------------- | :---------------------------------------------------------------- |
| Sample size $n$                           | `=COUNT(Data!D2:D161)`                                            |
| Sample mean $\bar{x}$                     | `=AVERAGE(Data!D2:D161)`                                          |
| Sample standard deviation $s$             | `=STDEV.S(Data!D2:D161)`                                          |
| Size of one group                         | `=COUNTIF(Data!C2:C161, "New")`                                   |
| Mean of one group                         | `=AVERAGEIF(Data!C2:C161, "New", Data!E2:E161)`                   |
| Standard deviation of one group           | `=STDEV.S(IF(Data!C2:C161="New", Data!E2:E161))`                  |
| Square root                               | `=SQRT(number)`                                                   |
| Sum of squared deviations from the mean   | `=DEVSQ(range)`                                                   |

Excel has no `STDEVIF` function, so `STDEV.S(IF(...))` keeps only the values in one group. Excel 365 accepts it as typed. In older versions of Excel, finish the formula with __Ctrl+Shift+Enter__ instead of Enter.

## The Standard Normal Distribution (σ known)

| __Standard Normal__                         | Excel Command                              |
| :------------------------------------------ | :----------------------------------------- |
| Critical value $z^*$ for confidence $C$     | `=NORM.S.INV(1-(1-C)/2)`                   |
| $z^*$ for 95% confidence                    | `=NORM.S.INV(0.975)` (gives 1.96)          |
| Left-tail probability $P(Z \le z)$          | `=NORM.S.DIST(z, TRUE)`                    |
| Two-sided p-value                           | `=2*(1-NORM.S.DIST(ABS(z), TRUE))`         |
| One-sided p-value ($H_a$: $<$)              | `=NORM.S.DIST(z, TRUE)`                    |
| One-sided p-value ($H_a$: $>$)              | `=1-NORM.S.DIST(z, TRUE)`                  |
| Margin of error (check)                     | `=CONFIDENCE.NORM(alpha, sigma, n)`        |

## Part A: One-Sample z-Interval

$$\bar{x} \pm z^* \frac{\sigma}{\sqrt{n}}$$

Conditions: random sample, and the population is normal or $n \ge 30$.

| __One-Sample z-Interval__    | Excel Command                          |
| :--------------------------- | :------------------------------------- |
| Standard error               | `=sigma/SQRT(n)`                       |
| Margin of error              | `=zstar*SE`                            |
| Check the margin of error    | `=CONFIDENCE.NORM(1-C, sigma, n)`      |
| Lower bound                  | `=xbar-ME`                             |
| Upper bound                  | `=xbar+ME`                             |

## Part B: One-Sample z-Test

$$H_0: \mu = \mu_0 \qquad z = \frac{\bar{x}-\mu_0}{\sigma/\sqrt{n}}$$

| __One-Sample z-Test__        | Excel Command                              |
| :--------------------------- | :----------------------------------------- |
| Standard error               | `=sigma/SQRT(n)`                           |
| Test statistic               | `=(xbar-mu0)/SE`                           |
| Two-sided p-value            | `=2*(1-NORM.S.DIST(ABS(z), TRUE))`         |

## The t Distribution (σ unknown)
The $t$ distribution looks like the standard normal but has heavier tails, which accounts for the extra uncertainty from estimating $\sigma$ with $s$. Its shape depends on the __degrees of freedom__; for one sample, $df = n-1$.

| __t Distribution__                          | Excel Command                              |
| :------------------------------------------ | :----------------------------------------- |
| Critical value $t^*$ for confidence $C$     | `=T.INV.2T(1-C, df)`                       |
| $t^*$ for 95% confidence, $df = 44$         | `=T.INV.2T(0.05, 44)` (gives 2.015)        |
| Two-sided p-value                           | `=T.DIST.2T(ABS(t), df)`                   |
| One-sided p-value ($H_a$: $<$)              | `=T.DIST(t, df, TRUE)`                     |
| One-sided p-value ($H_a$: $>$)              | `=T.DIST.RT(t, df)`                        |
| Margin of error (check)                     | `=CONFIDENCE.T(alpha, s, n)`               |

Two common mistakes: `T.INV.2T` takes the total area in __both__ tails ($1-C$, such as 0.05), not 0.975; and `T.DIST.2T` returns an error for a negative $t$, so wrap $t$ in `ABS()`.

## Part C: One-Sample t-Interval

$$\bar{x} \pm t^* \frac{s}{\sqrt{n}} \qquad df = n-1$$

Conditions: random sample, and the population is normal or $n \ge 30$ (with small samples, no strong skew or outliers).

| __One-Sample t-Interval__    | Excel Command                                          |
| :--------------------------- | :----------------------------------------------------- |
| Group size                   | `=COUNTIF(Data!C2:C161, "New")`                        |
| Group mean                   | `=AVERAGEIF(Data!C2:C161, "New", Data!E2:E161)`        |
| Group standard deviation     | `=STDEV.S(IF(Data!C2:C161="New", Data!E2:E161))`       |
| Standard error               | `=s/SQRT(n)`                                           |
| Critical value               | `=T.INV.2T(1-C, n-1)`                                  |
| Margin of error              | `=tstar*SE`                                            |
| Check the margin of error    | `=CONFIDENCE.T(1-C, s, n)`                             |

## Part D: One-Sample t-Test

$$H_0: \mu = \mu_0 \qquad t = \frac{\bar{x}-\mu_0}{s/\sqrt{n}} \qquad df = n-1$$

| __One-Sample t-Test__        | Excel Command                              |
| :--------------------------- | :----------------------------------------- |
| Test statistic               | `=(xbar-mu0)/(s/SQRT(n))`                  |
| p-value, $H_a: \mu < \mu_0$  | `=T.DIST(t, df, TRUE)`                     |
| p-value, $H_a: \mu > \mu_0$  | `=T.DIST.RT(t, df)`                        |
| p-value, $H_a: \mu \ne \mu_0$| `=T.DIST.2T(ABS(t), df)`                   |

## Part E: Two-Sample t-Interval

$$(\bar{x}_1-\bar{x}_2) \pm t^* \sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}$$

The degrees of freedom come from the Welch formula. Let $a = s_1^2/n_1$ and $b = s_2^2/n_2$:

$$df = \frac{(a+b)^2}{\frac{a^2}{n_1-1}+\frac{b^2}{n_2-1}}$$

A conservative (smaller) alternative is $df = \min(n_1-1,\; n_2-1)$.

Conditions: independent random samples, and each population is normal or each $n \ge 30$. If the interval contains 0, there may be no difference between the group means.

| __Two-Sample t-Interval__    | Excel Command                                          |
| :--------------------------- | :----------------------------------------------------- |
| Difference in means          | `=xbar1-xbar2`                                         |
| Standard error               | `=SQRT(s1^2/n1 + s2^2/n2)`                             |
| Welch degrees of freedom     | `=(a+b)^2/(a^2/(n1-1)+b^2/(n2-1))`                     |
| Conservative df              | `=MIN(n1-1, n2-1)`                                     |
| Critical value               | `=T.INV.2T(1-C, df)`                                   |
| Lower / upper bounds         | `=(xbar1-xbar2)-tstar*SE` and `=(xbar1-xbar2)+tstar*SE`|

## Part F: Two-Sample t-Test

$$H_0: \mu_1 = \mu_2 \qquad t = \frac{\bar{x}_1-\bar{x}_2}{\sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}}$$

| __Two-Sample t-Test__        | Excel Command                                                          |
| :--------------------------- | :--------------------------------------------------------------------- |
| Test statistic               | `=(xbar1-xbar2)/SE`                                                    |
| Two-sided p-value            | `=T.DIST.2T(ABS(t), df)`                                               |
| p-value directly from data   | `=T.TEST(IF(Data!C2:C161="New",Data!E2:E161), IF(Data!C2:C161="Old",Data!E2:E161), 2, 3)` |

In `T.TEST(array1, array2, tails, type)`, `tails` is 1 or 2 and `type` 3 means unequal variances (Welch). Excel uses the exact Welch df, so the result should match your hand calculation when you also use the Welch df.

## The F Distribution
ANOVA compares the variability __between__ group means to the variability __within__ groups. The F statistic is a ratio of the two, and the p-value is always a __right-tail__ area.

| __F Distribution__              | Excel Command                                   |
| :------------------------------ | :---------------------------------------------- |
| p-value                         | `=F.DIST.RT(F, df1, df2)`                       |
| Critical value                  | `=F.INV.RT(alpha, df1, df2)`                    |

## Part G: One-Way ANOVA
Do the means of $k$ groups differ? With $N$ total observations and grand mean $\bar{x}$:

$$H_0: \mu_1 = \mu_2 = \dots = \mu_k \qquad H_a: \text{at least one mean is different}$$

$$SSG = \sum n_i(\bar{x}_i-\bar{x})^2 \qquad SSE = \sum (n_i-1)s_i^2 \qquad F = \frac{SSG/(k-1)}{SSE/(N-k)}$$

| __Source__   | df      | SS    | MS                  | F             |
| :----------- | :------ | :---- | :------------------ | :------------ |
| Groups       | $k-1$   | SSG   | $MSG = SSG/(k-1)$   | $MSG/MSE$     |
| Error        | $N-k$   | SSE   | $MSE = SSE/(N-k)$   |               |
| Total        | $N-1$   | SST   |                     |               |

Conditions: independent random samples, each group roughly normal (or large), and similar spreads: $\dfrac{\text{largest } s}{\text{smallest } s} < 2$.

| __One-Way ANOVA__               | Excel Command                                                 |
| :------------------------------ | :------------------------------------------------------------ |
| Group size                      | `=COUNTIF(Data!B2:B161, "Denver")`                            |
| Group mean                      | `=AVERAGEIF(Data!B2:B161, "Denver", Data!F2:F161)`            |
| Group standard deviation        | `=STDEV.S(IF(Data!B2:B161="Denver", Data!F2:F161))`           |
| Grand mean                      | `=AVERAGE(Data!F2:F161)`                                      |
| One group’s piece of SSG        | `=n*(mean-$B$20)^2` (lock the grand mean cell)                |
| One group’s piece of SSE        | `=(n-1)*s^2`                                                  |
| SSG in one step                 | `=SUMPRODUCT(n_range, (mean_range-grand_mean)^2)`             |
| SSE in one step                 | `=SUMPRODUCT(n_range-1, sd_range^2)`                          |
| SST (check: SSG + SSE)          | `=DEVSQ(Data!F2:F161)`                                        |
| Equal-spread check              | `=MAX(sd_range)/MIN(sd_range)`                                |
| p-value                         | `=F.DIST.RT(F, k-1, N-k)`                                     |

On the Part G sheet, the grand mean is in cell B20, which is why the example locks `$B$20`. ANOVA only tells you that __at least one__ mean differs; compare the group means to describe which hubs stand out.

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
