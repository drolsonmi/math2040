# Lecture 19: Chi-Squared ($\chi^2$) Test
* __Notes__: 
  * Lab 4 on Friday, Oct 24 - Bring your laptops
  * Exam 2 on Wednesday, Oct 29 (2 weeks from today)


## The Chi-Squared ($\chi^2$) test
Commonly used to,
* determine if the sample is representative of the general population when sample can be classified into several groups
  * evaluate whether two variables are independent
* evaluate whether data resemble a particular distribution (e.g., normal, geometric, binomial, ...)


### The $\chi^2$ test statistic
In the past, we calculated a z-score as,
$$Z = \frac{point~estimate - null~value}{SE}$$

However, we want to test if they collectively are irregularly far from zero. So, how do we get rid of the negatives? Square it! Squaring it will do two things:
1. eliminate the negative
2. Any differences that are already large will become larger and stand out more

We do this for all points in our dataset:

$$\chi^2 = Z_1^2 + Z_2^2 + Z_3^2 + ...$$

There is another way to calculate $$\chi^2$$ which is more common, using the counts of each category:

$$\chi^2 = \sum \frac{(category~count - null~count)^2}{null~count}$$

The book uses the term, "null count". Really, this is the expected value, or the expected count. 

### Example 1: Does the sample represent the general population?
There are 100 multiple-choice questions on an exam (A,B,C,D). We expect there to be an equal number of A's, B's, C's, and D's. Looking at the exam, you count the questions with each answer. Are they equally distributed?
* $H_0$: All options are equally distributed (Any two categories are independent)
* $H_A$: Not all options are equally distributed (At least two categories are not independent)

| Category | Expected # | Actual # | $\frac{(X-E[X])^2}{E[X]}$  | $\chi^2$ Contribution |
| :------: | :--------: | :------: | :------------------------: | :-------------------: |
|    A     | 25         | 20       | $\frac{(20-25)^2}{25} = 1$ | 1                     |
|    B     | 25         | 20       | $\frac{(20-25)^2}{25} = 1$ | 1                     |
|    C     | 25         | 25       | $\frac{(25-25)^2}{25} = 0$ | 0                     |
|    D     | 25         | 35       | $\frac{(35-25)^2}{25} = 4$ | 4                     |

$\chi^2 = 1+1+0+4=6$

### The Graph
The normal distribution has two factors: the mean and the standard deviation.

The $chi^2$ distribution has only one factor: the __degrees of freedom__
* Simply put, the __degrees of freedom__ represents the minimum number of values that can vary freely
* Typically, $df = n-1$ because once $n-1$ values are determined, the last value cannot vary.
    * Think of it this way. We're going to make up a dataset, counting students who attend an event. If we find the percentages of students from each grade level, we can make up a percentage for Freshmen, Sophomores, and Juniors. But once those three are made up, then the percentage for Seniors has to be a specific value so they all add up to 1.

Because we're dealing with a squared value, the result of $\chi^2$ is always positive. So, this will almost always be a right-tailed test.

So, what does the $\chi^2$ distribution look like?

> Look at the $\chi^2$ distribution on Desmos

When we have a $\chi^2$ distribution, we are going to get a test statistic, then find the p-value of the tail to the right of that test statistic.

## Example 2: M&M's
Mars, Inc. claims that the colors of their basic M&M's candy have the following probability distribution:
| Color | Brown | Yellow | Red    | Orange | Green | Blue  |
| :---: | :---: | :----: | :----: | :----: | :---: | :---: |
| P(x)  | 0.30  | 0.20   | 0.20   | 0.10   | 0.10  | 0.10  |

You wonder if this is true. So, you grab a few handfuls and get the following counts for 250 M&M's. Assuming your sample is randomly selected, does your sample adequately represent the population? Use $\alpha=0.05$ (5% level of significance).
| Color     | Brown | Yellow | Red    | Orange | Green | Blue  |
| :-------: | :---: | :----: | :----: | :----: | :---: | :---: |
| In Sample | 69    | 51     | 47     | 22     | 26    | 35    |
| Expected  | 75    | 50     | 50     | 25     | 25    | 25    |

* $H_0$: All colors are appropriately represented
* $H_A$: They are not appropriately represented
* $df = 6-1 = 5$
  * Look up graph on Desmos
* Find expected counts
* Find $\chi^2$
* Find p-value
* Answer the question

| Color             | Brown | Yellow | Red    | Orange | Green | Blue  |
| :---------------: | :---: | :----: | :----: | :----: | :---: | :---: |
| In Sample         | 69    | 51     | 47     | 22     | 26    | 35    |
| Expected          | 75    | 50     | 50     | 25     | 25    | 25    |
| (x-E[x])^2 / E[x] | 0.48  | 0.02   | 0.18   | 0.36   | 0.04  | 4     |

$$\chi^2 = 0.48+0.02+0.18+0.36+0.04+4 = 5.08$$

Find the p-value
* Desmos: `chisqdist(5)`
* TI-84: `D:chi^2GOF-Test`

$$p-value=P(\chi^2>5.08) = 0.406 > 0.10$$
* Fail to reject H0
* Therefore the distribution appears to agree with the advertisement

Your friend decides to go all-in and counts 3,000 M&M's.

| Color             | Brown | Yellow | Red    | Orange | Green | Blue  |
| :---------------: | :---: | :----: | :----: | :----: | :---: | :---: |
| In Sample         | 904   | 597    | 589    | 308    | 312   | 290   |
| Expected          | 900   | 600    | 600    | 300    | 300   | 300   |
| (x-E[x])^2 / E[x] | 0.018 | 0.015  | 0.202  | 0.213  | 0.48  | 0.333 |

$$\chi^2 = 0.018+0.015+0.202+0.213+0.48+0.333 = 1.261$$

$$p-value = P(\chi^2 > 1.261) = 0.939$$
* Fail to reject H0
* Therefore the distribution appears to agree with the advertisement

## Conditions for the Chi-square Test
* __Independence__. Each case that contributes a count to the table must be independent of all the other cases in the table.
* __Sample size / distribution__. Each particular scenario (in other words, each cell count) must have at least 5 expected cases.

### Which distribution?
Let's look again at some house square footages from our Duke Forest dataset:
<pre>
6040	4475 	1745 	2091 	1772
1950	3909	2841	3924	2173
2091	2492	2200	3889	3169
2750	3234	2933	3831	2414
1416	2300	1932	2786	2830
3487	1831	1935	2015	2526
</pre>

Is this data normal? If it is, then the normal distribution will follow the mean and standard deviation of our data.
* Mean is $\bar{x} = 2766.033$
* Standard Deviation is $s = 1000.38$

Now, let's look at a few percentiles. The expected values will follow the normal distribution. 
* Find the z-score for the nth percentile
* Solve for x
$$z = \frac{x-\bar{x}}{s} \qquad\to\qquad x = zs + \bar{x}$$

> In Python, copy in data and find the percentiles
> ```python
> import numpy as np
> # Find the percentiles
> A = np.array([6040,4475,1745,2091,1772,1950,3909,2841,3924,2173,2091,2492,2200,3889,3169,2750,3234,2933,3831,2414,1416,2300,1932,2786,2830,3487,1831,1935,2015,2526])
> np.percentile(A,[20,25,30,40,50,60,70,75,80])
> 
> # Find what they should be on a normal distribution
> import scipy.stats as stats
> stats.norm.ppf([0.20,0.25,0.30,0.40,0.50,0.60,0.70,0.75,0.80], loc=A.mean(), scale=A.std())
> ```

| Percent           | 20     | 25     | 30     | 40     | 50     | 60     | 70     | 75     | 80     |
| :---------------- | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| Percentile        | 1947   | 2034   | 2091   | 2260   | 2509   | 2803.6 | 3003.8 | 3217.8 | 3555.8 |
| Expected          | 1938.2 | 2102.6 | 2250.2 | 2516.8 | 2766.0 | 3015.2 | 3281.8 | 3429.4 | 3593.8 |
|                   |        |        |        |        |        |        |        |        |        |
| (x-E[x])^2 / E[x] | 0.040  | 2.240  | 11.270 | 26.212 | 23.885 | 14.852 | 23.552 | 13.067 | 0.402  |

$$\chi^2 = 115.520 \qquad p-value=P(\chi^2>115.520) = 2.8*10^{-21} < 0.01$$

## Independence in two-way tables
What we have seen so far is a goodness of fit, checking how proportions of 1 variable fit with expected counts. What if we have 2 variables? 

For example, I want to see how well students have passed my MATH 1025 class between the 3 main modalities:

| Counts     | In-person | Online | IVC    | __Total__ |
| :--------- | :-------: | :----: | :----: | :-------: |
| Passed     | 24        | 21     | 18     | __63__    |
| Failed     | 3         | 4      | 2      | __9__     |
| __Total__  | __27__    | __25__ | __20__ | __*72*__  |

The proportion of those that passed was 63/72 = 0.875. The proportion of those that failed was 9/72 = 0.125. Assuming this proportion is good for all categories, what are my expected counts? Use a level of significance of 10%.

| Expected Counts | In-person       | Online          | IVC           |
| :-------------- | :-------------: | :-------------: | :-----------: |
| Passed          | 0.875*27=23.625 | 0.875*25=21.875 | 0.875*20=17.5 |
| Failed          | 0.125*27=3.375  | 0.125*25=3.125  | 0.125*20=2.5  |

* H0:  The counts appropriately represent the expected counts (in other words, the proportion of those that passed is around 0.875 for all categories)
* HA:  The counts do not represent the expected counts (in other words, it is not consistently 0.875 of all students that pass)

Now, we find the $\chi^2$ test statistic.
$$\ch^2 = \frac{(24-23.625)^2}{23.625} + \frac{(21-21.875)^2}{21.875} + \frac{(18-17.5)^2}{17.5} + \frac{(3-3.375)^2}{3.375} + \frac{(4-3.125)^2}{3.125} + \frac{(2-2.5)^2}{2.5}$$
$$\chi^2=0.00595 + 0.035 + 0.01429 + 0.04167 + 0.245 + 0.1 = 0.44191$$
$$df = (\text{\# of rows} - 1)*(\text{\# of columns}-1) = (2-1)*(3-1)=1*2=2$$
$$p-value=0.802$$

We fail to reject the null hypothesis, so the assumption that the counts appropriately represent the expected counts stands. Approximately 87.5% of students in my MATH 1025 class pass, regardless of the modality.

-----
# Homework
## Reading
* 6.3 Testing for goodness of fit using chi-square

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises