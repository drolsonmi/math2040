<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 14: Poisson Distribution
* Lab 3 on __Friday__
* Project 1 coming soon

Resources for this lecture:

Remember:

## Scenario
Wages
* Gather hourly wages of 500 randomly selected employees (we'll call this $X$)
* Calculate the mean (or Expected Value). The Expected Value is $E[X] = 12$.
* What is the probability, based on this average, that a randomly selected employee earns $11/hour?

The __Poisson Distribution__ looks at the probability of a certain number of events in a given time period. In this scenario, we are looking at the probability of earning a certain number of dollars in an hour.

## The Poisson Probability
Let's call the expected value $E[X] = \lambda$.
$$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

What is the probability, based on this average, that a randomly selected employee earns $11/hour?

$$P(X=11) = \frac{12^{11}e^{-12}}{11!} = \frac{743008370688\cdot 6.144*10^{-6}}{39916800} = 0.1144$$

## The Poisson Distribution
* Demonstrate in Desmos

```python
L = 12
d=poissondist(L)
a = [0...50]
0<y<d.pdf(a){a-0.4<x<a+0.4}
```

Other examples of the poisson distribution
* How many people run the stop sign on the NW corner of campus in a day during school hours (8-5)?
* How many items are sold in a week?
* How often does a certain model of car need repairs in a year?
* How many businesses go bankrupt in a month?

-----
# Homework
## Reading
* 4.5 Poisson distribution

## Exercises
1. Exercise 4.31 from section 4.5 exercises
2. Exercise 4.33 from section 4.5 exercises
3. Exercise 4.34 from section 4.5 exercises
