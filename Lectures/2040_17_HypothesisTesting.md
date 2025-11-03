<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 17: Hypothesis Testing
* __Notes__

Resources for this lecture:

Remember:

## Hypothesis testing framework
* Courtroom
* Null Value
* Default assumption (Null Hypothesis)
* Desired outcome (Alternate hypothesis)

## Testing hypotheses using confidence intervals
Show that the number of beans in my jar is not equally balanced (balanced means 50% are black beans, 50% are pinto beans)
* What is the null value?
* What is the null hypothesis?
* What is the alternate hypothesis?
* Is my null value a plausible true value?
* Do I reject H0 and adopt HA instead? Or is there not enough evidence to reject H0?

### Example: Elections
In the most recent elections, a poll of 325 people indicated that 53% of them would vote for a candidate. Is that enough to say with a 95% confidence level that this candidate will win the election without counting?
* What is the null value?
* What is the null hypothesis?
* What is the alternate hypothesis?
$$\hat{p} = 0.53 \qquad SE=\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} = \sqrt{\frac{0.53(0.47)}{325}} = \sqrt{0.000766} = 0.0277$$
$$ME = z_cSE = 1.96(0.0277) = 0.0543$$
$$p\text{ is in }\hat{p}\pm ME = 0.53 \pm 0.0543$$
$$0.4757 \le p \le 0.5843$$

Since a minority vote is possible, we cannot say for sure that the true proportion is a majority.
* We reject H0
* Conclusion: We do not have enough evidence to show that the candidate has won the vote.


## Decision Errors

|         | Fail to reject H0                | Reject H0                        |
| :------ | :------------------------------: | :------------------------------: |
| H0 True | Good                             | Type 1 Error<br>(False Positive) |
| HA True | Type 2 Error<br>(False Negative) | Good                             |

Example: Testing for cancer
* H0: The patient does not have cancer
* HA: The patient does have cancer
  * If we reject H0, then we adopt HA, indicated the patient has a positive result for cancer
  * If we adopt HA and declare the patient has cancer but actually doesn't, that is a false positive

## Testing hypotheses using the p-value
Level of Significance
* Confidence level and level of significance on Desmos

Test statistic
$$z = \frac{\text{point estimate - null value}}{SE}$$

The p-value is the size of the tail beyond the test statistic.
* Small p-value means not likely
* If the test statistic is in the tail despite being unlikely, it indicates there is likely a difference

> ### Example: 
> (Do an example of something that is not equally balanced, where we reject H0)

3 types of hypothesis tests
* Two-tailed test ($H_A: p\ne p_0$)
* Left-tailed test ($H_A: p< p_0$)
* Right-tailed test ($H_A: p> p_0$)

> Show the 3 test types on Desmos: 10% in two tails, in left tail, in right tail
> * Show a test statistic that would pass the test in left-tailed test, but not in two-tailed test

> ### Example: Elections
> In the most recent elections, a poll of 325 people indicated that 53% of them would vote for a candidate. Is that enough to say with a 5% level of significance that this candidate will win the election without counting?
> * What is the null value?
> * What is the null hypothesis?
> * What is the alternate hypothesis?
>
> $$\hat{p} = 0.53$$
> $$n\hat{p} = 325 * 0.53 = 172.25 \approx 172\qquad n(1-\hat{p}) = 325*0.47 = 152.75\approx 153$$
>
> The sample size is large enough. Assuming the sample is random and independent, the CLT is satisfied and we can continue.
>
> $$SE=\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} = \sqrt{\frac{0.53(0.47)}{325}} = \sqrt{0.000766} = 0.0277$$
> $$z = \frac{0.53 - 0.50}{0.0277} = 1.083$$
> $$\text{p-value} = P(z > 1.083) = 0.139 > 0.05 = \alpha$$
> 
> $$\text{Fail to reject }H_0$$

### Revisiting the Shapiro-Wilk test (Lab 3)
* Null Hypothesis: The data is normally distributed (default assumption)
* Alternate Hypothesis: The data is not normally distributed

If the p-value is smaller than the threshold, then null hypothesis is rejected, and we can claim the data is not normally distributed

-----
# Homework
## Reading
* 5.3 Hypothesis testing for a proportion
* 6.1 Inference for a single proportion

## Exercises
1. Exercise 5.15 from section 5.3 exercises
2. Exercise 5.16 from section 5.3 exercises
3. Exercise 5.17 from section 5.3 exercises
4. Exercise 5.22 from section 5.3 exercises
5. Exercise 5.23 from section 5.3 exercises
6. Exercise 5.24 from section 5.3 exercises
7. Exercise 5.25 from section 5.3 exercises
8. Exercise 5.29 from chapter 5 exercises