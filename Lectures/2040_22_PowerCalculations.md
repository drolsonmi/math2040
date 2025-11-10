<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 22: Power Calculations
* __Note__: 

Resources for this lecture:
* [Desmos: Power](https://www.desmos.com/calculator/pprrzsem7i)

Remember:

## Power Calculations
In a study, we want to know how likely we are to detect an effect.
* If there is a real effect and that effect is large enough that is has practical value, we can calculate the __power__, or the probability that we detect that effect.

## Calculating the Power
Remember the Type I and Type II Errors

|                | Fail to reject H0                   | Reject H0                      |
| -------------: | :---------------------------------: | :----------------------------: |
| H0 is true     | Good                                | Type I Error<br>False Negative |
| H0 is not true | Type II Error<br>False Positive     | Good                           |

In reality, either H0 is true or H0 is not true. Let's first assume that H0 is true.
* If H0 is true, then the true mean is $\mu_0$
  > Draw a normal distribution around $\mu_0$ on Desmos (use link above)
* Significance Level is probability of a Type I Error:
    $$\alpha = P(Reject~H_0 | H_0~is~true) = P(\text{Type I Error})$$
  > Highlight significance level
* Complement of significance level (confidence level) is probability of correctly saying H0 is true:
    $$P(Fail~to~reject~H_0 | H_0~is~true) = 1 - P(Reject~H_0 | H_0~is~true)$$

Now, we consider if H0 is not true
* If H0 is not true, then HA is true, and the true mean is around $\mu_1$
  > Draw another normal distribution around $\mu_1$
* Probability of a Type II Error is the tail of this second distribution that goes into the area of the Confidence Level
    $$\beta = P(Fail~to~reject~H_0 | H_0~is~not~true) = P(\text{Type II Error})$$
  > Highlight Type II Error region
* The rest of the area in the HA normal distribution is the probability that we accurately reject H0. This is __power__. In short, this is the probability that we successfully reject the 
    $$Power = P(Reject~H_0 | H_0~is~not~true)$$

### Example 1
In an automobile production line, the time to assemble a door takes an average of 8.50 minutes with a standard deviation of 1.3 minutes. You hear of a new process that decreases the process to 8.21 minutes. You decide to test this by sampling 50 door assemblies using the new procedure. What is the power? In other words, what is the probability that you will get a value that shows the process has decreased production time? Use a 5% level of significance.
* H0: $$\mu = 8.50$$
* HA: $$\mu < 8.50$$

The level of significance is $$\alpha = P(\text{Type I Error}) = P(x < x_c)$$. The critical value is $$x_c = 8.198$$.

To find $$\beta = P(\text{Type II Error})$$, we create a new distribution assuming HA is true (mean of the distribution is now the true value of 8.21). Then $$\beta = P(\text{Type II Error}) = P(x > x_c) = 0.526$$

The power is the complement: $$Power = 1-P(\text{Type II Error}) = 1-0.526 = 0.474$$. So there is a 47.4% chance that I will get a good result.

### Example 1 Viewpoint 2
In an automobile production line, the time to assemble a door takes an average time with a standard deviation of 1.3 minutes. You hear of a new process that decreases the process by 0.29 minutes. You decide to test this by sampling 50 door assemblies to measure the time difference using the new procedure. What is the power? In other words, what is the probability that you will get a difference in times that shows the process has decreased production time? Use a 5% level of significance.
* Let $$d = t_new - t_old$$
* H0:  $$\mu_d = 0$$
* HA:  $$\mu_d = -0.29$$

> Do on Desmos to show it's the same.


## How to increase the power
1. Increase significance level ($\alpha$) --> This increases the power, but also increases *P(Type I Error)*.
2. Increase sample size ($n$) --> Makes both distributions narrower
3. Decrease variability ($s$) --> Makes both distributions narrower (don't have control over this)
4. Increase separation between point estimate and null value --> (don't have control over this)

> Vary each of these in Desmos

Really, the only option is to change *n*.
* Note that the difference between $\mu_0$ and $\mu_A$ is equal to the sum of the distances from $\mu_0$ to the critical value and from $\mu_A$ to that critical value
    * Distance from $\mu_0$ to the critical value = $z_\alpha SE$
    * Distance from $\mu_A$ to the critical value = $z_\beta SE$
    $$\mu_A-\mu_0 = z_\beta SE + z_\alpha SE$$

To find the right sample size,
1. Find the z-score that corresponds with $$\alpha$$
2. Find your z-score that correspons with $$\beta$$
3. Set $$(z_\alpha + z_\beta)SE$$ equal to the difference $$\mu_A-\mu_0$$ and solve for SE
4. Solve for *n*

### Example 1 Viewpoint 3
In an automobile production line, the time to assemble a door takes an average time with a standard deviation of 1.3 minutes. You hear of a new process that decreases the process by 0.29 minutes. You decide to test this by sampling *n* door assemblies to measure the time difference using the new procedure. How many door assemblies should you sample to get a power or 80%? Use a 5% level of significance.
1. $\alpha = 0.05$ for a standard normal distribution gives a z-score of $z_\alpha = -1.645$
    * $$z_\alpha SE = 1.645 SE$$ on a normal distribution with $\mu=0$ and $\sigma_\bar{x} = SE$
2. $\beta = 1-Power = 1-0.80 = 0.20$ for a standard normal distribution gives a z-score of $z_\beta = 0.842$
    * $$z_\beta SE = 0.842 SE$ for a standard normal distribution with $\mu=-0.29$ and $\sigma_\bar{x} = SE$
3. Minimum effect size = |-0.29| = 0.29. Take the differences
    $$\mu_A-\mu_0 = 0.842 SE - (-1.645 SE)$$
    $$0.29 = 2.487 SE$$
    $$SE = \frac{0.29}{2.487} = 0.1166$$
4. Solve for *n*, assuming both groups are the same size
    $$SE = \frac{\sigma}{\sqrt{n}}$$
    $$n = \left(\frac{\sigma}{SE}\right)^2 = \left(\frac{1.3}{0.1166}\right)^2 = 124.31$$

Minimum is 124.3, but we can only do whole numbers. So, we need to sample at least 125 doors from each method.

-----
# Homework
## Reading
* 7.4 Power calculations for a difference of means

## Exercises
1. Exercise 7.33 from section 7.4 exercises
2. Exercise 7.34 from section 7.4 exercises
3. Exercise 7.53 from chapter 7 exercises