# Lecture 13: Binomial Distributions
* __Note__: 

Resources for this lecture:

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

## Binomial Distributions
### Binomial Categories
* Experiment: Do you like pineapple on your pizza?
  * Only 2 options: Yes or No
  * $$p$$ is the proportion of students answering "Yes"
* Probability that out of 5 people, 3 say yes

$$P(X=3) = (Combination)*P(YYYNN) = (Combination)*P(Y)*P(Y)*P(Y)*P(N)*P(N)$$
$$P(X=3) = (Combination)*p*p*p*(1-p)*(1-p) = (Combination)p^3(1-p)^{5-3}$$

### Combinations
The 5 people in our example can be rearranged: {YYYNN, YYNYN, YNYYN, NYYYN, YYNNY, YNYNY, NYYNY, YNNYY, NYNYY, NNYYY}

The method to calculate the number of ways we can get *k* successes from a sample of *n* is called a __combination__. 

$${}_nC_k=\begin{pmatrix}n\\ k\end{pmatrix} = \frac{n!}{k!(n-k)!}$$

where $$n! = n(n-1)(n-2)(n-3)...*3*2*1$$.

### Binomial Probabilities
The full equation for the probability of *k* results in a binomial experiment is
$$P(X=k) = \begin{pmatrix}n\\ k\end{pmatrix}p^k(1-p)^{n-k}$$

Going back to the pineapple problem, let's say that 40% of people like pineapple on their pizza. Then the probability that 3 out of 5 people say yes would be,
$$\begin{align*}
  P(X=3) &= \begin{pmatrix}5\\ 3\end{pmatrix}p^3(1-p)^2 \\
    &= 10*(0.40)^3(0.60)^2 \\
    &= 10(0.064)(0.36) \\
    &= 0.2304\end{align*}$$

### Binomial Distributions

### Normal approximation to binomial distribution
$$\mu=np \qquad \sigma=\sqrt{np(1-p)}$$

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