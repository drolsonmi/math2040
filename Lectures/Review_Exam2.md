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
<title>Exam 2 Review</title>
</head>

# Exam 2 Review
Following is the material on the front page of the exam:

> Each student is allowed to bring the following: 
> * a scientific or graphing calculator 
> * a 3x5 notecard with handwritten notes 
> * a pencil/pen/eraser 
> 
> A Z-Table will be provided on the exam. You may ask the testing center for scratch paper if desired.
> 
> You have 2 hours to complete this exam. 
> 
> Unless otherwise indicated, points are awarded as follows: 
> * Multiple choice questions are worth 2 points each.  
> * Short answer questions are worth 3 points each. 
> * Math-based questions are worth 4 points each. 
> 
> This exam begins with a number of questions to test your knowledge of individual topics. You will then be given a scenario and some data for you to analyze. 
> 
> Remember to show your work for partial credit. If no work is shown, your question will not be eligible for partial credit. 
> 
> As you take the exam, remember that its purpose is to show me how well you understand the material. Remember: Cheating is disrespectful to your classmates and other students who studied a great deal.  While we all want to do well there will always be more to life than a single test. And remember that nobody wants to go through surgery under the knife of a surgeon who had to cheat on his exams...

-----

## Quick Reference: TI-84 Calculator Commands

| Task | TI-84 Menu / Location | Syntax / Input |
| :--- | :--- | :--- |
| **Binomial $P(X = k)$** | `2nd` $\to$ `VARS` (DISTR) $\to$ `binompdf` | `binompdf(n, p, k)` |
| **Binomial $P(X \le k)$** | `2nd` $\to$ `VARS` (DISTR) $\to$ `binomcdf` | `binomcdf(n, p, k)` |
| **Geometric $P(X = k)$** | `2nd` $\to$ `VARS` (DISTR) $\to$ `geometpdf` | `geometpdf(p, k)` |
| **Geometric $P(X \le k)$** | `2nd` $\to$ `VARS` (DISTR) $\to$ `geometcdf` | `geometcdf(p, k)` |
| **Poisson $P(X = k)$** | `2nd` $\to$ `VARS` (DISTR) $\to$ `poissonpdf` | `poissonpdf(`$\lambda$`, k)` |
| **Poisson $P(X \le k)$** | `2nd` $\to$ `VARS` (DISTR) $\to$ `poissoncdf` | `poissoncdf(`$\lambda$`, k)` |
| **Normal Probability** | `2nd` $\to$ `VARS` (DISTR) $\to$ `normalcdf` | `normalcdf(lower, upper,` $\mu, \sigma$`)` |
| **Inverse Normal Value** | `2nd` $\to$ `VARS` (DISTR) $\to$ `invNorm` | `invNorm(left_area,` $\mu, \sigma$`)` |
| **1-Sample $p$ Confidence Interval** | `STAT` $\to$ `TESTS` $\to$ `1-PropZInt` | `1-PropZInt(x, n, C-Level)` |
| **1-Sample $p$ Hypothesis Test** | `STAT` $\to$ `TESTS` $\to$ `1-PropZTest` | `1-PropZTest(`$p_0$, `x, n, alternative)` |

---

## Topic 1: Probability Functions (PDF vs. CDF)

* **Probability Density / Mass Function (PDF):**
  * Computes the probability of an outcome taking on **exactly** a specific value $k$.
  * $P(X = k)$
* **Cumulative Distribution Function (CDF):**
  * Computes the probability of an outcome taking on a value **less than or equal to** $k$.
  * $P(X \le k) = P(X = 0) + P(X = 1) + \dots + P(X = k)$

> **Tip for "At Least" / "Greater Than":**
> * $P(X \ge k) = 1 - P(X \le k - 1) = 1 - \text{CDF}(k - 1)$
> * $P(X > k) = 1 - P(X \le k) = 1 - \text{CDF}(k)$

---

## Topic 2: Discrete Probability Distributions

### A. Binomial Distribution
Used when counting the number of **successes** ($k$) in a **fixed number of independent trials** ($n$).

#### Conditions (**BINS**)
1. **B**inary: Outcomes are classified as Success or Failure.
2. **I**ndependent: Trials are independent of each other.
3. **N**umber: Fixed number of trials, $n$.
4. **S**ame probability: Probability of success $p$ is constant for every trial.

#### Formulas
* **Combinatorics:**
  $$\text{Factorials: } n! = n\times (n-1) \times (n-2) \times \dots \times 2 \times 1$$
  $$\text{Permutations: } {}_nP_k = \frac{n!}{(n-k)!} \qquad \qquad \text{Combinations: } {}_nC_k=\binom{n}{k} = \frac{{}_nP_k}{k!} = \frac{n!}{(n-k)!k!}$$
* **Probability:** 
  $$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$
* **Mean ($\mu$):** 
  $$E[X] = \mu_{\hat{p}} = np$$
* **Standard Deviation ($\sigma$):** 
  $$\sigma_{\hat{p}} = \sqrt{np(1-p)}$$

#### TI-84 Commands
* Exact probability $P(X = k)$: `binompdf(n, p, k)`
* Cumulative probability $P(X \le k)$: `binomcdf(n, p, k)`

---

### B. Geometric Distribution
Used when counting the number of trials ($k$) required to achieve the **first success**.

#### Conditions (**BITS**)
1. **B**inary: Success or Failure.
2. **I**ndependent trials.
3. **T**rials until first success: Variable $X$ is the number of trials needed.
4. **S**ame probability $p$ of success on each trial.

#### Formulas
* **Probability:** 
  $$P(X = k) = (1-p)^{k-1} p$$
* **Mean ($\mu$):** 
  $$E[X] = \mu_{\hat{p}} = \frac{1}{p}$$
* **Standard Deviation ($\sigma$):** 
  $$\sigma_{\hat{p}} = \frac{\sqrt{1-p}}{p}$$

#### TI-84 Commands
* Exact probability $P(X = k)$: `geometpdf(p, k)`
* Cumulative probability $P(X \le k)$: `geometcdf(p, k)`

---

### C. Poisson Distribution
Used when counting the number of events ($k$) occurring in a **fixed interval** of time or space.

#### Key Properties
* Events occur independently at a constant average rate $\lambda$.
* $X \sim \text{Poisson}(\lambda)$, where $\lambda$ is the mean number of occurrences in the given interval.

#### Formulas
* **Probability:** 
  $$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$$
* **Mean ($\mu$):** 
  $$E[X] = \mu_{\hat{p}} = \lambda$$
* **Standard Deviation ($\sigma$):** 
  $$\sigma_{\hat{p}} = \sqrt{\lambda}$$

#### TI-84 Commands
* Exact probability $P(X = k)$: `poissonpdf(`$\lambda$`, k)`
* Cumulative probability $P(X \le k)$: `poissoncdf(`$\lambda$`, k)`

---

## Topic 3: Continuous Distributions — Normal Distribution

### A. Properties of the Normal Distribution
* Bell-shaped, symmetric, continuous density curve centered at mean $\mu$ with spread standard deviation $\sigma$.
* Total area under the curve is always $1$ (or $100\%$).
* Notation: $X \sim N(\mu, \sigma)$.

### B. Empirical Rule (68-95-99.7 Rule)
For a symmetric, bell-shaped distribution:
* $\approx 68\%$ of data lies within $\mu \pm 1\sigma$.
* $\approx 95\%$ of data lies within $\mu \pm 2\sigma$.
* $\approx 99.7\%$ of data lies within $\mu \pm 3\sigma$.

---

### C. Standard Normal Distribution & Z-Scores
The **Standard Normal Distribution** has mean $\mu = 0$ and standard deviation $\sigma = 1$, denoted $Z \sim N(0, 1)$.

#### Z-Score Formula
A $z$-score measures how many standard deviations an observation $x$ lies away from the mean $\mu$:
$$z = \frac{x - \mu}{\sigma}$$

* Positive $z$-score: Value is above the mean.
* Negative $z$-score: Value is below the mean.

---

### D. Probability as Area under the Curve
For any continuous random variable, $P(a < X < b)$ corresponds to the area under the PDF curve between $x = a$ and $x = b$.

#### TI-84 Command: `normalcdf`
To find $P(a < X < b)$:
* `normalcdf(lower, upper,` $\mu, \sigma$`)`
* For Standard Normal ($Z$), set $\mu = 0, \sigma = 1$.
* For unbounded regions:
  * $P(X < b) \implies$ `normalcdf(-1E99, b,` $\mu, \sigma$`)`
  * $P(X > a) \implies$ `normalcdf(a, 1E99,` $\mu, \sigma$`)`
  *(Note: Key `1E99` using `1` $\to$ `2nd` $\to$ `,` (EE) $\to$ `99`)*

---

### E. Inverse Normal (`invNorm`)
Used when you are given a **probability or percentile** (area) and need to find the corresponding observation value $x$ or $z$-score.

#### TI-84 Command: `invNorm`
* `invNorm(area,` $\mu, \sigma$`)`
* **Important:** The `area` input **must** be the cumulative area to the **left** of the desired target value (unless using TI-84 Plus CE software specifying "LEFT", "CENTER", or "RIGHT").

---

## Topic 4: Central Limit Theorem (CLT)

### The Theorem
For a population with any distribution having mean $\mu$ and finite standard deviation $\sigma$, as sample size $n$ becomes large, the sampling distribution of the sample mean approaches a Normal distribution with a mean of $\mu_{\hat{p}} = p$ and a standard deviation of $\sigma_{\hat{p}} = \sigma / \sqrt{n}$. We call this sampling distribution $\bar{X}$:

$$\bar{X} \approx N\left(\mu, \frac{\sigma}{\sqrt{n}}\right)$$

* For Categorical data, *large enough* means,
    - Number of successes is at least 10 ($n\hat{p} \ge 10$)
    - Number of failures is at least 10 ($n(1-\hat{p}) \ge 10$)

### CLT for Sample Proportions ($\hat{p}$)
When taking random samples of size $n$ from a population with true proportion $p$:
* Mean of sample proportions: $\mu_{\hat{p}} = p$
* Standard Error of sample proportions: $\sigma_{\hat{p}} = \sqrt{\frac{p(1-p)}{n}}$

#### Conditions for Sampling Distribution of $\hat{p}$ to be Approximately Normal:
1. **Random Sampling:** Sample must be selected randomly.
2. **Large Counts Condition (Normality):** 
   $$np \ge 10 \quad \text{and} \quad n(1-p) \ge 10$$

---

## Topic 5: Confidence Intervals for 1-Sample Proportion Data

### A. Purpose
To estimate an unknown population parameter $p$ using a sample proportion $\hat{p} = \frac{x}{n}$.

### B. Formula
$$\text{Confidence Interval} = \hat{p} \pm z_c \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$

Where:
* $\hat{p} = \frac{x}{n}$ (Sample proportion)
* $z_c$ is the critical value based on confidence level $C$:
  * $90\%$ Confidence $\implies z_c \approx 1.645$
  * $95\%$ Confidence $\implies z_c \approx 1.960$
  * $99\%$ Confidence $\implies z_c \approx 2.576$
* $\text{Margin of Error (ME)} = z_c \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$

### C. Conditions to Check
1. **Random:** Data comes from a random sample or randomized experiment.
2. **Large Counts:** $n\hat{p} \ge 10$ and $n(1-\hat{p}) \ge 10$ (or $x \ge 10$ successes and $n - x \ge 10$ failures).

### D. TI-84 Command
* `STAT` $\to$ `TESTS` $\to$ `A: 1-PropZInt`
* Inputs: 
  * `x`: Number of successes (must be a whole integer)
  * `n`: Total sample size
  * `C-Level`: Confidence level (e.g., `0.95`)

---

## Topic 6: Hypothesis Testing for 1-Sample Proportion Data

### A. Hypotheses Setup
* **Null Hypothesis ($H_0$):** $p = p_0$ (where $p_0$ is the hypothesized population proportion)
* **Alternative Hypothesis ($H_a$):**
  * $p \ne p_0$ (Two-sided test)
  * $p > p_0$ (One-sided upper test)
  * $p < p_0$ (One-sided lower test)

### B. Test Statistic ($z$)
$$z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$$

> **Note:** Notice that standard error here uses $p_0$ from $H_0$, **not** $\hat{p}$.

Determination:
* If the test statistic $z$ is more extreme than the critical value $z_c$, then we **reject $H_0$**.
* If the test statistic $z$ is closer to zero than the critical value $z_c$, then we **fail to reject $H_0$**.

### C. Decision Rule (p-value approach)
Assume you find a test statistic $z_t$. The p-value is found as,
* Left-tailed test:   $p\text{-value} = P(z < z_t)$ 
* Right-tailed test:  $p\text{-value} = P(z > z_t)$
* Two-tailed test:    $p\text{-value} = 2*P(|z| > |z_t|)$

Determination:
* **If $p\text{-value} \le \alpha$:** Reject $H_0$. There is convincing statistical evidence for $H_a$.
* **If $p\text{-value} > \alpha$:** Fail to reject $H_0$. There is insufficient statistical evidence for $H_a$.

### D. Conditions to Check
1. **Random:** Random sample.
2. **Large Counts:** $n p_0 \ge 10$ and $n(1 - p_0) \ge 10$ (using the hypothesized value $p_0$).

### E. TI-84 Command
* `STAT` $\to$ `TESTS` $\to$ `5: 1-PropZTest`
* Inputs:
  * `p0`: Hypothesized value from $H_0$
  * `x`: Number of successes
  * `n`: Sample size
  * `prop`: Select alternative hypothesis matching $H_a$ ($\ne p_0$, $< p_0$, or $> p_0$)