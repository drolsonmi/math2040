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
<title>Lab 5: Distributions</title>
</head>

# Lab 5 Distributions
In Lab 5, you are going to explore a dataset using different types of distributions. You will consider multiple variables, but the distribution you use depends on that variable. 

Remember there are two basic calculations with distributions:
- A __PDF__ (Probability Density Function) will give the __likelihood__ of the event. (For discrete distributions, this is also the probability.)
- A __CDF__ (Cumulative Density Function) will give the __probability__ of the event or the range of events.

We learned four different distributions. Here is a summary:

## Normal Distributions

$$z = \frac{x-\bar{x}}{s} \qquad or \qquad z = \frac{x-\mu}{\sigma}$$

## Geometric Distributions
The probability of success on the $n$-th trial

$$P(X=k) = (1-p)^{n-k} p \qquad E[X] = \frac{1}{p}$$

## Binomial Distributions
The probability of $k$ successes out of $n$ trials

$$P(X=k) = {}_nC_k p^k (1-p)^{n-k} \qquad P(X\le k) = P(X=0) + P(X=1) + \dots + P(X=k)$$


## Poisson Distributions
The probability of $k$ successes in a given amount of time

$$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

## Excel Calculations

Below is a table of all the commands you will need in Microsoft Excel to work with the 4 distributions we have discussed.

| __Normal Distribution__       | Excel Command                    |
| :---------------------------- | :------------------------------- |
| Probability (CDF)             | =NORM.DIST(x, mean, sd, TRUE)    |
| Density (PDF)                 | =NORM.DIST(x, mean, sd, FALSE)   |
| z-score                       | =(x-mean)/sd                     |
| Percentile (inverse CDF)      | =NORM.INV(probability, mean, sd) |
| Standard normal probabilities | =NORM.S.DIST(z, TRUE)            |
| Standard normal inverse       | =NORM.S.INV(probability)         |

| __Binomial Distribution__     | Excel Command                    |
| :---------------------------- | :------------------------------- |
| $P(X = k)$                    | =BINOM.DIST(k, n, p, FALSE)      |
| $P(X \le k)$                  | =BINOM.DIST(x, n, p, TRUE)       |
| Inverse binomial              | =BINOM.INV(n, p, probability)    |
| Combinations $\binom{n}{k}$   | =combin(n,k)                     |

$$E[X] = np \qquad P(X=k) = {}_nC_k p^k (1-p)^{n-k}$$

| __Poisson Distribution__      | Excel Command                    |
| :---------------------------- | :------------------------------- |
| $P(X = k)$                    | =POISSON.DIST(x, lambda, FALSE)  |
| $P(X \le k)$                  | =POISSON.DIST(x, lambda, TRUE)   |

Functions for the Geometric Distribution may or may not be programmed into Excel. You will need to calculate these manually.

$$E[X] = \frac{1}{p} \qquad P(X=k) = (1-p)^{k-1}p$$