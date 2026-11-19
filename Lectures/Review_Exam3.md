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
<title>Exam 3 Review</title></head>

# Exam 3 Review

> Following is the material on the front page of the exam:
>
> * You may use a scientific or graphing calculator, one 3x5 handwritten notecard, and a pencil/pen/eraser.
> * A Z-table, t-table, and $\chi^2$-table will be provided. Scratch paper is available from the testing center upon request.
> * You will have 2 hours to complete the exam.
> * Unless otherwise indicated, multiple choice questions are worth 2 points, short answer questions are worth 3 points, and math-based questions are worth 4 points.
> * The exam begins with questions on each topic, followed by a scenario with data for you to analyze.
> * You must show your work to be eligible for partial credit. Questions without work will not receive partial credit.
> * Cheating is unfair to your classmates who have worked hard to prepare. Please do your own work.

-----

## Quick Reference: TI-84 Calculator Commands

| Task | TI-84 Menu / Location | Syntax / Input |
| :--- | :--- | :--- |
| **Critical value $z_c$** | `2nd` → `VARS` (DISTR) → `invNorm` | `invNorm(left_area, 0, 1)` |
| **Critical value $t_c$** | `2nd` → `VARS` (DISTR) → `invT` | `invT(left_area, df)` |
| **t probability** | `2nd` → `VARS` (DISTR) → `tcdf` | `tcdf(lower, upper, df)` |
| **$\chi^2$ probability** | `2nd` → `VARS` (DISTR) → `χ²cdf` | `χ²cdf(χ², 1E99, df)` |
| **F probability** | `2nd` → `VARS` (DISTR) → `Fcdf` | `Fcdf(F, 1E99, df_G, df_E)` |
| **2-proportion CI** | `STAT` → `TESTS` → `2-PropZInt` | $x_1, n_1, x_2, n_2$, C-Level |
| **2-proportion test** | `STAT` → `TESTS` → `2-PropZTest` | $x_1, n_1, x_2, n_2$, direction of $H_A$ |
| **$\chi^2$ goodness of fit** | `STAT` → `TESTS` → `D:χ²GOF-Test` | Observed: `L1`, Expected: `L2`, df |
| **$\chi^2$ two-way table** | `STAT` → `TESTS` → `χ²-Test` | Observed: `[A]`, Expected: `[B]` |
| **1-sample mean CI** | `STAT` → `TESTS` → `TInterval` | Data or Stats ($\bar{x}, s, n$), C-Level |
| **1-sample mean test** | `STAT` → `TESTS` → `T-Test` | $\mu_0$, Data or Stats, direction of $H_A$ |
| **2-sample mean CI (non-paired)** | `STAT` → `TESTS` → `2-SampTInt` | Data or Stats, C-Level, Pooled: **No** |
| **2-sample mean test (non-paired)** | `STAT` → `TESTS` → `2-SampTTest` | Data or Stats, direction of $H_A$, Pooled: **No** |
| **ANOVA** | `STAT` → `TESTS` → `ANOVA(` | `ANOVA(L1, L2, L3, ...)` |

> **Note:** For **paired** data, find the differences first (e.g., `L3 = L1 - L2`), then use `TInterval` or `T-Test` on `L3`.
>
> **Note:** The calculator finds $df$ for `2-SampTInt` / `2-SampTTest` with a more precise formula than our conservative rule, so its answers will differ slightly from answers found by hand.
>
> **Desmos:** `chisqdist(df)`, `tdist(df)`, and `normaldist(μ, σ)` graph these distributions and give the area to the right of a value.

---

## Choosing the Right Procedure

| Type of Data | Groups / Variables | Procedure | Test Statistic |
| :--- | :--- | :--- | :--- |
| Categorical (success/failure) | 2 samples | 2-sample proportion CI / test | $z$ |
| Categorical (several categories) | 1 variable vs. an expected distribution | $\chi^2$ goodness of fit | $\chi^2$ |
| Categorical | 2 variables (two-way table) | $\chi^2$ test of independence | $\chi^2$ |
| Quantitative | 1 sample | 1-sample mean CI / test | $t$ |
| Quantitative | 2 **paired** samples | 1-sample $t$ on the differences | $t$ |
| Quantitative | 2 **non-paired** samples | 2-sample mean CI / test | $t$ |
| Quantitative | 3 or more categories | ANOVA | $F$ |

---

## Topic 1: Confidence Intervals for 2-Sample Categorical Data

Steps for creating a Confidence Interval (same steps as 1 sample; only the Standard Error changes)
1. Verify CLT is satisfied (random, large enough)
2. Determine the confidence level and critical value $z_c$
3. Find the Standard Error
4. Find the Margin of Error
5. Find and interpret the interval

### A. Difference of Two Proportions
* We compare two samples by examining the difference $\hat{p}_1 - \hat{p}_2$.
* **When do we use this?**
  * Comparing one population to another
  * Experiments comparing a control group to a treatment group

#### Conditions (CLT must hold for **both** samples)
* Random, independent samples
* Large enough (at least 10 successes and 10 failures in each sample):
  $$x_1 = n_1\hat{p}_1 \ge 10 \qquad x^C_1 = n_1 - x_1 \ge 10$$
  $$x_2 = n_2\hat{p}_2 \ge 10 \qquad x^C_2 = n_2 - x_2 \ge 10$$

### B. Formulas
* **Standard Error:**
  $$SE = \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}+\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$$
* **Margin of Error:**
  $$ME = z_c \cdot SE$$
* **Confidence Interval:**
  $$(\hat{p}_1-\hat{p}_2) \pm z_c \cdot SE$$
* **Common critical values:** $z_c = 1.645$ (90%), $1.960$ (95%), $2.576$ (99%)

### C. Interpretation
* "We are 90% confident that the true difference in proportions between ___ and ___ is between ___ and ___."
* **If the interval contains 0**, there may be no difference between the two proportions.

> **Example (Election):** Utah $n_1 = 260$, $\hat{p}_1 = 0.594$; Texas $n_2 = 425$, $\hat{p}_2 = 0.561$; 90% confidence.
> $SE = 0.03882$, $ME = 1.645(0.03882) = 0.06386$, interval: $0.033 \pm 0.06386 = (-0.031, 0.097)$.
> Since the interval contains 0, we can't say the proportions differ.

### D. TI-84 Command
* `STAT` → `TESTS` → `2-PropZInt`
* **Inputs:** $x_1$, $n_1$, $x_2$, $n_2$, C-Level

---

## Topic 2: Hypothesis Testing for 2-Sample Categorical Data

Steps for completing a Hypothesis Test
1. Verify CLT is satisfied
2. Identify the null and alternative hypotheses
3. Determine the level of significance $\alpha$
4. Find the Standard Error (pooled)
5. Find the test statistic and/or the p-value (or use a confidence interval)
6. State your conclusion

### A. Hypotheses Setup
* **Null Hypothesis:** $H_0: \; p_1 - p_2 = 0$
* **Alternative Hypothesis** (one of three):
  * Left-tailed: $H_A: \; p_1 - p_2 < 0$
  * Right-tailed: $H_A: \; p_1 - p_2 > 0$
  * Two-tailed: $H_A: \; p_1 - p_2 \ne 0$

### B. Pooled Proportion
* Under $H_0$, the two samples are treated as coming from the **same population**, so we combine them for a better estimate of $p$:
  $$\hat{p}_{pooled} = \frac{\text{Total number of successes in both samples}}{\text{Total of both sample sizes}} = \frac{x_1 + x_2}{n_1 + n_2} = \frac{n_1\hat{p}_1 + n_2\hat{p}_2}{n_1 + n_2}$$
* **Pooled Standard Error:**
  $$SE = \sqrt{\frac{\hat{p}_{pooled}(1-\hat{p}_{pooled})}{n_1} + \frac{\hat{p}_{pooled}(1-\hat{p}_{pooled})}{n_2}} = \sqrt{\hat{p}_{pooled}(1-\hat{p}_{pooled})\left(\frac{1}{n_1} + \frac{1}{n_2}\right)}$$

> **Important:** In 1-sample tests, we used the null value $p_0$ to find the SE. In 2-sample tests, we use $\hat{p}_{pooled}$. The **confidence interval** still uses $\hat{p}_1$ and $\hat{p}_2$ separately.

### C. Test Statistic ($z$)
$$z = \frac{(\hat{p}_1 - \hat{p}_2) - 0}{SE}$$

### D. Decision Rule (p-value approach)
* **P-value by test type** (for test statistic $z$):
  * Left-tailed: $P(Z < z)$
  * Right-tailed: $P(Z > z)$
  * Two-tailed: $2 \cdot P(Z > |z|)$
* **Decision:**
  * If p-value $\le \alpha$: **Reject $H_0$**. There is enough evidence to suggest $H_A$.
  * If p-value $> \alpha$: **Fail to reject $H_0$**. There is not enough evidence to suggest $H_A$.

### E. TI-84 Command
* `STAT` → `TESTS` → `2-PropZTest`
* **Inputs:** $x_1$, $n_1$, $x_2$, $n_2$, and the direction of $H_A$

---

## Topic 3: Chi-Squared ($\chi^2$) Testing

### A. Uses of the $\chi^2$ Test
* Determine whether a sample is representative of the general population when the sample falls into several groups (**goodness of fit**)
* Evaluate whether two variables are independent (**two-way tables**)
* Evaluate whether data resemble a particular distribution (normal, binomial, geometric, ...)

### B. The $\chi^2$ Test Statistic
* Built from z-scores. Squaring removes negatives and makes large differences stand out:
  $$\chi^2 = Z_1^2 + Z_2^2 + Z_3^2 + \cdots$$
* **Count-based formula:**
  $$\chi^2 = \sum \frac{(\text{observed count} - \text{expected count})^2}{\text{expected count}} = \sum \frac{(x - E[x])^2}{E[x]}$$
* The textbook calls the expected count the **null count**.

### C. The $\chi^2$ Distribution and Degrees of Freedom
* The $\chi^2$ distribution has **one** parameter: degrees of freedom ($df$). (The normal distribution has two: $\mu$ and $\sigma$.)
* **Degrees of freedom:** the minimum number of values that can vary freely.
* $\chi^2$ is always positive, so the test is **right-tailed**:
  $$\text{p-value} = P(\chi^2 > \text{test statistic})$$

#### Conditions
1. **Independence:** each case contributing to the table must be independent of all other cases (random sample).
2. **Sample size:** each cell must have at least **5 expected** cases.

### D. Goodness of Fit (1 Variable)

#### Hypotheses
* $H_0$: The counts follow the expected (claimed) distribution
* $H_A$: The counts do not follow the expected distribution

#### Formulas
* **Expected count:** $E[x] = n \cdot P(x)$ (sample size × claimed proportion)
* **Degrees of freedom:**
  $$df = k - 1 \qquad (k = \text{number of categories})$$

> **Example (M&M's):** Claimed: Brown 0.30, Yellow 0.20, Red 0.20, Orange 0.10, Green 0.10, Blue 0.10. Sample of 250.
>
> | Color | Brown | Yellow | Red | Orange | Green | Blue |
> | :---: | :---: | :----: | :-: | :----: | :---: | :--: |
> | Observed | 69 | 51 | 47 | 22 | 26 | 35 |
> | Expected | 75 | 50 | 50 | 25 | 25 | 25 |
> | $(x-E[x])^2 / E[x]$ | 0.48 | 0.02 | 0.18 | 0.36 | 0.04 | 4 |
>
> $\chi^2 = 5.08$, $df = 6 - 1 = 5$, p-value $= P(\chi^2 > 5.08) = 0.406 > \alpha$ → Fail to reject $H_0$. The colors appear to match the advertised distribution.

#### TI-84 Commands
* Enter observed counts in `L1` and **expected counts** (not proportions) in `L2`
* `STAT` → `TESTS` → `D:χ²GOF-Test` → Observed: `L1`, Expected: `L2`, df: $k-1$

### E. Independence in Two-Way Tables (2 Variables)

#### Hypotheses
* $H_0$: The two variables are independent (the counts match the expected counts; the proportion is the same across all categories)
* $H_A$: The two variables are not independent (the proportion is not consistent across categories)

#### Formulas
* **Expected count** for each cell (row proportion × column total):
  $$E[x] = \frac{\text{row total}}{\text{table total}} \times \text{column total} = \frac{(\text{row total})(\text{column total})}{\text{table total}}$$
* **Degrees of freedom:**
  $$df = (\text{\# of rows} - 1)(\text{\# of columns} - 1)$$
  (do **not** count the "Total" row or column)

> **Example (MATH 1025 pass/fail by modality):** 63 of 72 passed, so the pass proportion is $63/72 = 0.875$.
> Expected passing in-person: $0.875 \times 27 = 23.625$, and so on for each cell.
> $\chi^2 = 0.44191$, $df = (2-1)(3-1) = 2$, p-value $= 0.802 > 0.10$ → Fail to reject $H_0$. About 87.5% of students pass regardless of modality.

#### TI-84 Commands
* Enter the observed table in matrix `[A]`: `2nd` → `x⁻¹` (MATRIX) → `EDIT` → `[A]`, dimensions rows × columns
* `STAT` → `TESTS` → `χ²-Test` → Observed: `[A]`, Expected: `[B]`
* The calculator stores the expected counts in `[B]`. Check that each is at least 5.

### F. Checking Whether Data Fit a Distribution
* To check whether data are normally distributed:
  1. Find the sample percentiles of the data (20th, 25th, 30th, ...)
  2. Find the expected value of each percentile under a normal distribution: find the z-score for that percentile, then $x = z \cdot s + \bar{x}$
  3. Compute $\chi^2 = \sum \frac{(x - E[x])^2}{E[x]}$ and its p-value
* A very small p-value means the data do **not** fit the distribution.

---

## Topic 4: CLT for Sample Means and the t-Distribution

### A. CLT for Quantitative Variables
* The sampling distribution of $\bar{x}$:
  $$\mu_{\bar{x}} = \mu \qquad \sigma_{\bar{x}} = SE_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$$
* **Standardizing** a single value vs. a sample mean:
  $$z = \frac{x - \mu}{\sigma} \qquad z = \frac{\bar{x} - \mu}{SE}$$

> **Tip:** Think logically before calculating. A sample mean (e.g., over 45 days) is much **less** likely to be far from $\mu$ than a single value (one day).

#### Conditions
* **Independence:** the data are random
* **Large enough:** as a general rule, $n \ge 30$ (smaller samples are okay if the population is normal with no clear outliers)

### B. The t-Distribution
* We rarely know $\sigma$, so we estimate it with the sample standard deviation $s$:
  $$SE = \frac{\sigma}{\sqrt{n}} \approx \frac{s}{\sqrt{n}}$$
* Using $s$ adds uncertainty, so we use the **t-distribution** instead of the normal distribution.
* **Properties:**
  * Bell-shaped, symmetric, centered at 0
  * Thicker tails than the normal distribution
  * One parameter: degrees of freedom, $df = n - 1$
  * As $df$ increases, the t-distribution approaches the standard normal

#### TI-84 Commands
* **Probability:** `tcdf(lower, upper, df)`
  * Left-tailed: `tcdf(-1E99, t, df)`
  * Right-tailed: `tcdf(t, 1E99, df)`
  * Two-tailed: `2 * tcdf(|t|, 1E99, df)`
* **Critical value $t_c$:** for a C% confidence interval, `invT((1 + C)/2, df)`. For example, 95% with $df = 7$: `invT(0.975, 7)` $= 2.365$

---

## Topic 5: Confidence Intervals for 1-Sample Quantitative Data

Steps for creating a Confidence Interval
1. Verify CLT is satisfied (random, large enough)
2. Determine the confidence level and critical value $t_c$ (with $df = n - 1$)
3. Find the Standard Error
4. Find the Margin of Error
5. Find and interpret the interval

### A. Formulas
$$SE = \frac{s}{\sqrt{n}} \qquad ME = t_c \cdot SE \qquad \bar{x} \pm ME$$

### B. Interpretation
* "We are 95% confident that the true average ___ is between ___ and ___."

### C. TI-84 Command
* `STAT` → `TESTS` → `TInterval`
* **Inputs:** Data (list) **or** Stats ($\bar{x}$, $S_x$, $n$), C-Level

---

## Topic 6: Hypothesis Testing for 1-Sample Quantitative Data

Steps for completing a Hypothesis Test
1. Verify CLT is satisfied
2. State $H_0$ and $H_A$
3. Determine the level of significance $\alpha$
4. Find the test statistic $t$ and the p-value
5. State your conclusion

### A. Hypotheses Setup
* **Null Hypothesis:** $H_0: \mu = \mu_0$
* **Alternative Hypothesis:** $H_A: \mu < \mu_0$, $\mu > \mu_0$, or $\mu \ne \mu_0$

### B. Test Statistic ($t$)
$$t = \frac{\bar{x} - \mu_0}{SE} = \frac{\bar{x} - \mu_0}{s / \sqrt{n}} \qquad df = n - 1$$

### C. Decision Rule (p-value approach)
* **P-value by test type:**
  * Left-tailed: $P(t < \text{observed } t)$
  * Right-tailed: $P(t > \text{observed } t)$
  * Two-tailed: $2 \cdot P(t > |\text{observed } t|)$
* **Decision:**
  * If p-value $\le \alpha$: **Reject $H_0$**. "There is enough evidence to say, with a ___ level of significance, that ___."
  * If p-value $> \alpha$: **Fail to reject $H_0$**. "There is not enough evidence to say ___."

### D. TI-84 Command
* `STAT` → `TESTS` → `T-Test`
* **Inputs:** $\mu_0$, Data (list) **or** Stats ($\bar{x}$, $S_x$, $n$), direction of $H_A$

---

## Topic 7: Inference with 2 Quantitative Samples — Paired Samples

### A. Paired vs. Non-Paired
* **Paired (dependent):** each observation in one sample is connected to a specific observation in the other.
  * Examples: husband's height vs. wife's height; a child's height at age 1 vs. age 4
* **Non-paired (independent):** there is no connection between specific observations in the two samples.

> **Tip:** Ask, "Does each value in Sample 1 have a specific partner in Sample 2?" If yes, the data are paired.

### B. Method
* Find the difference for each pair, then do a **1-sample** analysis on the differences.
* $\bar{d}$ = mean of the differences, $s_d$ = standard deviation of the differences, $n$ = number of **pairs**

#### Conditions
* CLT is satisfied for the differences (random; large enough or normally distributed)

#### Formulas
* **Standard Error and degrees of freedom:**
  $$SE = \frac{s_d}{\sqrt{n}} = \sqrt{\frac{s_d^2}{n}} \qquad df = n - 1$$
* **Confidence Interval:**
  $$ME = t_c \cdot SE \qquad \mu_d = \bar{d} \pm ME$$
* **Hypothesis Test:**
  * $H_0: \mu_d = 0$; $\quad H_A: \mu_d < 0$, $\mu_d > 0$, or $\mu_d \ne 0$
  $$t = \frac{\bar{d} - \mu_0}{SE} \qquad \text{(typically } \mu_0 = 0\text{)}$$
* **Decision:** Reject $H_0$ if the p-value $\le \alpha$ (equivalently, if $t$ is more extreme than $t_c$).

#### TI-84 Commands
* Enter the samples in `L1` and `L2`, then set `L3 = L1 - L2`
* **CI:** `TInterval` with List: `L3`
* **Test:** `T-Test` with $\mu_0 = 0$ and List: `L3`

---

## Topic 8: Inference with 2 Quantitative Samples — Non-Paired Samples

Steps (CI or Hypothesis Test)
1. Verify CLT is satisfied for **both** samples
2. For a CI: determine the confidence level. For a test: state $H_0$ and $H_A$ and the level of significance $\alpha$
3. Find the degrees of freedom and critical value $t_c$
4. Find the Standard Error
5. Find the interval, or the test statistic and p-value
6. Interpret the interval / state your conclusion

### A. Formulas
* **Standard Error:**
  $$SE = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$$
* **Degrees of freedom (conservative):**
  $$df = \min\{n_1 - 1,\ n_2 - 1\}$$
* **Confidence Interval:**
  $$ME = t_c \cdot SE \qquad \mu_1 - \mu_2 = (\bar{x}_1 - \bar{x}_2) \pm ME$$
* **Hypothesis Test:**
  * $H_0: \mu_1 - \mu_2 = 0$; $\quad H_A: \mu_1 - \mu_2 < 0$, $> 0$, or $\ne 0$
  $$t = \frac{(\bar{x}_1 - \bar{x}_2) - \mu_0}{SE} \qquad \text{(typically } \mu_0 = 0\text{)}$$

> **Important:** Square the standard deviations in the SE: $\frac{s_1^2}{n_1}$, not $\frac{s_1}{n_1}$.

### B. Interpretation
* **CI:** "We are 95% confident that the true difference in average ___ is between ___ and ___." If the interval contains 0, there may be no difference.
* **Test:** "There is (not) enough evidence to suggest that ___."

### C. TI-84 Commands
* **CI:** `STAT` → `TESTS` → `2-SampTInt`
* **Test:** `STAT` → `TESTS` → `2-SampTTest`
* **Inputs:** Data (`L1`, `L2`) **or** Stats ($\bar{x}_1$, $S_{x1}$, $n_1$, $\bar{x}_2$, $S_{x2}$, $n_2$); set **Pooled: No**

---

## Topic 9: ANOVA (Analysis of Variance)

### A. What is ANOVA?
* A 2-sample t-test compares the means of **two** groups. ANOVA compares the means of **three or more** categories.
* ANOVA compares the variance **between** categories to the variance **within** each category.
* The **categories** are the independent variable; the **measurement** is the dependent variable.

#### Conditions
* Independence: random samples, independent within and between categories
* Each category is approximately normal
* The categories have roughly equal variance

### B. Hypotheses
* $H_0$: There is no difference between the categories ($\mu_1 = \mu_2 = \mu_3 = \cdots$)
* $H_A$: At least one mean is different than the others

### C. Measurements
* $n$ = total number of observations, $k$ = number of categories, $\bar{x}_i$ = mean of category $i$, $GM$ = grand mean (mean of all data points)
* **Mean Square Error** (variance **within** categories):
  $$MSE = \frac{SS_E}{df_E} = \frac{\sum(x - \bar{x}_i)^2}{df_E} \qquad df_E = n - k$$
* **Mean Square between Groups** (variance **between** categories):
  $$MSG = \frac{SS_G}{df_G} = \frac{\sum n_i(\bar{x}_i - GM)^2}{df_G} \qquad df_G = k - 1$$
* **Test Statistic:**
  $$F = \frac{MSG}{MSE} = \frac{\text{Mean Square between Groups}}{\text{Mean Square Error}}$$

### D. Comparing MSG to MSE
* $F \approx 1$: the variation is mostly random; no real dependence on the categories.
* $F > 1$: more variation between categories than within, which suggests the mean depends on the category.
* How far above 1 $F$ must be depends on the level of significance.
* To reject $H_0$, we want **high variance between** categories and **low variance within** categories.

### E. The ANOVA Table

| Source | $df$ | Sum of Squares | Mean Square | $F$ | p-value |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Groups (Factor) | $k - 1$ | $SS_G$ | $MSG$ | $\frac{MSG}{MSE}$ | $P(F > F_{obs})$ |
| Error | $n - k$ | $SS_E$ | $MSE$ | | |
| Total | $n - 1$ | $SS_G + SS_E$ | | | |

### F. Decision Rule
* ANOVA is **right-tailed**: p-value $= P(F > F_{obs})$
* If p-value $\le \alpha$: **Reject $H_0$**. There is enough evidence to suggest at least one mean is different.
* If p-value $> \alpha$: **Fail to reject $H_0$**. There is not enough evidence to suggest a difference between the categories.

### G. TI-84 Commands
* Enter each category's data in its own list (`L1`, `L2`, `L3`, ...)
* `STAT` → `TESTS` → `ANOVA(` → `ANOVA(L1, L2, L3)`
* **Output:** $F$, p-value, then **Factor** ($df_G$, $SS_G$, $MSG$) and **Error** ($df_E$, $SS_E$, $MSE$)
* **p-value from $F$:** `Fcdf(F, 1E99, df_G, df_E)`