# Lecture 12: Distribution Probabilities

Resources for this lecture:
* Desmos, show a normal distribution with cdf

Remember:
* Continuous Distributions
* Z-scores

## Finding Probabilities in the Normal Distribution
* Instead of looking at the probability of a particular value, we are looking at the probability of it being in a range
  * $$P(80\le X \le 90) = \frac{\text{number of subjects between 80 and 90}}{\text{total sample size}} = \text{Area under the curve}$$

* Since finding the probability of a specific value is impossible, the height of the line no longer tells us the probability
  * The height of the line is known as the __likelihood__
  * The probability is found by calculating the area under the PDF that is within our range

### Area of a tail
> * Finding probability (area) on Desmos and on a TI-84
> * Z-Table
>
> For those who like to see the calculus, the equation of the normal curve is
>
> $$f(x)=\frac{1}{\sqrt{2\pi}} e^{x^2/2}$$
>
> To calculate the area, we take an integral:
>
> $$Area = \int_{-\infty}^z \frac{1}{\sqrt{2\pi}} e^{x^2/2} dx$$

* What is area of left tail up to z=-3? up to z=-2? up to z=-1?
* What is area of right tail above z=1? z=2? z=3?

### Complements
* Know left-tail, find right-tail
* We know area left of z=-1. What is area right of z=-1?

### Area of a central range
* Know left-tail, know right-tail, find center
* What is area between z=-1 and z=1?
* Empirical Rule


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
* 4.1.3 Finding tail areas
* 4.1.4 Normal Probability examples
* 4.1.5 68-95-99.7 rule
* 4.2.2 Geometric distribution

## Exercises
1. Exercise () from section () exercise
2. Exercise () from chapter () exercises
3. From Chapter 2 Exercises