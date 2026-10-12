# Lab 5 Distributions

A __PDF__ (Probability Density Function) will give the __likelihood__ of the event. (For discrete distributions, this is also the probability.)

A __CDF__ (Cumulative Density Function) will give the __probability__ of the event or the range of events.

Below is a table of all the commands you will need in Microsoft Excel to work with the 4 distributions we have discussed.

| Normal Distribution           | Excel Command                    |
| :---------------------------- | :------------------------------- |
| Probability (CDF)             | =NORM.DIST(x, mean, sd, TRUE)    |
| Density (PDF)                 | =NORM.DIST(x, mean, sd, FALSE)   |
| z-score                       | =(x-mean)/sd                     |
| Percentile (inverse CDF)      | =NORM.INV(probability, mean, sd) |
| Standard normal probabilities | =NORM.S.DIST(z, TRUE)            |
| Standard normal inverse       | =NORM.S.INV(probability)         |

| Binomial Distribution         | Excel Command                    |
| :---------------------------- | :------------------------------- |
| $P(X = k)$                    | =BINOM.DIST(k, n, p, FALSE)      |
| $P(X \le k)$                  | =BINOM.DIST(x, n, p, TRUE)       |
| Inverse binomial              | =BINOM.INV(n, p, alpha)          |

| Poisson Distribution          | Excel Command                    |
| :---------------------------- | :------------------------------- |
| $P(X = k)$                    | =POISSON.DIST(x, lambda, FALSE)  |
| $P(X \le k)$                  | =POISSON.DIST(x, lambda, TRUE)   |

| Geometric Distribution        | Excel Command                    |
| :---------------------------- | :------------------------------- |
| $P(X = k)$                    | =GEOM.DIST(x, p, FALSE)          |
| $P(X \le k)$                  | =GEOM.DIST(x, p, TRUE)           |