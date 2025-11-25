<head>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
</head>

# Lecture 27: Logistic Regression
* __Note__: 

Resources for this lecture:

Remember:

## Purpose
* Linear regression uses a value $x$ and our parameters to predict a numerical value
    $$\hat{y} = \beta_0 + \beta_1 x$$
* Logistic regression uses a value $x$ and our parameters to predict a category

## The logistic regression equation
$$transformation(p) = \beta_0 + \beta_1x$$
$$transformation(p) = f(x) \tag\text{where }f(x) = \beta_0 + \beta_1x$$

Logit Transformation
$$logit(p) = \ln\left(\frac{p}{1-p}\right) = f(x)$$
$$p = \frac{e^f(x)}{1 + e^{f(x)}}$$

> Plot this function on Desmos
>   * What happens if $\beta_0$ changes?
>   * What happens if $\beta_1$ changes?
>   * What happens if $\beta_1$ becomes negative?

### Demo
> [CoLab demo on LogisticRegression](https://colab.research.google.com/drive/1_cYfd2OiJxZFeJLGTuen9iLdFxbEgDlm?usp=sharing)

## What if there's more than one variable?
With linear regression, we just added more terms to our regression equation. We do the same here.
$$p = \frac{e^f(x)}{1 + e^{f(x)}} \qquad f(x) = \beta_0 + \beta_1x_1 + \beta_2x_2 + \beta_3x_3 + \dots$$

-----
# Homework
## Reading
* 

## Exercises
1. Exercise () from section () exercises
2. Exercise () from chapter () exercises