<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 12: Normal Distribution
* Lab 3 on __Friday__
* Project 1 coming soon

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
> $$f(x)=\frac{1}{\sqrt{2\pi}} e^{-x^2/2}$$
>
> To calculate the area, we take an integral:
>
> $$Area = \int_{-\infty}^z \frac{1}{\sqrt{2\pi}} e^{-x^2/2} dx$$

* What is area of left tail up to z=-3? up to z=-2? up to z=-1?
* What is area of right tail above z=1? z=2? z=3?

### Complements
* Know left-tail, find right-tail
* We know area left of z=-1. What is area right of z=-1?

### Area of a central range
* Know left-tail, know right-tail, find center
* What is area between z=-1 and z=1?
* Empirical Rule

## Finding z-scores knowing the probabilities
What is the value of z for this probability?
$$P(a\le z \le b) = 0.25$$
* Reverse engineer on a z-table
* Desmos
* TI-84

-----
# Homework
## Reading
* 4.1.3 Finding tail areas
* 4.1.4 Normal Probability examples
* 4.1.5 68-95-99.7 rule
* 4.2.2 Geometric distribution

## Exercises
1. Exercise 4.3(e-h) from section 4.1 exercises
  * You did parts a-d in lesson 11 homework
2. Exercise 4.5 from section 4.1 exercises
3. Exercise 4.7 from section 4.1 exercises
4. Exercise 4.9 from section 4.1 exercises
5. Exercise 4.36 from chapter 4 exercises