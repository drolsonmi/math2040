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
<title>Lecture 11: Distributions</title>
</head>

# Lecture 11: Distributions
* __Note__: Today is the last day to take Exam 1

Resources for this lecture:
* [Desmos: Z-score and Empirical Rule](https://www.desmos.com/calculator/ca83f56b2f)

## Discrete vs. Continuous probabilities
* Reminder: Difference between discrete and continuous variables
* With discrete variables, we can pinpoint the probability of a specific value
  * What is the probability of randomly selecting a red book
* With continuous variables, we cannot pinpoint the probability of a specific value
  * What is the probability of randomly selecting a book with 512 pages?
  * What is the probability of randomly selecting a book with 752,500 words?
* Instead of looking at the probability of a particular value, we are looking at the probability of it being in a range
  * $$P(500\le pages \le 525) = \frac{\text{number of books between 500 and 525 pages long}}{\text{total number of books}}$$
  * $$P(\text{lower limit}\le X \le \text{upper limit}) = \frac{\text{number of subjects between upper and lower limits}}{\text{total sample size}}$$

## Probability Density Function
* [Histogram on python](https://github.com/drolsonmi/math2040/blob/main/Lectures/code/2040_11_Distributions.ipynb)
  * Temperature data
  * RH data
* Decrease bin width to see how it becomes continuous
  * number of bins = [30,60,80,120]
* Probability density function (draw the pdf line (or kde line) to show pattern)

## Probability
Consider the pdf for the sum of rolling two dice:
- Create bargraph of sums: count(2)=1, count(3)=2, count(4)=3, count(5)=4, etc.

If we want to know the probability of rolling a value between 3 and 5, what would we do?
- $P(3~or~4~or~5) = P(3) + P(4) + P(5) = \tfrac{2+3+4}{36} = \tfrac{9}{36}$

Now, let's calculate the area from the graph
- Each bar has a width of 1
- Find the area of each bar: ($1*\frac{2}{36}=\frac{2}{36},  1*\frac{3}{36}=\frac{3}{36},  1*\frac{4}{36}=\frac{4}{36}$)
- Find the total area:  ($\tfrac{2}{36} + \frac{3}{36} + \frac{4}{36} = \frac{9}{36}$)

The area of the graph indicates total probability. 

With continuous variables, we can't just measure the height of the bars. Since it is continuous, the width of a single value is infinitessimally small that the area would be 0. The curve gives us some information, but is not the probability. For that, we need the area.

Thus,
- the height of the bars/curve indicate what we call the __likelihood__ (or the __probability density function__ (pdf))
- the area of the bars/curve indicate the __probability__ (or the __cumulative density function__ (cdf))

## Normal Distributions
* Normal Distributions
  - Density function is based on the mean and standard deviation
  - Increasing/decreasing the mean will shift the distribution
  - Increase/decreasing the standard deviation will spread/compress the distribution

### Standardizing (Z-Score)
Let's say you have taken an IQ test to measure your level of intelligence.
- National average = 100,  Standard Deviation = 15
- You score a 107

You have a friend from another country who uses a different test to measure their level of intelligence.
- National average = 25,  Standard Deviation = 5
- Friend scores a 27.5

Who did better? Since they are on different scales, it is hard to measure.

We can __standardize__ the data by measuring not how many points you scored above the mean, but how many standard deviations you were above the mean.
- Find the distance from your value to the mean ($x-\mu$)
- Find how many standard deviation this is (divide by $\sigma$)

The result is what we call a __z-score__:

$$z = \frac{x-\mu}{\sigma}$$

Let's apply this to the problem:

$$z_y = \frac{107-100}{15} = \frac{7}{15} = 0.4667 \qquad z_f = \frac{27.5-25}{5} = \frac{2.5}{5} = 0.50$$

Your friend scored half a standard deviation above the mean. You were less than half a standard deviation above the mean. So, relatively speaking, your friend performed better than you did.

Bottom line: The __z-score__ tells us how many standard deviations our value is from the mean

> [Desmos: Z-score and Empirical Rule](https://www.desmos.com/calculator/ca83f56b2f)

### Empirical Rule
Now, we combine the principles of the z-score with the probability (area) under the pdf

-----
# Homework
(10 points)

## Reading
* 3.5 Continuous Distributions
* 4.1.1 Normal distribution model
* 4.1.2 Standardizing with Z-scores

## Exercises
1. Exercise 3.37 from section 3.5 exercises
2. Exercise 3.38 from section 3.5 exercises
3. Exercise 4.2 from section 4.1 exercises
4. Exercise 4.3(a-d) from section 4.1 exercises