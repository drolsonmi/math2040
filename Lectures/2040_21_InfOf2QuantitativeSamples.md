<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 21: Inference with 2 Quantitative Samples
* __Note__: 

Resources for this lecture:

Remember:

## Paired samples
* The two samples are dependent on each other
    * One event in one sample is connected to a specific event in the other sample
    * Husband - to - wife height difference
    * Temperature - to - exam scores
    * Children's height at 1 year old compared to 4 years old (Longitudinal study)

$$d = \mu_1 − \mu_2$$

### Confidence Intervals
$$SE = \frac{\sigma_d}{\sqrt{n}}$$

$$ME = t_c \cdot SE$$
* To find the critical value, use a t-distribution with *df = n − 1*

$$\mu_d = \bar{d} \pm ME$$


### Hypothesis Testing
$$SE = \frac{\sigma_d}{\sqrt{n}} = √((σ_d^2)/n)

$$t = \frac{\mu_d − \mu_0}{SE}$$
* Typically, $$\mu_0 = 0$$

p-value = probability of getting a value more extreme than your test statistic


## Non-paired samples
* There is no connection between specific events in the two samples
* Independent samples

### Confidence Intervals
$$SE = \sqrt{ \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} }$$

$$ME = t_c \cdot SE$$
* To find the critical value, use a t-distribution with $$df = \min⁡{n_1−1, n_2−1}$$

$$\mu_1 − \mu_2 = (\bar{x}_1 − \bar{x}_2) \pm ME$$


### Hypothesis Tests
$$SE = \sqrt{\frac{s_1^2}{n_1} +\frac{s_2^2}{n_2}}$$

$$t = \frac{(\bar{x}_1−\bar{x}_2) − \mu_0}{SE}$$
* Typically, $$\mu_0 = 0$$


## Practice






-----
# Homework
## Reading
* 7.2 Paired data
* 7.3 Difference of two means

## Exercises
1. Exercise 7.16 from section 7.2 exercises
2. Exercise 7.17 from section 7.2 exercises
3. Exercise 7.19 from section 7.2 exercises
4. Exercise 7.21 from section 7.2 exercises
5. Exercise 7.22 from section 7.2 exercises (Look at exercise 7.20 for more context)
6. Exercise 7.27 from section 7.3 exercises
7. Exercise 7.29 from section 7.3 exercises
8. Exercise 7.32(a,b) from section 7.3 exercises
9. Exercise 7.31 from section 7.3 exercises