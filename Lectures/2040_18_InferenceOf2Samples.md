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
<title>Lecture 18: Inference with proportions of 2 samples</title></head>

# Lecture 18: Inference with proportions of 2 samples
* __Notes:__
  * No class on Friday or Monday - Fall Break
  * Lab 4 on Friday, Oct 24 - Bring your laptops
  * Exam 2 on Wednesday, Oct 29 (2 weeks from this Wednesday)

Ahead of the 2024 election, random polls were taken in Utah and in Texas.
* A poll of 260 Utahns showed that 59.4% would vote for Donald Trump
* A poll of 425 Texans showed that 56.1% would vote for Donald Trump

## Difference of two proportions
We want to compare the two samples. We do this by seeing how they compare to each other (for example, $\hat{p}_1 > \hat{p}_2$) or how the difference looks ($\hat{p}_1 - \hat{p}_2 > 0$). We will focus on the difference of the two proportions.

Also, since we are dealing with 2 samples, the Central Limit Theorem must be satisfied *for both samples*. That is, all of the following must be true:

$$x_1 = n_1\hat{p}_1 \ge 10 \qquad x^C_1 = n_1 - x_1 \ge 10$$

$$x_2 = n_2\hat{p}_2 \ge 10 \qquad x^C_2 = n_2 - x_2 \ge 10$$

### When do we use this?
* Comparing one population to another
* Experimental studies, comparing the control group to the treatment group

## Confidence Interval for 2 categorical samples

We follow the same steps as before. The only difference will be in the calculation for the Standard Error
1. Verify CLT is verified
2. Determine confidence level and critical value
3. Find the Standard Error

  $$SE = \sqrt{\frac{p_1(1-p_1)}{n_1}+\frac{p_2(1-p_2)}{n_2}}$$

4. Find the Margin of Error

  $$ME = z_c SE$$

5. Find and interpret the confidence interval

  $$(\hat{p}_1-\hat{p}_2) \pm z_cSE$$

### Election example
Using a 90% confidence level, determine the difference between the two poll results.

1. Verify CLT is verified
  * Random? Yes
  * Large Enough? Yes
    
    $$x_1 = n_1\hat{p}_1 = 260(0.594) = 154 \ge 10 \qquad x^C_1 = 260 - 154 = 106 \ge 10$$

    $$x_2 = n_2\hat{p}_2 = 425(0.561) = 238 \ge 10 \qquad x^C_2 = 425 - 238 = 187 \ge 10$$

2. Determine confidence level and critical value
  * $C = 0.90 \to z_c = 1.645$

3. Find the Standard Error

  $$\begin{align*}
    SE &= \sqrt{\frac{p_1(1-p_1)}{n_1}+\frac{p_2(1-p_2)}{n_2}} \\
       &= \sqrt{\frac{0.594(0.406)}{260}+\frac{0.561(0.439)}{425}} \\
       &= \sqrt{0.0009276 + 0.0005795} \\
       &= 0.03882
    \end{align*}$$

4. Find the Margin of Error

  $$ME = z_c SE = 1.645(0.03882) = 0.06386$$

5. Find and interpret the confidence interval

  $$\begin{align*}
      (\hat{p}_1-\hat{p}_2) \pm ME &= (0.594 - 0.561) \pm 0.06386 \\
                                   &= 0.033 \pm 0.06386 = (-0.031, 0.097)
    \end{align*}$$

  * We are 90% confident that the true difference in proportions between Utahn and Texan voters is between -3.1% and 9.7%.


## Hypothesis Testing for 2 categorical samples
### Pooled Proportions
The null hypothesis is typically $\hat{p}_1-\hat{p}_2=0$. When this is the case, we are essentially saying the samples are part of the same population makeups. In this case, we can get a more accurate estimate of the proportion by using the __pooled proportion__. This combines the successes from both samples.

$$\hat{p}_{pooled} = \frac{\text{Total number of successes in both samples}}{\text{Total of both sample sizes}}$$

$$\hat{p}_{pooled} = \frac{x_1 + x_2}{n_1 + n_2} = \frac{n_1\hat{p}_1 + n_2\hat{p}_2}{n_1 + n_2}$$

where $x_i$ is the number of successes in sample $i$. Our Standard Error becomes,

$$SE = \sqrt{\frac{\hat{p}_{pooled}(1-\hat{p}_{pooled})}{n_1} + \frac{\hat{p}_{pooled}(1-\hat{p}_{pooled})}{n_2}} = \sqrt{\hat{p}_{pooled}(1-\hat{p}_{pooled})\left(\frac{1}{n_1} + \frac{1}{n_2}\right)}$$

Remember that we want the best possible proportion when we calculate SE. With 1 sample, we used the null value. In this case, our null value is 0. However, this indicates

### The Hypothesis Test
Steps are followed as we saw with 1 sample:
* Verify CLT is verified
* Identify null and alternate hypotheses
* $H_0: ~~~ p_1−p_2=0$
* $H_A$:
    * Left-tailed test: $\qquad p_1−p_2<0$
    * Right-tailed test: $\qquad p_1−p_2>0$
    * Two-tailed test: $\qquad p_1−p_2\ne 0$
* Determine level of significance
* Find SE
* Perform the inference by doing either of these:
    * Find a confidence interval
    * Find a test statistic (z-score) and calculate the p-value








## A Second Example: Do Mamograms help?

|           | Died from breast cancer | Didn't die from breast cancer |
| --------: | :---------------------: | :---------------------------: |
| Mammogram | 500                     | 44,425                        |
| Control   | 505                     | 44,405                        |

-----
# Homework
(13 points)

## Reading
* 6.2 Difference of two proportions

## Exercises
1. Exercise 6.18 from section 6.2 exercises
2. Exercise 6.19 from section 6.2 exercises
3. Exercise 6.22 from section 6.2 exercises
4. Exercise 6.24 from section 6.2 exercises
5. Exercise 6.23 from section 6.2 exercises
6. Exercise 6.25 from section 6.2 exercises
7. Exercise 6.28 from section 6.2 exercises