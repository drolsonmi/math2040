<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

Resources:
* [Desmos: Linear Regression](https://www.desmos.com/calculator/ezcqkdityj)

# Lecture 24: Correlation
* __Note__: 

## Relationship
Correlation and Linear Regression look at the relationship of two quantitative variables.
* One variable is dependent on the other
* We show this dependence using a scatterplot
    * The independent variable is on the x-axis
    * The dependent variable is on the y-axis

> Show Desmos: Linear Regression
>   - show the datapoints and a line
>   - Change the slope to show better fits

In a perfect relationship, a scatterplot would show points along a straight line.
* Indicates the two variables are related to each other and not influenced from other variables
$$y = b_0 + b_1 x$$

Reality, there are always outside influences (confounding variables), creating an error $\epsilon$.
$$y = b_0 + b_1 x + \epsilon$$

* Sometimes, this relationship is a line (linear regression)
* Sometimes, it follows another function (polynomial regression, exponential regression)

We'll focus on linear regression here.

## Predictions and Residuals
Once we have a line (learn how to make it later), we can use it to make predictions:
$$y_i = b_0 + b_1 x_i + e_i \qquad \hat{y}_i = b_0 + b_1 x_i$$

> Example: 
>   * Temperature: [52, 52, 54, 54, 52, 52, 48, 46, 45, 43, 45, 45, 46, 46, 46, 46]
>   * Relative Humidity: [62, 58, 47, 50, 50, 54, 62, 66, 70, 76, 76, 70, 71, 66, 71, 76]
> $$y = 182.07 - 2.446x$$
>
> What is the humidity if the temperature is 50F?
> $$y = 182.07 - 2.446(50) = 59.77$$
> 
> Desmos: Add the predictions

Obviously, it's not perfect. We can calculate the error between a prediction and the true value, also known a __residual__.
$$y_i-\hat{y}_i = (b_0 + b_1x_i + e_i) - (b_0 + b_1x_i) = e_i$$

> Desmos: Add the residuals

We want to get the best line. To get this, we need the correlation.

## Correlation
In a perfect relationship, a scatterplot would show points along a straight line.
* Indicates the two variables are related to each other and not influenced from other variables
$$y = b_0 + b_1 x$$

This perfect relationship has a 100% correlation ($r = 1.0$). The __correlation__ indicates the strength of the relationship. It takes on a value between -1.0 and +1.0.
* Show an image of high correlation, moderate correlation, low correlation

We find the correlation using the variability of the x-variable and of the y-variable
$$R = \frac{1}{n-1}\sum \frac{x_i-\bar{x}}{s_x}\frac{y_i-\bar{y}}{s_y} = \frac{\sum z_xz_y}{n-1}$$

> What is the correlation in the Temperature vs. Relative Humidity example above?

## $R^2$ coefficient
Although *R* is commonly used to describe the relationship, it is more common to use $R^2$
* $R^2$ describes what amount of variation in the dependent variable can be attributed to variations in the independent variable



-----
# Homework
## Reading
* 8.1 Fitting a line, residuals, and correlation
* 8.2.7 Using $R^2$ to describe the strength of a fit

## Exercises
1. Exercise 8.2 from section 8.1 exercises
2. Exercise 8.5 from section 8.1 exercises
3. Exercise 8.7 from section 8.1 exercises
4. Exercise 8.12 from section 8.1 exercises
5. Exercise 8.16 from section 8.1 exercises
6. Exercise 8.37 from chapter 8 exercises
7. What is the correlation between these numbers? Do this calculation by hand and show your work (You may use the calculator to find the means and standard deviations and to do the final calculations). Then use a calculator's linear regression function to check your work.

        |   x   |   y   | 
        | :---: | :---: |
        | 18.01 | 19.04 |
        | 17.53 | 28.79 |
        | 16.53 | 19.29 |
        | 13.57 | 24.73 |
        | 15.22 | 28.10 |
        | 16.03 | 28.67 |
        | 15.86 | 28.77 |
        | 16.78 | 29.67 |
        | 15.88 | 26.90 |
        | 15.68 | 27.81 |
        | 14.66 | 27.05 |
        | 18.02 | 29.73 |
        | 14.32 | 26.58 |
        | 18.05 | 31.30 |
        | 18.82 | 30.76 |

8. Find the $R^2$ value of the data in the previous question. Interpret what this number means.