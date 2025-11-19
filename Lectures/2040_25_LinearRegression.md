<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 25: Linear Regression
* __Note__: 

Resources for this lecture:

Remember:

## Relationship between two variables
Correlation and Linear Regression look at the relationship of two quantitative variables.
* One variable is dependent on the other
* We show this dependence using a scatterplot
    * The independent variable is on the x-axis
    * The dependent variable is on the y-axis

Correlation:
$$r = \frac{1}{n-1}\sum \frac{x_i-\bar{x}}{s_x}\frac{y_i-\bar{y}}{s_y}$$

## Linear Regression (Least Squares Regression)
$$y = \beta_0 + \beta_1x$$
$$\beta_1 = \frac{s_y}{s_x}r$$
$$y-\bar{y} = \beta_1(x-\bar{x}) \qquad\to\qquad y = \bar{y}-\beta_1\bar{x} + \beta_1x$$
$$\to \qquad \text{Let }\beta_0 = \bar{y}-\beta_1\bar{x} \qquad \to \qquad y = \beta_0 + \beta_1x$$

## Interpolation vs Extrapolation

# Inference for Linear Regression

-----
# Homework
## Reading
* 8.2 Least Squares Regression
* 8.4 Inference for linear regression

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises