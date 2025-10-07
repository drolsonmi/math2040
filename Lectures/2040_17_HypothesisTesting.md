# Lecture 17: Hypothesis Testing
* __Note__: 

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
In the most resent elections, a poll of 325 people indicated that 53% of them would vote for a candidate. Is that enough to say with a 95% confidence level that this candidate will win the election without counting?
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

The p-value is the size of the tail beyond the test statistic.
* Small p-value means not likely
* If the test statistic is in the tail despite being unlikely, it indicates there is likely a difference

### Revisiting the Shapiro-Wilk test (Lab 3)
* Null Hypothesis: The data is normally distributed (default assumption)
* Alternate Hypothesis: The data is not normally distributed

If the p-value is smaller than the threshold, then null hypothesis is rejected, and we can claim the data is not normally distributed

-----
# Homework
## Reading
* 5.3 Hypothesis testing for a proportion

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises