# Lecture 6: Variance and Standard Deviations
Resources for this lecture:
* [Desmos: Variance](https://www.desmos.com/calculator/780ec2028e)

Remember:
* $\mu$ indicates the mean of a population
* $\bar{x}$ indicates the mean of a sample

## Variance
Take the following datasets and ask the students to explain the difference. (Perhaps draw a boxplot of these)
* {1, 4, 5, 6, 9}
* {1, 2, 5, 8, 9}

Variance measures how spread out the data is. To do this, let's just compare each value to the mean:
$$x_i - \mu\tag{Deviation}$$

We could then take the average of all deviations. The problem is that this average would always be 0 since the mean is the middle point, meaning there is as much deviation between points on its left as on its right. We have to get rid of negatives.

$$\sigma^2  = \frac{\sum (x_i - \mu)^2}{n}\tag{Population Variance}$$

By squaring the deviation, we do 2 things:
1. Get rid of the negatives
2. Exaggerate the deviations ("reward" the points close to the mean, "penalize" the points further from the mean)

### Sample Variance
The calculation of $\sigma^2$ is the calculation for the entire population. If we are only taking a sample, however, then our calculation isn't perfect. We take into account our __degrees of freedom__ or "the number of sample values that can vary after certain restrictions have been imposed on all data values". (Triola, *Essentials of Statistics*, 6th Edition). In short, we have to make restrictions on a number of datapoints, and the degrees of freedom is the number of remaining datapoints that can vary freely.

In the case of 1 sample, we have $n-1$ degrees of freedom. So, our variance is divided by $n-1$ instead of $n$.
$$s^2  = \frac{\sum (x_i - \bar{x})^2}{n-1}\tag{Sample Variance}$$

* Demonstrate this calculation on Desmos (link above)

## Standard Deviation
We squared the deviations to get rid of the negatives. But now we have to get rid of the square by taking a square root. The result is the __standard deviation__.

$$\sigma  = \sqrt{\frac{\sum (x_i - \mu)^2}{n}} \qquad s  = \sqrt{\frac{\sum (x_i - \bar{x})^2}{n-1}}\tag{Standard Deviation}$$

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
* 2.1.4 Variance and Standard Deviation

## Exercises
* From section 2.1
  * Exercises 2.9