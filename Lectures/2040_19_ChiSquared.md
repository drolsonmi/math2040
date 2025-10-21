# Lecture 19: Chi-Squared ($\chi^2$) Test
* __Note__: 

Resources for this lecture:

Remember:

## The Chi-Squared ($\chi^2$) test
Commonly used to,
* determine if the sample is representative of the general population when sample can be classified into several groups
  * evaluate whether two variables are independent
* evaluate whether data resemble a particular distribution (e.g., normal, geometric, binomial, ...)


### The $\chi^2$ test statistic
In the past, we calculated a z-score as,
$$Z = \frac{point~estimate - null~value}{SE}$$

However, we want to test if they collectively are irregularly far from zero. So, how do we get rid of the negatives? Square it!

$$\chi^2 = \frac{(point~estimate - null~value)^2}{SE}$$

### The Graph
The normal distribution has two factors: the mean and the standard deviation.

The $chi^2$ distribution has only one factor: the __degrees of freedom__
* Simply put, the __degrees of freedom__ represents the minimum number of values that can vary freely
* Typically, $df = n-1$ because once $n-1$ values are determined, the last value cannot vary.
    * Think of it this way. We're going to make up a dataset, counting students who attend an event. If we find the percentages of students from each grade level, we can make up a percentage for Freshmen, Sophomores, and Juniors. But once those three are made up, then the percentage for Seniors has to be a specific value so they all add up to 1.

So, what does the $\chi^2$ distribution look like?

> Look at the $\chi^2$ distribution on Desmos

When we have a $\chi^2$ distribution, we are going to get a test statistic, then find the p-value of the tail to the right of that test statistic.

## Examples
### Does the sample represent the general population?
Here are two examples:

__Example 1__: There are 100 multiple-choice questions on an exam (A,B,C,D). We expect there to be an equal number of A's, B's, C's, and D's. Looking at the exam, you count the questions with each answer. Are they equally distributed?
* $H_0$: All options are equally distributed (Any two categories are independent)
* $H_A$: Not all options are equally distributed (At least two categories are not independent)

| Category | Expected # | Actual # | $\frac{(X-E[X])^2}{E[X]}$  | $\chi^2$ Contribution |
| :------: | :--------: | :------: | :------------------------: | :-------------------: |
|    A     | 25         | 20       | $\frac{(20-25)^2}{25} = 1$ | 1                     |
|    B     | 25         | 20       | $\frac{(20-25)^2}{25} = 1$ | 1                     |
|    C     | 25         | 25       | $\frac{(25-25)^2}{25} = 0$ | 0                     |
|    D     | 25         | 35       | $\frac{(35-25)^2}{25} = 4$ | 4                     |

$\chi^2 = 1+1+0+4=6$

Because we're dealing with a squared value, the result of $\chi^2$ is always positive. So, this will almost always be a right-tailed test.

__Example 2__: A gummy bear factory does not produce equal amounts of each color. The colors make the following probability distribution:
| Color | Red   | Orange | Yellow | Green | Pink  | White |
| :---: | :---: | :----: | :----: | :---: | :---: | :---: |
| P(x)  | 0.18  | 0.14   | 0.20   | 0.18  | 0.17  | 0.13  |

You grab a few handfuls and get the following counts for 250 gummy bears. Assuming your sample is randomly selected, does your sample adequately represent the population? Use $\alpha=0.05$ (5% level of significance).
| Color     | Red   | Orange | Yellow | Green | Pink  | White |
| :-------: | :---: | :----: | :----: | :---: | :---: | :---: |
| In Sample | 42    | 36     | 49     | 44    | 40    | 39    |

* $H_0$: All categories are appropriately represented
* $H_A$: They are note appropriately represented
* $df = 6-1 = 5$
  * Look up on Desmos
* Find expected counts
* Find $\chi^2$
* Find p-value
* Answer the question

### Which distribution?


-----
# Homework
## Reading
* 

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises