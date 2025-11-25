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
$$R = \frac{1}{n-1}\sum \frac{x_i-\bar{x}}{s_x}\frac{y_i-\bar{y}}{s_y}$$

## A note on Modeling
1. Collect and analyze Data
2. Model the data (find patterns) - we can use these models to make predictions
3. Create laws that describe principles

For example, in physics we have the equation $F=ma$. Where did that come from?
1. Astronomer Tico Bray watched the stars and planets, recording their motion in the skies
2. Astronomer Johannes Kepler created a number of equations that modeled their motion
3. Isaac Newton created the Laws of Motion which we can now use to describe any motion

So far this semester, we have only collected and analyzed data. Once we have an analysis, we can create a couple of equations that we can use when new data is presented.
> The data shows that there is a linear relationship between height and weight among children ages 5-10.
>   * A new child comes to the doctor's office. The child 42 inches tall. What is the expected weight?
>   * We don't know the weight yet, but if we use the line that fits the data, we can estimate the weight

We're going to finish this semester looking at two simple models to make predictions:
* Linear Regression to predict numerical values
* Logistic Regression to predict categories

## Linear Regression (Least Squares Regression)
$$y = b_0 + b_1x$$
$$b_1 = \frac{s_y}{s_x}R$$
$$y-\bar{y} = b_1(x-\bar{x}) \qquad\to\qquad y = \bar{y}-b_1\bar{x} + b_1x$$
$$\to \qquad \text{Let }b_0 = \bar{y}-b_1\bar{x} \qquad \to \qquad y = b_0 + b_1x$$

> In Excel, calculate a correlation on the Duke Forest dataset (Price vs Area)
>    * Scatterplot
>    * Calculate Correlation
>    * Find slope and y-intercept
>    * Predict house price if the area is 4750 sq ft

## Interpolation vs Extrapolation

# Inference for Linear Regression
Our sample has a correlation of $R$. What is the population's correlation ($\rho$)? What are the population's bias ($\beta_0$) and parameter ($\beta_1$)? Are we sure that we have a strong correlation for our population?
$$y = \beta_0 + \beta_1 x$$
* We can create a confidence interval 
    * $\rho = R \pm ME$
    * $\beta_0 = b_0 \pm ME$
    * $\beta_1 = b_1 \pm ME$
* We can also do a hypothesis test to see if these measures are significant

> Do a Linear Regression Test in Excel


-----
# Homework
## Reading
* 8.2 Least Squares Regression
* 8.4 Inference for linear regression

## Exercises
1. Exercise 8.19 from section 8.2 exercises
2. Exercise 8.22 from section 8.2 exercises
3. Exercise 8.23 from section 8.2 exercises
4. Exercise 8.25 from section 8.2 exercises
5. Exercise 8.31 from section 8.4 exercises
6. Exercise 8.32 from section 8.4 exercises
7. Exercise 8.44 from chapter 8 exercises