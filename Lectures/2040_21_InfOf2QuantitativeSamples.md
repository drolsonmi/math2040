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
<title>Lecture 21: Inference with 2 Quantitative Samples</title></head>

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

$$SE = \frac{s_d}{\sqrt{n}} = \sqrt{\frac{s_d^2}{n}}$$

$$ME = t_c \cdot SE$$

* To find the critical value, use a t-distribution with *df = n − 1*

$$\mu_d = \bar{d} \pm ME$$


### Hypothesis Testing

$$SE = \frac{s_d}{\sqrt{n}} = \sqrt{\frac{s_d^2}{n}}$$

$$t = \frac{\bar{d} − \mu_0}{SE}$$

* Typically, $$\mu_0 = 0$$

p-value = probability of getting a value more extreme than your test statistic

### Practice 1: Paired Sample
A tutoring center wants to know whether its 2-week study-skills workshop raises students’ scores. Eight students take a practice exam before the workshop and a similar exam after it. Assume the sample is random and that the population is normally distributed.

| Student    |   1   |   2   |   3   |   4   |   5   |   6   |   7   |   8   |
| :--------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Before     |  72   |  65   |  80   |  58   |  90   |  77   |  68   |  74   |
| After      |  78   |  70   |  83   |  64   |  91   |  82   |  67   |  80   |

1. Build a 95% confidence interval for the mean improvement.
2. At α = 0.05, is there evidence that the workshop raises scores on average?

#### Confidence Interval
* CLT is satisfied
* Find the differences

| Student    |   1   |   2   |   3   |   4   |   5   |   6   |   7   |   8   |
| :--------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Difference |   6   |   5   |   3   |   6   |   1   |   5   |  -1   |   6   |

* Perform 1-sample confidence interval on the differences

$$\bar{x}_d = 3.875 \qquad s = 2.642$$

$$t_c = 2.365 \qquad SE = \frac{s}{\sqrt{n}} = \frac{2.642}{\sqrt{8}} = 0.934 \qquad ME = t_cSE = 2.365(0.934) = 2.209$$

$$\mu_d = \bar{x}_d \pm ME = 3.875 \pm 2.209 \qquad (1.666, 6.084)$$

We are 95% that the true average increase in exam scores is between 1.666 and 6.084.

#### Hypothesis Test
* CLT is satisfied
* State Hypotheses
  * $H_0: \mu_d = 0$
  * $H_A: \mu_d > 0$
* Critical Value
  * Right-tailed test
  
  $$t_c = 1.895$$

* Test Statistic and p-value

  $$SE = \frac{s}{\sqrt{n}} = \frac{2.642}{\sqrt{8}} = 0.934$$

  $$t = \frac{\bar{x}_d - \mu_0}{SE} = \frac{3.875 - 0}{0.934} = 4.149$$

  * $t$ is more extreme than $t_c$ --> __Reject $H_0$__

  $$p\text{-value} = P(t > 4.149) = 0.0022$$

  * p-value $< \alpha$ --> __Reject $H_0$__

* Conclusion
  * There is enough evidence to suggest that the workshop does raise average exam scores


### Practice 2: Paired Sample
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

$$H_0:~~\mu_d = 0 \qquad \qquad H_A:~~\mu_d\ne 0$$

$$\bar{d} = 0.0985 \qquad s_d = 0.0619 \qquad n = 20 \qquad df = 19$$

$$SE = \frac{s_d}{\sqrt{n}} = \frac{0.0619}{\sqrt{20}} = 0.013846$$

$$t = \frac{\bar{d} - \mu_0}{SE} = \frac{0.0985-0}{0.013846} = 7.113746$$

$$p\text{-value} = 2*P(t>7.113746) = 2 * 4.577 * 10^{-7} = 0.00000091549$$

* Reject H0

Thus, there is a statistically significant difference.


## Non-paired samples
* There is no connection between specific events in the two samples
* Independent samples

### Confidence Intervals

$$SE = \sqrt{ \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} } \qquad ME = t_c \cdot SE$$

To find the critical value, use a t-distribution with $$df = \min⁡\{n_1−1, n_2−1\}$$

$$\mu_1 − \mu_2 = (\bar{x}_1 − \bar{x}_2) \pm ME$$

### Hypothesis Tests
$$SE = \sqrt{\frac{s_1^2}{n_1} +\frac{s_2^2}{n_2}} \qquad t = \frac{(\bar{x}_1−\bar{x}_2) − \mu_0}{SE}$$
* Typically, $$\mu_0 = 0$$


### Practice 1: Non-paired Sample
A horticulture class wants to compare two fertilizers. They randomly assign 18 tomato seedlings to two groups. After 4 weeks they measure each plant’s height in cm. Assume normally distributed.

| Fertilizer | Data                                   | Sample Size | Mean   | StDev |
| :--------- | :------------------------------------- | :---------: | :----: | :---: |
| A          | 24, 27, 22, 30, 26, 28, 25, 29	        | 8           | 26.375 | 2.669 |
| B          | 20, 23, 25, 19, 22, 24, 21, 26, 18, 22 | 10          | 22.0   | 2.582 |

1. Build a 95% confidence interval for the difference in means.
2. At α = 0.05, is there evidence that mean height differs between the two fertilizers?

#### Confidence Interval
* CLT is satisfied

$$df = \min\{8-1, 10-1\} = \min\{7, 9\} = 7 \qquad t_c = 2.365$$

$$SE = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}} = \sqrt{\frac{2.669^2}{8} + \frac{2.582^2}{10}} = 1.248 \qquad ME = t_cSE = 2.365(1.248) = 2.951$$

$$\mu_d = \bar{x}_d \pm ME = (26.375 - 22.000) \pm 2.951 = 4.375 \pm 2.951 \qquad (1.4245, 7.326)$$

We are 95% confident that the true average differences in plant heights is between 1.4245 cm and 7.326, with fetilizer A having the larger heights.

#### Hypothesis Test
* CLT is satisfied
* State Hypotheses
  * $H_0: \mu_d = 0$
  * $H_A: \mu_d \ne 0$
* Critical Value:  two-tailed test

  $$t_c = 2.365$$

* Test Statistic and p-value

  $$SE = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}} = \sqrt{\frac{2.669^2}{8} + \frac{2.582^2}{10}} = 1.248$$

  $$t = \frac{(\bar{x}_1 - \bar{x}_2) - \mu_0}{SE} = \frac{(26.375 - 22.000) - 0}{1.248} = \frac{4.375}{1.248} = 3.506$$

  * $t$ is more extreme than $t_c$ --> __Reject $H_0$__

  $$p\text{-value} = P(t > 3.506) = 0.0099$$

  * p-value $< \alpha$ --> __Reject $H_0$__

* Conclusion
  * There is enough evidence to suggest that there is a difference in the growth of plants between the two fertilizers.


### Practice 2: Non-paired Sample
Now, let's compare soil in Utah to soil in Colorado. Soil samples are taken at random in Utah and in Colorado. The data are below. With a 1% significance level, is there a statistically significant difference in water content between the two states? Assume the populations are normally distributed.

| Mass Differences |       |       |       |       |       |       |       |
| ---------------: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Utah             |  0.04 |  0.06 |  0.03 |  0.05 |  0.02 |  0.04 |       |
|                  |  0.03 |  0.05 |  0.06 |  0.04 |  0.03 |  0.05 |       |
|                  |       |       |       |       |       |       |       |
| Colorado         |  0.07 |  0.06 |  0.08 |  0.05 |  0.03 |  0.06 |  0.07 |
|                  |  0.03 |  0.06 |  0.07 |  0.05 |  0.08 |  0.02 |  0.04 |

* CLT is satisfied

$$H_0:~~\bar{x}_1 - \bar{x}_2 = 0 \qquad\qquad H_A:~~\bar{x}_1 - \bar{x}_2 \ne 0$$

$$\bar{x}_1 = 0.041667 \qquad s_1 = 0.012673 \qquad n_1 = 12$$

$$\bar{x}_2 = 0.055    \qquad s_2 = 0.019115 \qquad n_2 = 14$$

$$df = \min\{n_1 - 1,n_2 - 1\} = \min\{11,13\} = 11$$

$$SE = \sqrt{\frac{s_1^2}{n_1}+\frac{s_2}{n_2}} = \sqrt{\frac{0.012673^2}{12} + \frac{0.019115^2}{14}} = 0.006284$$

$$t = \frac{(\bar{x}_1-\bar{x}_2)-0}{SE} = \frac{0.041667-0.055}{0.006284} = -2.12195$$

$$p\text{-value} = 2*P(t<-2.12195) = 2 * 0.0286878 = 0.573756$$


-----
# Homework
(15 points)

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