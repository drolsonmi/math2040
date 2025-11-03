<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 20: Inference with 1-sample Quantitative Data
* __Note__: 

Resources for this lecture:

Remember:

## CLT for Quantitative Variables
When dealing with Confidence Intervals and Hypothesis Tests for Categorical data, we used the mean and standard error in our calculations.
$$\mu_{\hat{p}} = p \qquad \sigma_{\hat{p}}=SE_{\hat{p}}=\sqrt{\frac{p(1-p)}{n}}\tag{CLT for Categorical Variables}$$
$$ME=z_c\pm SE \tag{Confidence Intervals}$$
$$z = \frac{\hat{p}-p_0}{SE} \tag{Hypothesis Testing}$$

In addition to categorical variables, we can also take a quantitative variable and make it categorical by establishing a threshold and counting events above and below the threshold.

What if, however, we want to know the true mean? For example,
* What is the average age of students at Snow College?
* What is the average weight of a scoop of ice cream?
* What is the average wait-time at an Instacare?
* ...

We can follow many of the same processes. However, we have to look at the Central Limit Theorem differently.

### Sampling Distributions
> https://onlinestatbook.com/stat_sim/sampling_dist/index.html
>   * Sampling Distributions form Normal Distributions if they are large enough
>   * a

### CLT for Sample Mean
$$\mu_{\bar{x}}=\mu \qquad \sigma_{\bar{x}}=SE_{\bar{x}}=\frac{\sigma}{\sqrt{n}}\tag{CLT for Quantitative Variables}$$

> A restaurant earns about $13,000 a day with a standard deviation of $750.
> * What is the probability that they earn less than $12,500 in one day?
> $$P(x < \$12,500)\tag{$\mu = \$13,000~~~~\sigma = \$750$}$$
> $$z = \frac{x-\mu}{\sigma} = \frac{\$12,500 - \$13,000}{\$750} = -\frac{2}{3}$$
> $$P(z < -\frac{2}{3}) = 0.252$$
> * What is the probability that a sample of 45 days earns an average of less than $12,500 in one day?
>    * Think through this logically first. Should this be a higher or lower probability?
> $$P(\bar{x} < \$12,500)\tag{$\mu_{\bar{x}} = \$13,000~~~~SE = \frac{\$750}{\sqrt{45}}=\$111.80$}$$
> $$z = \frac{\bar{x}-\mu}{SE} = \frac{\$12,500 - \$13,000}{\$111.80} = -4.47$$
> $$P(z < -4.47) = 3.9*10^{-6}$$

The two conditions for the CLT to hold are the same for quantitative variables as they were for categorical variables, though the second is now calculated differently:
1. __Independence__ (random)
2. __Large Enough__
    * As a general rule, we say it's large enough if $n\ge 30$
    * > Show this in the simulator

> The average weight of a particular chocolate bar is claimed to be 20 ozs with a standard deviation of 0.7 ozs.
>   * What is the probability that a single chocolate bar is over 20.5 ozs?
>   * If you sample 40 chocolate bars, what is the probability that the sample mean is over 20.5 ozs? 

## T-Distribution
Everything we did above works beautifully if we know $\sigma$. However, we often don't. So, we have to approximate using the sample.
$$\sigma_{\bar{x}} = SE = \frac{\sigma}{\sqrt{n}} \approx \frac{s}{\sqrt{n}}$$

> Demonstrate on Desmos with $n$ as a variable

### Probabilities with the T-distribution
> Show on Desmos and TI-84

### Confidence Intervals
A sample of 56 gas stations show an average price of $3.25 for a gallon of unleaded gasoline with a standard deviation of $0.07. What is the 95% confidence interval for the true price of unleaded gasoline?
$$SE = \frac{s}{\sqrt{n}} = \frac{\$0.07}{\sqrt{56}} = \frac{\$0.07}{7.48} = 0.00935$$
$$ME = z_cSE = 1.96*0.00935 = 0.0183$$
$$x = \bar{x} \pm ME = \{\$3.25 - \$0.0183, \$3.25 + \$0.0183\} = \{\$3.232, \$3.268\}$$

We are 95% confident that the true average price of unleaded gasoline is between $3.232 and $3.268.

### Hypothesis Testing
A sample of 56 gas stations show an average price of $3.25 for a gallon of unleaded gasoline with a standard deviation of $0.07. If last year's average price of gas this time of year was $3.29, can we say with a 1% level of significance that gas is cheaper this year?
* H0: $\mu = 3.29$
* HA: $\mu < 3.29$
* $\alpha = 0.01$

$$t = \frac{\bar{x}-\mu_0}{SE} = \frac{\bar{x}-\mu_0}{s/\sqrt{n}} = \frac{3.25-3.29}{0.07/\sqrt{56}} = \frac{-0.04}{0.00935} = -4.278 $$
$$\text{p-value} = P(t<-4.278) = 0.00003816$$

Yes, there enough evidence to say with a 1% level of significance that gas prices are lower this year than they were last year.

-----
# Homework
## Reading
* 7.1 One-sample means with the *t*-distribution

## Exercises
1. Exercise 7.1 from section 7.1 exercises
2. Exercise 7.2 from section 7.1 exercises
3. Exercise 7.3 from section 7.1 exercises
4. Exercise 7.6 from section 7.1 exercises
5. Exercise 7.13 from section 7.1 exercises
6. Exercise 7.7 from section 7.1 exercises
7. Exercise 7.11 from section 7.1 exercises
