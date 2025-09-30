# Lecture 13: Binomial Distributions
* Lab 3 on __Friday__
* Project 1 coming soon

Resources for this lecture:

## Other Distributions
Normal distributions are only one type of distribution. Others we'll see:
* Geometric Distribution
* Binomial Distribution
* Poisson Distribution

## Bernoulli Trials
A __Bernoulli random variable__ is a variable that only has two possible outcomes. We often indicate these as a "Success" or a "Failure".
* Yes/No questions
* In a category/Not in a category
* Success/Fail questions

## Geometric Distributions
Flip a coin. (This is a Bernoulli variable.)
* P(H) = 0.5
* P(TH) = P(T and H) = 0.5 * 0.5 = 0.25
* P(TTH) = P(T and T and H) = 0.5 * 0.5 * 0.5=0.125
* P(TTTH) = P(T and T and T and H) = 0.5 * 0.5 * 0.5 * 0.5 = 0.0625

Geometric Distribution is the distribution of probabilities of a successful outcome on the n-th trial.

Let $p$ be the probability of a successful trial.
* Probability of finding the first success in the 1st trial $= P(S) = p$
* Probability of finding the first success in the 2nd trial $= P(FS) = P(F and S) = (1-p)p$
* Probability of finding the first success in the 3rd trial $= P(FFS) = P(F and F and S) = (1-p)^2p$
* Probability of finding the first success in the 4th trial $= P(FFFS) = (1-p)^3p$
* Probability of finding the first success in the *n*-th trial $= P(S on nth trial) = (1-p)^{n-1}p$

$$\mu = \frac{1}{p} \qquad \sigma = \sqrt{\frac{1-p}{p^2}}$$

> Desmos:
> 
> ```python
> p = 0.5
> g = geodist(p)
> a = [1,...,30]
> 0 < y < g.pdf(a) {a-0.4 < x < a+0.4}
> ```

### Normal approximation to binomial distribution
$$\mu = \frac{1}{p}\qquad \sigma=\sqrt{\frac{1-p}{p^2}}$$


## Binomial Distributions
One study shows that 57% of people surveyed like pineapple on pizza
* Experiment: Do you like pineapple on your pizza?
  * Only 2 options: Yes or No
  * $$p$$ is the proportion of students answering "Yes"
* Probability that out of 5 people, 3 say yes

$$\begin{align*}
  P(X=3) &= (Combination)*P(YYYNN) \\
         &= (Combination)*P(Y)*P(Y)*P(Y)*P(N)*P(N) \\
         &= (Combination)*p*p*p*(1-p)*(1-p) \\
         &= (Combination)p^3(1-p)^{5-3}
\end{align*}$$

### Combinations
The 5 people in our example can be rearranged: {YYYNN, YYNYN, YNYYN, NYYYN, YYNNY, YNYNY, NYYNY, YNNYY, NYNYY, NNYYY}

The method to calculate the number of ways we can get *k* successes from a sample of *n* is called a __combination__. 

$${}_nC_k=\begin{pmatrix}n\\ k\end{pmatrix} = \frac{n!}{k!(n-k)!}$$

where $$n! = n(n-1)(n-2)(n-3)...*3*2*1 = \prod_{k=1}^n k$$. We often use the phrase "n choose k" to describe the combination $$\begin{pmatrix}n\\k\end{pmatrix}$$.

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
|   k    |    0   |    1   |    2   |    3   |    4   |    5   |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| P(X=k) | P(X=0) | P(X=1) | P(X=2) | P(X=3) | P(X=4) | P(X=5) |
|        | 0.0147 | 0.0974 | 0.2583 | 0.3424 | 0.2270 | 0.0602 |

* Show on Desmos for the pizza example

### Normal approximation to binomial distribution
$$\mu=np \qquad \sigma=\sqrt{np(1-p)}$$

* Show on Desmos for the pizza example

## Practice Example
Duke Forest dataset
  • How many houses were built before 1975?

> 75 out of the sample of 98. That is $p=0.7653$.

A real estate salesman has a client who wants a sampling of houses that are for sale. If the salesman randomly chooses 15 houses, what are the chances that exactly 10 of them were built before 1975?

> $$ \begin{align*} P(X=11) &= \begin{pmatrix}15\\11\end{pmatrix} p^{11}(1-p)^{15-11}\\ &= \frac{15!}{11!(15-11)!}(0.7653)^{11}(1-0.7653)^{15-11}\\ &= \frac{1307674368000}{39916800\cdot 24}(0.7653)^{11}(0.2347)^4 \\ &= 1365\cdot 0.0527\cdot 0.00303 \\ &= 0.2180\end{align*}$$
>
> On a TI-84, `binomcdf(15,75/98,11)` gives 0.2184

What are the chances that at least 11 of them were built before 1975?

> We can use a TI-84 or Desmos
> $$P(X\ge 11) = P(X=11 OR X=12 OR X=13 OR X=14 OR X=15)$$
> $$P(X=11) = 0.2184$$
> $$P(X=12) = 0.2374$$
> $$P(X=13) = 0.1787$$
> $$P(X=14) = 0.0832$$
> $$P(X=15) = 0.0181$$
>
> $$P(X\ge 11) = P(X=11) + P(X=12) + P(X=13) + P(X=14) + P(X=15) = 0.7359$$

-----
# Homework
## Reading
* 4.2 Geometric distribution
* 4.3 Binomial distribution

## Exercises
* Exercise 4.11 from section 4.2 exercise
* Exercise 4.13 from section 4.2 exercise
* Exercise 4.17 from section 4.3 exercise
* Exercise 4.19 from section 4.3 exercise
* Exercise 4.18 from section 4.3 exercise
* Exercise 4.20 from section 4.3 exercise
* Exercise 4.22 from section 4.3 exercise
* Exercise 4.23 from section 4.3 exercise
