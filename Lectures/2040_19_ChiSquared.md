# Lecture 19: Chi-Squared ($\chi^2$) Test
* __Note__: 

Resources for this lecture:

Remember:

## The Chi-Squared ($\chi^2$) test
Commonly used to,
* determine if the sample is representative of the general population when sample can be classified into several groups
* evaluate whether data resemble a particular distribution (e.g., normal, geometric, binomial, ...)
* evaluate whether two variables are independent

### The $\chi^2$ test statistic
In the past, we calculated a z-score as,
$$Z = \frac{point~estimate - null~value}{SE}$$

However, we want to test if they collectively are irregularly far from zero. 

## Examples
### Does the sample represent the general population?


### Which distribution?


### Testing for Independence
* $H_0$: Two categories are independent
* $H_A$: Two categories are not independent

| Category | Expected # | Actual # | $\frac{(X-E[X])^2}{E[X]}$  | $\chi^2$ Contribution |
| :------: | :--------: | :------: | :------------------------: | :-------------------: |
|    A     | 25         | 20       | $\frac{(20-25)^2}{25} = 1$ | 1                     |
|    B     | 25         | 20       | $\frac{(20-25)^2}{25} = 1$ | 1                     |
|    C     | 25         | 25       | $\frac{(25-25)^2}{25} = 0$ | 0                     |
|    D     | 25         | 35       | $\frac{(35-25)^2}{25} = 4$ | 4                     |

$\chi^2 = 1+1+0+4=6$

Because we're dealing with a squared value, the result of $\chi^2$ is always positive. So, this will almost always be a right-tailed test.

### Sample Variance


## Standard Deviation


## Behavior of the Standard Deviation
> Demo

## Class Practice
Duke Forest dataset --> 
* Find the variance and the standard deviation of the square footage for the first 30 houses
> 6040	4475 	1745 	2091 	1772
> 1950	3909	2841	3924	2173
> 2091	2492	2200	3889	3169
> 2750	3234	2933	3831	2414
> 1416	2300	1932	2786	2830
> 3487	1831	1935	2015	2526


-----
# Homework
## Reading
* 

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises