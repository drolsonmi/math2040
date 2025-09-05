# Lecture 7: 5-Number Summary and Boxplots
Resources:
* Microsoft Excel
* Desmos

## Measuring the middle of the data
* Mean
* Mode
* Median

When data is symmetric, these will be the same. If they are not symmetric, then
* the mean is heavily influenced by outliers
* the median is somewhat influenced by outliers
* the mode is not influenced by outliers and remains unchanged

(Draw a normal distribution to show symmetry, then show a skewed dataset)

## Finding the Median
* List the numbers in order
* Find the middle point
    * If the middle point is on a value, the median is that value
    * If the middle point is between two values, the median is the average of the two values

> * Have 11 students choose a random number between 0 and 20
> * Find the median
> * Add a value of 20 to the end of the list so there are 12 values
> * Find the median

## Quartiles
The measurement of quartiles can be inclusive or exclusive, meaning it includes or excludes the endpoints
* TI-84 is inclusive
* Excel has a function for each
  * If the median is a value in the dataset, then excel will weight half the median (find the quartile with the median and the quartile without the median, then average the two)

5-number summary
* Boxplot
> * Create the scale (Numberline from 0 to 20)
> * Create the label ("Random numbers from class")
> * Draw the 5 numbers
> * Create boxplot
> * Identify lowest 25%, highest 25%, and the IQR

## Outliers
* Any value larger than 1.5*IQR
* Any value smaller than 1.5*IQR

## Class Practice
Duke Forest dataset --> 
* Find 5-number summary of square footage for the first 30 houses and make a boxplot
* Identify the IQR and any outliers
> 6040  4475 	1745 	2091 	1772
> 1950  3909	2841	3924	2173
> 2091	2492	2200	3889	3169
> 2750	3234	2933	3831	2414
> 1416	2300	1932	2786	2830
> 3487	1831	1935	2015	2526

In Desmos, show the following:
* 5-number summary: `A.quartile([0...4])`
* Boxplot: `boxplot(A)` --> Show including and excluding outliers

## Percentiles
* Quartiles divided the data into 4 equally-sized segments
* Percentiles divide the data into 100 equally-sized segments
  * 1st quartile = 25th percentile
  * median = 2nd quartile = 50th percentile
  * 3rd quartile = 75th percentile
  * maximum = 4th quartile = 100th percentile
* If your value is in the 65th percentile, that means it is above the lowest 65% of the data

## Comparing boxplots to histograms
> * Create a normal distribution of data and show histogram and boxplot in Desmos
> * Slowly add data to skew the distribution and see how the boxplot is affected
> * Discuss what is going on

-----
# Homework
## Reading
* 2.1.5 Box plots, quartiles, and the median

## Exercises
* From section 2.1 Exercises
  * Exercises 2.8, 2.10, 2.17
* From Chapter 2 Exercises
  * Exercises 2.33, 2.28, 2.30, 2.34