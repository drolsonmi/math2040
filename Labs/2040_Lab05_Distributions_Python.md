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
<title>Lab 5: Distributions (Python)</title>
</head>

# Lab 5 Distributions (Python)
In Lab 5, you are going to explore a dataset using different types of distributions. You will consider multiple variables, but the distribution you use depends on that variable. 

Remember there are two basic calculations with distributions:
- A __PDF__ (Probability Density Function) will give the __likelihood__ of the event. (For discrete distributions, this is also the probability.)
  - This can also be called a *PMF* (Probability Mass Function), and is referred to that way in some python commands
- A __CDF__ (Cumulative Distribution Function) will give the __probability__ of the event or the range of events.

We learned four different distributions. Here is a summary:

## Setup
All of the distribution functions below come from the `scipy.stats` module. Run this once at the top of your script or notebook:

```python
from scipy.stats import norm, geom, binom, poisson
from math import comb
```

## Normal Distributions

$$z = \frac{x-\bar{x}}{s} \qquad or \qquad z = \frac{x-\mu}{\sigma}$$

Here is a table with all Normal Distribution functions within Python

| __Normal Distribution__       | Python Command                         |
| :---------------------------- | :------------------------------------- |
| Probability (CDF)             | `norm.cdf(x, loc=mean, scale=sd)`      |
| Density (PDF)                 | `norm.pdf(x, loc=mean, scale=sd)`      |
| z-score                       | `(x - mean) / sd`                      |
| Percentile (inverse CDF)      | `norm.ppf(probability, loc=mean, scale=sd)` |
| Standard normal probabilities | `norm.cdf(z)`                          |
| Standard normal inverse       | `norm.ppf(probability)`                |

If you leave out `loc` and `scale`, Python assumes the standard normal (mean 0, sd 1).

## Geometric Distributions
The probability of success on the $n$-th trial

$$P(X = n) = (1-p)^{n-1} p \qquad E[X] = \frac{1}{p}$$

Python's `geom` uses the same definition as our formula ($n$ = the trial on which the first success happens), so you can use it directly or calculate by hand.

| __Geometric Distribution__    | Python Command                         |
| :---------------------------- | :------------------------------------- |
| $P(X = n)$                    | `geom.pmf(n, p)`                       |
| $P(X = n)$ (by hand)          | `(1 - p)**(n - 1) * p`                 |
| $P(X \le n)$                  | `geom.cdf(n, p)`                       |
| $E[X]$                        | `1 / p`                                |

## Binomial Distributions
The probability of $k$ successes out of $n$ trials

$$P(X=k) = \binom{n}{k} p^k (1-p)^{n-k} \qquad P(X\le k) = P(X=0) + P(X=1) + \dots + P(X=k)$$

Here is a table with all Binomial Distribution functions within Python

| __Binomial Distribution__     | Python Command                         |
| :---------------------------- | :------------------------------------- |
| $P(X = k)$                    | `binom.pmf(k, n, p)`                   |
| $P(X \le k)$                  | `binom.cdf(k, n, p)`                   |
| Inverse binomial              | `binom.ppf(probability, n, p)`         |
| Combinations $\binom{n}{k}$   | `comb(n, k)`                           |

## Poisson Distributions
The probability of $k$ successes in a given amount of time

$$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

Here is a table with all Poisson Distribution functions within Python

| __Poisson Distribution__      | Python Command                         |
| :---------------------------- | :------------------------------------- |
| $P(X = k)$                    | `poisson.pmf(k, lam)`                  |
| $P(X \le k)$                  | `poisson.cdf(k, lam)`                  |

Note: `lambda` is a reserved word in Python, so use a different variable name such as `lam`.
