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
    $$\alpha = P(Reject~H_0 | H_0~is~true)$$
  > Highlight p-value
* Complement of p-value (confidence level) is probability of correctly saying H0 is true:
    $$P(Fail~to~reject~H_0 | H_0~is~true) = 1 - P(Reject~H_0 | H_0~is~true)$$

Now, we consider if H0 is not true
* If H0 is not true, then HA is true, and the true mean is around $\mu_1$
  > Draw another normal distribution around $\mu_1$
* Probability of a Type II Error is the tail of this second distribution that goes into the area of the Confidence Level
    $$P(Fail~to~reject~H_0 | H_0~is~not~true)$$
* The rest of the area in the HA normal distribution is the probability that we accurately reject H0. This is __power__. In short, this is the probability that we successfully reject the 
    $$Power = P(Reject~H_0 | H_0~is~not~true)$$

## How to increase the power
1. Increase significance level ($\alpha$) --> This increases the power, but also increases *P(Type I Error)*.
2. Increase sample size ($n$) --> Makes both distributions narrower
3. Decrease variability ($s$) --> Makes both distributions narrower (don't have control over this)
4. Increase separation between point estimate and null value --> (don't have control over this)

> Vary each of these in Desmos

## Example


-----
# Homework
## Reading
* 

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises