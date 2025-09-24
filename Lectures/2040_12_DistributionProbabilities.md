# Lecture 9: Distribution Probabilities
*  

Resources for this lecture:

Remember:
* Continuous Distributions
* Z-scores

## Finding Probabilities in the Normal Distribution
* Instead of looking at the probability of a particular value, we are looking at the probability of it being in a range
  * $$P(80\le X \le 90) = \frac{\text{number of subjects between 80 and 90}}{\text{total sample size}} = \text{Area under the curve}$$

* Since finding the probability of a specific value is impossible, the height of the line no longer tells us the probability
  * The height of the line is known as the __likelihood__
  * The probability is found by calculating the area under the PDF that is within our range

* Finding areas
  * Empirical Rule

> * Finding probability (area) on Desmos and on a TI-84
> * Z-Table

## Other Distributions
Normal distributions are only one type of distribution. Others we'll see:
* Geometric Distribution
* Binomial Distribution
* Poisson Distribution

## Geometric Distributions

* Probability of finding the first success in the 1st trial $= p$
* Probability of finding the first success in the 2nd trial $= (1-p)p$
* Probability of finding the first success in the 3rd trial $= (1-p)^2p$
* Probability of finding the first success in the 4th trial $= (1-p)^3p$
* Probability of finding the first success in the *n*-th trial $= (1-p)^{n-1}p$

$$\mu = \frac{1}{p} \qquad \sigma = \sqrt{\frac{1-p}{p^2}}$$

> Desmos:
> 
> ```python
> p = 0.5
> g = geodist(p)
> a = [1,...,30]
> 0 < y < g.pdf(a) {a-0.4 < x < a+0.4}
> ```

-----
# Homework
## Reading
* 

## Exercises
* Exercise () from section () exercise
* Exercise () from chapter () exercises
  * 
* From Chapter 2 Exercises
  * Exercises 