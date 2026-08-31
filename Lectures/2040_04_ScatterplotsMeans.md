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
<title>Lecture 4: Scatterplots and Means</title>
</head>

# Lecture 4: Scatterplots and Means

## Graphing
What is the point of graphing? Who is our main audience?
* My rule of thumb for graphing: *If you can hand the graph to your audience and they can understand the basics without explanation, then the graph is good enough*

## Requirements for all graphs
* Scale - Build the scale first and fit the data to the scale
* Label

## Scatterplot
Demonstrate a scatterplot
* Graph the following dataset by hand, then on Excel

| Hours Studied | 1     | 2    | 3     | 4     | 5     | 6     | 7     | 8     | 9     | 10    |
| :------------ | :---: | :---:| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Test Score    | 58    | 63   | 66    | 71    | 74    | 79    | 83    | 86    | 92    | 95    |

Relationships
* Linear
  * Introduce the idea of correlation
* Nonlinear

Nonlinear example for wind turbine output:

| Wind Speed (mph)  | 5     | 7     | 9     | 11    | 13    | 15    | 17    | 19    | 21    | 23    |
| :---------------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Power Output (kW) | 3     | 6     | 11    | 18    | 29    | 42    | 58    | 78    | 97    | 123   | 

## Dotplots
* Demonstrate and move on
  * Exam scores = $\{68, 70, 72, 72, 74, 74, 75, 75, 75, 76, 76, 78, 78, 80, 82\}$

## Data Measures
$$A = \{12, 18, 24, 15, 21, 10, 17, 25, 13\}$$

$A_i$ is the value of element $i$

$$A_1 = 12 \qquad A_2 = 18 \qquad A_3 = 24 \qquad ... $$

$n$ is the sample size (in this case, 9)

### Mean
Also known as the average.

$$\bar{x} = \frac{\sum_i A_i}{n}$$
$$\bar{x} = \frac{12+18+24+15+21+10+17+25+13}{9} = \frac{155}{9} = 17.22$$

### Median
Order the data, then select the centralmost value

$$A = \{10, 12, 13, 15, \mathbf{17}, 18, 21, 24, 25\}$$

* The value of 17 is in the middle with equal number of values on both sides
* Median = 17
* What if there are two values in the middle?

$$A = \{10, 12, 13, 15, \mathbf{17, 18}, 20, 21, 24, 25\}$$

* The center is between 17 and 18. When this happens, take the average
* Median = $\frac{17 + 18}{2} = 17.5$

### Mode(s)
* Unimodal, Bimodal, Multimodal

-----
# Homework
(10 points)

## Reading
* 2.1.1 Scatterplots for paired data
* 2.1.2 Dot plots and the mean

## Exercises
1. Exercise 2.2 from section 2.1 exercises
2. Exercise 2.3 from section 2.1 exercises
3. Exercise 2.4 from section 2.1 exercises
4. Exercise 2.6 from section 2.1 exercises