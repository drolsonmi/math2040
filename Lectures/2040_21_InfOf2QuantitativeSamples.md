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
$$SE = \frac{s_d}{\sqrt{n}} = \sqrt{\frac{s_d^2}{n}}$$

$$t = \frac{\bar{d} − \mu_0}{SE}$$
* Typically, $$\mu_0 = 0$$

p-value = probability of getting a value more extreme than your test statistic


## Non-paired samples
* There is no connection between specific events in the two samples
* Independent samples

### Confidence Intervals
$$SE = \sqrt{ \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} }$$

$$ME = t_c \cdot SE$$

To find the critical value, use a t-distribution with $$df = \min⁡\{n_1−1, n_2−1\}$$

$$\mu_1 − \mu_2 = (\bar{x}_1 − \bar{x}_2) \pm ME$$


### Hypothesis Tests
$$SE = \sqrt{\frac{s_1^2}{n_1} +\frac{s_2^2}{n_2}}$$

$$t = \frac{(\bar{x}_1−\bar{x}_2) − \mu_0}{SE}$$
* Typically, $$\mu_0 = 0$$


## Practice
### Paired Sample
Soil scientists often measure the water content in soil by taking the mass, then baking the soil to let the water evaporate, then taking the mass again. The data from 35 random samples are below. With a 1% significance level, is there a statistically significant difference in the masses? (That is, does the water have a significant contribution to the mass, or is the soil dry?) Assume the population is normally distributed.

|        |       |       |       |       |       |       |       |       |       |       |
| -----: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Before | 50.23 | 48.71 | 49.94 | 47.52 | 50.61 | 48.34 | 49.13 | 49.53 | 50.44 | 49.01 |
| After  | 50.11 | 48.53 | 49.83 | 47.50 | 50.55 | 48.15 | 49.03 | 49.52 | 50.34 | 48.96 |
| Diff   |  0.12 |  0.18 |  0.11 |  0.02 |  0.06 |  0.19 |  0.10 |  0.01 |  0.10 |  0.05 |
|        |       |       |       |       |       |       |       |       |       |       |
| Before | 47.91 | 50.02 | 48.65 | 49.41 | 47.83 | 50.15 | 48.92 | 49.84 | 48.13 | 50.52 |
| After  | 47.88 | 49.85 | 48.53 | 49.35 | 47.81 | 49.96 | 48.81 | 49.82 | 47.99 | 50.35 |
| Diff   |  0.03 |  0.17 |  0.12 |  0.06 |  0.02 |  0.19 |  0.11 |  0.02 |  0.14 |  0.17 |

* CLT is satisfied
* H0:  $$\mu_d = 0$$      HA:  $$\mu_d\ne 0$$
* $$\bar{d} = 0.0985 \qquad s_d = 0.0619 \qquad n = 20 \qquad df = 19$$
* $$SE = \frac{s_d}{\sqrt{n}} = \frac{0.0619}{\sqrt{20}} = 0.013846$$
* $$t = \frac{\bar{d} - \mu_0}{SE} = \frac{0.0985-0}{0.013846} = 7.113746$$
* $$p-value = 2*P(t>7.113746) = 2 * 4.577 * 10^{-7} = 0.00000091549$$
* Reject H0

Thus, there is a statistically significant difference.


### Non-paired Sample
Now, let's compare soil in Utah to soil in Colorado. Soil samples are taken at random in Utah and in Colorado. The data are below. With a 1% significance level, is there a statistically significant difference in water content between the two states? Assume the populations are normally distributed.

| Mass Differences |       |       |       |       |       |       |       |
| ---------------: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Utah             |  0.04 |  0.06 |  0.03 |  0.05 |  0.02 |  0.04 |       |
|                  |  0.03 |  0.05 |  0.06 |  0.04 |  0.03 |  0.05 |       |
|                  |       |       |       |       |       |       |       |
| Colorado         |  0.07 |  0.06 |  0.08 |  0.05 |  0.03 |  0.06 |  0.07 |
|                  |  0.03 |  0.06 |  0.07 |  0.05 |  0.08 |  0.02 |  0.04 |

* CLT is satisfied

$$\text{H0: } \bar{x}_1 - \bar{x}_2 = 0$$     HA:  $$\bar{x}_1 - \bar{x}_2 \ne 0$$

* $$\bar{x}_1 = 0.041667 \qquad s_1 = 0.012673 \qquad n_1 = 12$$
* $$\bar{x}_2 = 0.055    \qquad s_2 = 0.019115 \qquad n_2 = 14$$
    * $$df = \min{n_1-1,n_2-1} = \min{11,13} = 11$$
* $$SE = \sqrt{\frac{s_1^2}{n_1}+\frac{s_2}{n_2}} = \sqrt{\frac{0.012673^2}{12} + \frac{0.019115^2}{14}} = 0.006284$$
* $$t = \frac{(\bar{x}_1-\bar{x}_2)-0}{SE} = \frac{0.041667-0.055}{0.006284} = -2.12195$$
* $$p-value = 2*P(t<-2.12195) = 2 * 0.0286878 = 0.573756$$


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