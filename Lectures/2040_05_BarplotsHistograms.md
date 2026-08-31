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
<title>Lecture 5: Barplots and Histograms</title>
</head>

# Lecture 5: Barplots and Histograms

## Bargraph
Graph for Categorical Variables
* Create a table with the categories and counts of # of bedrooms in a house from duke forest dataset
* Create a bargraph

### Common problems with a bargraph
Show common mistakes: [Irizarry, *Introduction to Data Science*, Chapter 11 Data visualization principles](https://rafalab.dfci.harvard.edu/dsbook/data-visualization-principles.html)
* What is wrong with pie charts?
  * "Pie charts are a very bad way of displaying information. The eye is good at judging linear measures and bad at judging relative areas. A bar chart or dot chart is a preferable way of displaying this type of data."

## What is a histogram?
* Categorization of quantitative data
* Displays __Data Density__
  * Density is amount in a given volume, or in this case, quantity in a given range

## Setting up a histogram
* Getting the range
* Getting the number of bins (Power of 2's rule)
* Setting up the bins
  * bin size
  * bin limits
* Categorizing the data

## Drawing a histogram

## Skewness
* Symmetric (Normal) graphs
* Right- and left-skewed
  * Measure of skewness:

  $$\frac{\bar{x}}{median}$$

  * If measure of skewness > 1, then $\bar{x} > median$, so skewed right
  * If measure of skewness < 1, then $\bar{x} < median$, so skewed left

* Uniform
* Bimodal

-----
# Homework
(13 points)

## Reading
* 2.2.1 Contigency tables and bar plots
* 2.1.3 Histograms and shape
* 2.2.5 The only pie chart you will see in this book

## Exercises
1. Exercise 2.21 from section 2.2 exercises
2. Exercise 2.22 from section 2.2 exercises
3. Exercise 2.12 from section 2.1 exercises
4. Exercise 2.15 from section 2.1 exercises
5. Exercise 2.16 from section 2.1 exercises
6. Exercise 2.18 from section 2.1 exercises
7. Exercise 2.31 from chapter 2 exercises
