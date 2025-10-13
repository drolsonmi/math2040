# Lecture 16: Confidence Intervals
* __Note__: 

Resources for this lecture:

Remember:

## The Confidence Interval
We have a sample statistic. We also have a standard error (related to the standard deviation). How can we use this to infer information about the population?
* Margin of error:  $ME = z_c SE$
* Confidence interval: a range of numbers the population's proportion is likely to be in
$$p = \hat{p} \pm ME \qquad \hat{p} - ME \le p \le \hat{p} + ME$$

This is known as a __confidence interval__.

## Finding the critical value
The __confidence level__ indicates how sure we are of these measurements. 
* Normal distribution - the confidence level is the area in the middle
  * > Demo on Desmos
  * The size of the tails (1-C) represents the chance that we could be wrong
  * This will be known as the level of significance when we discuss hypothesis testing
* The __critical value__ is the z-score that borders this area

> Demo: Desmos 1040-L20

### Practice
> Give everyone a small handful of beans
> * Find the proportion of beans that are white
> * Gather and submit the data (Microsoft Forms: Bean Counter)
>
> In your groups:
>   * Find the mean ($\mu_\hat{p}$) and the standard error ($SE_\hat{p}$)
>   * Find the margin of error using a 90% confidence level
>   * Find the 90% confidence level of the true proportion
> 
> Together (in Desmos: [2040-CLT](https://www.desmos.com/calculator/ugpnvtiiyp))
>   * Plot each group's value and margin of error
>   * What are the mean and standard deviation? Do the match what we calculated?* 

## What is the ideal sample size?
$$ME = z_c \sqrt{\frac{p_0(1-p_0)}{n}} \qquad\to\qquad n = $$

-----
# Homework
## Reading
* 5.2 Confidence intervals for a proportion
* 6.1.5 Choosing a sample size when estimating a proportion

## Exercises
1. What is the critical value for each of the following confidence levels?
    * C = 65%
    * C = 82%
    * C = 87%
    * C = 92%
    * C = 99.5%
2. Exercise 5.7 from section 5.2 exercises
3. Exercise 5.9 from section 5.2 exercises
4. Exercise 5.12 from section 5.2 exercises
5. Exercise 5.13 from section 5.2 exercises
6. Exercise 5.27 from chapter 5 exercises