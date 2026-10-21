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
<title>Lecture 16: Confidence Intervals</title></head>

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

### Finding the critical value
The __confidence level__ indicates how sure we are of these measurements. 
* Normal distribution - the confidence level is the area in the middle
  * > Demo on Desmos
  * The size of the tails (1-C) represents the chance that we could be wrong
  * This will be known as the level of significance when we discuss hypothesis testing
* The __critical value__ is the z-score that borders this area

> Demo: Desmos 1040-L20

### Finding the confidence interval
After you get your sample proportion $\hat{p}$,
* Find the standard error: $SE_\hat{p} = \sqrt{\fracc{\hat{p}(1-\hat{p})}{n}}$
* Find the margin of error: $ME = z_c SE$
* Calculate your confidence interval
  * $\hat{p} - ME \le p \le \hat{p} + ME$
* Conclusion
  * "I am ($C$)% confident that the true proportion of (variable being measured) is between ($\hat{p}-ME$) and ($\hat{p}+ME$)"

### Practice
> Give everyone a small handful of beans
> * Find the proportion of beans that are white
> * Gather and submit the data (Microsoft Forms: Bean Counter)
>
> If beans not available, Dice
> * Roll 10 dice 3 times and count all the 1's and 2's
> * Calculate the proportion of 1's and 2's in your sample of 30 rolls
>
> In your groups:
>   * Find the standard error ($SE_\hat{p}$)
>   * Find the margin of error using a 90% confidence level
>   * Find the 90% confidence interval for the true proportion
> 
> Together (in Desmos: [2040-CLT](https://www.desmos.com/calculator/ugpnvtiiyp))
>   * Plot each group's value and margin of error
>   * What are the mean and standard deviation? Do the match what we calculated?* 

## How does the sample size $n$ affect the confidence interval?

<iframe src="https://www.desmos.com/calculator/6nscq72swx?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

* [Desmos Demo of Confidence Interval](https://www.desmos.com/calculator/6nscq72swx)
  * As $n$ increases, $ME$ decreases
  * As $C$ increases, $z_c$ increases, and thus $ME$ increases

### What is the ideal sample size?

$$ME = z_c \sqrt{\frac{p_0(1-p_0)}{n}} \qquad\to\qquad n = \frac{1}{\hat{p}(1-\hat{p})}\left(\frac{z_c}{ME}\right)^2$$

What should be my sample size if I want the margin of error to be 0.10 at a 90% confidence level?
* Take $\hat{p} = 0.70$
* Unknown $\hat{p}$ (worst-case scenario: $\hat{p} = 0.50$)

-----
# Homework
(12 points)

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