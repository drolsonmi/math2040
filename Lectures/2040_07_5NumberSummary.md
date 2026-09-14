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
<title>Lecture 7: 5-Number Summary and Boxplots</title>
</head>

# Lecture 7: 5-Number Summary and Boxplots
Resources:
* Microsoft Excel
* Desmos

## Measuring the middle of the data
* Mean
* Mode
* Median

> __Demo__: Histogram in Desmos
> * Draw a Histogram in Desmos for this dataset:
> 
> $$\{1,2,2,3,3,3,4,4,4,4,5,5,5,6,6,7\}$$
>
> Graph the mean, median, mode
> * mean: `x = A.mean()`
> * median: `x = A.median()`
> * mode: `x = 4`

When data is symmetric, these will be the same. If they are not symmetric, then
* the mean is heavily influenced by outliers
* the median is somewhat influenced by outliers
* the mode is not influenced by outliers and remains unchanged

> Add the values $\{6, 7, 8, 8, 9\}$ to the dataset. See how the mean and median move

## Quartiles
The measurement of quartiles can be inclusive or exclusive, meaning it includes or excludes the endpoints
* TI-84 is inclusive
* Excel has a function for each
  * If the median is a value in the dataset, then excel will weight half the median (find the quartile with the median and the quartile without the median, then average the two)

### 5-number summary
The 5-number summary consists of,

$$\{minimum, Q_1, median, Q_3, maximum\}$$

What do these numbers mean?
* $Q_1$ is value above the lowest quarter of the data
* Median is value above the lowest half (or 2 quarters) of the data (Can also be called $Q_2$)
* $Q_3$ is value above the lowest 3 quarters of the data
* Maximum is value above the all 4 quarters of the data

### Boxplot
A boxplot is a graph that indicates the 5-number summary. It consists of a box to indicate the range of the 2nd and 3rd quarters (the 2 quarters in the middle, or the centermost 50% of the data) and whiskers to indicate the range of the 1st and 4th quarters.

* Create the scale (Numberline from 0 to 20)
* Create the label ("Random numbers from class")
* Draw the 5 numbers
* Create box between $Q_1$ and $Q_3$
* Create whiskers between min and $Q_1$ and between $Q_3$ and max
> * Identify lowest 25%, highest 25%, and the IQR

### Comparing boxplots to histograms
> * Create a normal distribution of data and show histogram and boxplot in Desmos
> * Slowly add data to skew the distribution and see how the boxplot is affected
> * Discuss what is going on

### Outliers
* Any value larger than $Q_3 + 1.5*IQR$
* Any value smaller than $Q_1 - 1.5*IQR$

## Percentiles
* Quartiles divided the data into 4 equally-sized segments
* Percentiles divide the data into 100 equally-sized segments
  * 1st quartile = 25th percentile
  * median = 2nd quartile = 50th percentile
  * 3rd quartile = 75th percentile
  * maximum = 4th quartile = 100th percentile
* If your value is in the 65th percentile, that means it is above the lowest 65% of the data

Find the 10th, 20th, 30th, … 80th, 90th percentiles of the following dataset:

$$\{50, 54, 57, 59, 61, 64, 66, 68, 69, 70, 71, 72, 72, 73, 73, 74, 74, 75, 75, 76, 76, 76, 77, 77, 77, 78, 78, 79, 79, 80\}$$

Questions:
* Look at the percentiles. Describe the distribution to me. (Should be left skewed)

In Desmos, show the following:
* Histogram: `histogram(A)`
* 5-number summary: `A.quartile([0...4])`
* Boxplot: `boxplot(A)` --> Show including and excluding outliers

## Class Practice
Use the following prompt in AI:

	I need to practice making a boxplot and finding percentiles. Give me 25 random values between 20 and 40 with a right skew. Order them from least to greatest.

Then,
	• Find the 5-number summary
	• Create a boxplot
	• Find the 20th, 40th, 60th, and 80th percentiles

When completed, ask AI to provide the 5-number summary, boxplot, and the 20th, 40th, 60th, and 80th percentiles. Grade yourself
* Be sure to note if you added a numberline and a label to your boxplot!!

What would be the 10th percentile?


-----
# Homework
(13 points) 

## Reading
* 2.1.5 Box plots, quartiles, and the median

## Exercises
1. Exercise 2.8 from section 2.1 exercises
2. Exercise 2.10 from section 2.1 exercises
3. Exercise 2.17 from section 2.1 exercises
4. Exercise 2.33 from chapter 2 exercises
5. Exercise 2.28 from chapter 2 exercises
6. Exercise 2.30 from chapter 2 exercises
7. Exercise 2.34 from chapter 2 exercises