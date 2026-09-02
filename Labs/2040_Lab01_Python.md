# Lab 1: Intro to Python
A common tool for data analysis is Microsoft Excel. We will be using Excel a lot throughout the semester. In addition to basic calculations, Excel can also graph data. In my experience, graphing in Excel is difficult to deal with.

Another way commonly used to do analysis and make graphs in statistics is using progamming languages. These include,
* SAS (Statistical Analysis System - For very large and professional statistics)
* R (Created specifically for statistics - Great as an introduction)
* Python (Broad application language - Has become equal in most respects to R)
* SQL (Not specifically for statistics, but integral with R and Python)
* Julia
* Matlab
* ...many other languages...

Each language has a different strength, so languages are chosen based on the needs of the project. For this semester, you can choose the language you want. Because of its simplicity, I'll demonstrate in Python this semester.
* Statistics majors may want to consider learning R - I have resources for you
* Can use Python online with a Google account for free
    * [colab.research.google.com](https://colab.research.google.com)
    * If needed, we can switch Google Colab to program in R. If you want this, let me know.
* You can also install Python or R directly on your computer for free. I'd be happy to help if you want to do this.

## Instruction
* Create new Colab
  * Go to drive.google.com and log in to your Google account
  * If you don't have a Google account, you can create one using your @students.snow.edu email address
  * `+ New` --> `More` --> `Google Colaboratory`

Python has a number of functions attached directly into its programming. However, some functions have been created by the python community to simplify and enhance what python can do. These extra functions are assembled into collections of functions we call "packages".

In data analysis, there are two packages we will use frequently. 
* The `pandas` package (__Pan__el __Da__ta) is used to organize and quickly adjust tables to effectively and efficiently provide information
    * The core element in the pandas package is the __DataFrame__. This is just a computer term for a table, though you have a lot more flexibility with a DataFrame than you do with a regular table
* The `stats` package has a series of statistical calculations

Import Pandas and Stats

```python
import pandas as pd              # Handles the Data
import scipy.stats as stats      # Statistics calculations
```

Now, any function we want from these packages will have either `pd` or `stats` in front to indicate which package houses the function we want.

```python
data = pd.read_csv(filename)  # The read_csv function is inside the pandas package
stats.ttest_1samp(data[var], pop_mean)  # The t-test function is in the stats package
```

* *Note 1*: Using a `#` allows you to make comments within your code. The program will ignore comments
* *Note 2*: In addition to cells with code, you can add cells with text. This is helpful if you want to include the code in your reports.

Python can work as a basic calculator. In a `Code` cell, do some basic calculations such as the following. Type `Ctrl+Enter` on Windows or Linux (`Cmd+Enter` on Mac) to run the calculations.
```python
print(5 + 8)
print((42+3) / 5)
```

Often, we want to refer back to certain values, so we save these values in variables (this is a computer variable, not a variable in statistics)
```python
result = (42+3) / 5
print(result)
```

Python can also perform calculations on lists of values. The easiest way to complete this is to use a package of functions called *Numerical Python* (or *NumPy* for short). We need to load this package of functions to use them.
```python
import numpy as np
scores = np.array([97,84,75,89,82,98,90,72,81,87])

print("Add 1: ", scores + 1)

print("Triple: ", scores * 3)

min_score = scores.min()
max_score = scores.max()
avg_score = scores.mean()
print("Minimum: ", min_score, "   Average: ", avg_score, "   Maximum: ", max_score)
```



## Example: Duke Forest
A dataset is essentially a series of value lists. This is how we will consider our variables in Python.
* Load data 
  * Download dataset
  * Upload to Colab
  * Load the data

```python
duke = pd.read_csv('/content/duke_forest.csv')
```

We can see a sample of the data:
```python
duke.head()
```

We can get basic information about the data:
```python
duke.info()
duke.describe()
```

* Quantitative data will have a numerical format, such as `Int` or `Float`
* Categorical data will have a non-numerical format, such as `Object` or `Str`


We can perform basic calculations on the data:
```python
print(f"Minimum: {duke['variable1'].min()}")
print(f"Maximum: {duke['variable1'].max()}")
print(f"Average: {duke['variable1'].mean()}")
```

## Helps
* [scipy.stats list of functions](https://docs.scipy.org/doc/scipy/reference/stats.html)
* [Seaborn Cheatsheet](https://www.datacamp.com/cheat-sheet/python-seaborn-cheat-sheet)

## Assignment
These tools of statistics are used to answer a question. You now get to think of a question, search for data to answer the question, then complete these tasks to answer the question.

Before coming to class, be sure you have:
* A laptop that you can bring to class
* A Google account (If you don't have one, you can create one for free using your @students.snow.edu account)

Common websites to find data:
* Textbook website: [https://www.openintro.org/book/os/](https://www.openintro.org/book/os/) - Select the `Data sets` button
* data.gov

### Instructions
Go to the [textbook's website](https://www.openintro.org/book/os/), select the `Data sets` button, then find a dataset you'd like to analyze. With this data,
* Create a question you would like to answer (Do this in a `Text` cell)
* Load the dataset in Colab
* Do a `.info()` on the dataset. 
* Identify all quantitative and categorical variables. (Do this in a `Text` cell)
* Choose one or two variables that will help answer your question. Indicate that variables you chose and why you chose them. (Do this in a `Text` cell)
* Calculate the Minimum, Maximum, and Average of those variables
* Describe your insights that might lead you toward an answer to your question (Do this in a `Text` cell)
    * You don't have to answer the question completely. We'll need more statistical tools before we can do that.
* Share and submit your project
    * Click on the `Share` button at the top of the page
    * Put in my email address: `michael.olson2@snow.edu` (*Be sure to include the '2' in the address.*)
    * Copy the link and say `Done`
    * In Canvas, submit the link you just copied (the address should begin with `https://colab.research.google.com`)
