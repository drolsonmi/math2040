<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 18: Inference with proportions of 2 samples
* __Notes:__
  * No class on Friday or Monday - Fall Break
  * Lab 4 on Friday, Oct 24 - Bring your laptops
  * Exam 2 on Wednesday, Oct 29 (2 weeks from this Wednesday)

## Difference of two proportions
We have two independent samples. How do we compare them? In this case, we are not comparing our sample to a null value, but to another dataset.
* $H_0:~~p_1=p_2 \qquad p_1−p_2=0$
* $H_A$:
    * Left-tailed test: $\qquad ~~p_1<p_2 \qquad p_1−p_2<0$
    * Right-tailed test: $\qquad p_1>p_2 \qquad p_1−p_2>0$
    * Two-tailed test: $\qquad~~p_1\ne p_2 \qquad p_1−p_2\ne 0$

$$SE = \sqrt{\frac{p_1(1-p_1)}{n_1}+\frac{p_2(1-p_2)}{n_2}}$$

Steps are followed as we saw with 1 sample:
* Verify CLT is verified
* Identify null and alternate hypotheses
* Determine level of significance
* Find SE
* Perform the inference by doing either of these:
    * Find a confidence interval
    * Find a test statistic (z-score) and calculate the p-value

Confidence interval:
$$\hat{p}_1-\hat{p}_2 \pm z_cSE$$

### Example
A poll of 260 Utahns showed that 59.4% would vote for Donald Trump in the 2024 election.
A poll of 425 Texans showed that 56.1% would vote for Donald Trump in the 2024 election.

### When do we use this?
* Comparing one population to another
* Experimental studies, comparing the control group to the treatment group

## Pooled Proportions
The null hypothesis is typically $\hat{p}_1-\hat{p}_2=0$. When this is the case, we are essentially saying the samples are part of the same population makeups. In this case, we can get a more accurate estimate of the proportion by using the __pooled proportion__.
$$\hat{p}_{pooled} = \frac{\text{Total number of successes in both samples}}{\text{Total of both sample sizes}}$$
$$\hat{p}_{pooled} = \frac{x_1 + x_2}{n_1 + n_2} = \frac{\hat{p}_1n_1 + \hat{p}_2n_2}{n_1 + n_2}$$

where $x_i$ is the number of successes in sample $i$. Our Standard Error becomes,
$$SE = \sqrt{\frac{\hat{p}_{pooled}(1-\hat{p}_{pooled})}{n_1} + \frac{\hat{p}_{pooled}(1-\hat{p}_{pooled})}{n_2}} = \sqrt{\hat{p}_{pooled}(1-\hat{p}_{pooled})\left(\frac{1}{n_1} + \frac{1}{n_2}\right)}$$


### Example: Do Mamograms help?

|           | Died from breast cancer | Didn't die from breast cancer |
| --------: | :---------------------: | :---------------------------: |
| Mammogram | 500                     | 44,425                        |
| Control   | 505                     | 44,405                        |

-----
# Homework
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