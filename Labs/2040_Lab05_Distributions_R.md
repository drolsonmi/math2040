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
<title>Lab 5: Distributions (R)</title>
</head>

# Lab 5 Distributions (R)
In Lab 5, you are going to explore a dataset using different types of distributions. You will consider multiple variables, but the distribution you use depends on that variable. 

Remember there are two basic calculations with distributions:
- A __PDF__ (Probability Density Function) will give the __likelihood__ of the event. (For discrete distributions, this is also the probability.)
- A __CDF__ (Cumulative Distribution Function) will give the __probability__ of the event or the range of events.

We learned four different distributions. Here is a summary:

## Setup
All of these functions are built into base R, so no packages are needed. R names its distribution functions with a consistent prefix:
- `d` = density (PDF)
- `p` = probability (CDF)
- `q` = quantile (inverse CDF / percentile)

## Normal Distributions

$$z = \frac{x-\bar{x}}{s} \qquad or \qquad z = \frac{x-\mu}{\sigma}$$

Here is a table with all Normal Distribution functions within R

| __Normal Distribution__       | R Command                              |
| :---------------------------- | :------------------------------------- |
| Probability (CDF)             | `pnorm(x, mean, sd)`                   |
| Density (PDF)                 | `dnorm(x, mean, sd)`                   |
| z-score                       | `(x - mean) / sd`                      |
| Percentile (inverse CDF)      | `qnorm(probability, mean, sd)`         |
| Standard normal probabilities | `pnorm(z)`                             |
| Standard normal inverse       | `qnorm(probability)`                   |

If you leave out `mean` and `sd`, R assumes the standard normal (mean 0, sd 1).

## Geometric Distributions
The probability of success on the $n$-th trial

$$P(X = n) = (1-p)^{n-1} p \qquad E[X] = \frac{1}{p}$$

__Be careful:__ R's geometric functions count the number of *failures before* the first success, not the trial number. To match our formula, plug in $n - 1$.

| __Geometric Distribution__    | R Command                              |
| :---------------------------- | :------------------------------------- |
| $P(X = n)$                    | `dgeom(n - 1, p)`                      |
| $P(X = n)$ (by hand)          | `(1 - p)^(n - 1) * p`                  |
| $P(X \le n)$                  | `pgeom(n - 1, p)`                      |
| $E[X]$                        | `1 / p`                                |

## Binomial Distributions
The probability of $k$ successes out of $n$ trials

$$P(X=k) = \binom{n}{k} p^k (1-p)^{n-k} \qquad P(X\le k) = P(X=0) + P(X=1) + \dots + P(X=k)$$

Here is a table with all Binomial Distribution functions within R

| __Binomial Distribution__     | R Command                              |
| :---------------------------- | :------------------------------------- |
| $P(X = k)$                    | `dbinom(k, n, p)`                      |
| $P(X \le k)$                  | `pbinom(k, n, p)`                      |
| Inverse binomial              | `qbinom(probability, n, p)`            |
| Combinations $\binom{n}{k}$   | `choose(n, k)`                         |

## Poisson Distributions
The probability of $k$ successes in a given amount of time

$$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

Here is a table with all Poisson Distribution functions within R

| __Poisson Distribution__      | R Command                              |
| :---------------------------- | :------------------------------------- |
| $P(X = k)$                    | `dpois(k, lambda)`                     |
| $P(X \le k)$                  | `ppois(k, lambda)`                     |
