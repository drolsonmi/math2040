# Lab 1: Intro to Python

## Different programming languages for statistics
* SAS (Statistical Analysis System - For very large and professional statistics)
* R (Created specifically for statistics - Great as an introduction)
* Python (Broad application language - Has become equal in most respects to R)
* SQL (Not specifically for statistics, but integral with R and Python)
* Julia
* Matlab
* ...many other languages...

You can choose the language you want, but I'll demonstrate in Python this semester
* Can use Python online with a Google account for free
    * You can install Python, or R directly on your computer for free. I'd be happy to help if you want to do this.
* Statistics majors may want to consider learning R - I have resources for you

## Example: Duke Forest
* Create new Colab
  * Go to drive.google.com and log in to your Google account
  * If you don't have a Google account, you can create one using your @students.snow.edu email address
  * `+ New` --> `More` --> `Google Colaboratory`
* Import pandas and seaborn
```python
import pandas as pd              # Handles the Data
import matplotlib.pyplot as plt  # Graphing programs
import seaborn as sns            # Graphs the Data
import scipy.stats as stats      # Statistics calculations
```
* *Note 1*: Using a `#` allows you to make comments within your code. The program will ignore comments
* *Note 2*: In addition to cells with code, you can add cells with text. This is helpful if you want to include the code in your reports.

* Load data 
  * Download dataset
  * Upload to Colab
  * Load the data
```python
duke = pd.read_csv('content/duke_forest.csv')
```
* We can see a sample of the data:
```python
duke.head()
```

* Graph boxplots of Price and Square Footage
```python
sns.boxplot(data=duke, x='price')
```
* We can change the size of the graph and add labels
```python
plt.figure(figsize=(10,3))
sns.boxplot(data=duke, x='price')
plt.title('Distribution of House Prices in the Duke Forest Area')
plt.xlabel('Prices (US$)')
plt.show()
```
* The `plt.show()` command just finalizes and displays the graph. Not exactly necessary in Colab, but it's a good habit to be in.
* Once the graph is plotted, we can right-click to copy and paste directly into a Word document

* Now graph Square Footage (See if class can do this)
```python
plt.figure(figsize=(10,3))
sns.boxplot(data=duke, x='area')
plt.title('Square Footage of Houses in the Duke Forest Area')
plt.xlabel('Area (sq-ft)')
plt.show()
```

* Get 5-number summary of data
```python
print("              Mean = ", duke['price'].mean())
print("Standard Deviation = ", duke['price'].std())
print("Minimum = ", duke['price'].min())
print("     Q1 = ", stats.quantile(duke['price'], 0.25))
print(" Median = ", duke['price'].median())
print("     Q3 = ", stats.quantile(duke['price'], 0.75))
print("Maximum = ", duke['price'].max())

# Or we can do all at once
print("5-number summary = ", stats.quantile(duke['price'], [0,0.25,0.50,0.75,1]))
```

* Graph scatterplots of price vs area
```python
sns.scatterplot(data=duke, x='area', y='price')
plt.title('Relationship between Area and Price')
plt.xlabel('Area (sq-ft)')
plt.ylabel('Price (US$)')
plt.show()
```

* Graph timeseries of price vs year built
```python
duke['bed'] = duke['bed'].astype('category')   # For sake of coloring
sns.scatterplot(data=duke, x='year_built', y='price', hue='bed')
plt.title('House Price over Time')
plt.xlabel('Year Built')
plt.ylabel('Price (US$)')
plt.show()
```


## Helps
* [scipy.stats list of functions](https://docs.scipy.org/doc/scipy/reference/stats.html)
* [Seaborn Cheatsheet](https://www.datacamp.com/cheat-sheet/python-seaborn-cheat-sheet)

# Assignment
In class, we will see how to use Python to do calculations and to create graphs. Before coming to class, be sure you have:
* A laptop that you can bring to class
* A Google account (If you don't have one, you can create one for free using your @students.snow.edu account)

Here are a couple of helps if you need more after our lecture:
* The instructions for this lab are on my Github page: https://github.com/drolsonmi/math2040/blob/main/Labs/2040_Lab01_IntroToPython.md
* scipy.stats list of functions: https://docs.scipy.org/doc/scipy/reference/stats.html
* Seaborn Cheatsheet: https://www.datacamp.com/cheat-sheet/python-seaborn-cheat-sheet

## Instructions
Go to the [textbook's website](https://www.openintro.org/book/os/), select a website, then find a dataset you'd like to analyze. In your analysis:
* Identify quantitative variables
* Find 5-number summaries of at least two quantitative variables
* Create boxplots for at least two quantitative variables, correctly labeled
* Compare two variables
  * Identify the explanatory and response variables
  * Create a scatterplot of the two variables, correctly labeled

You are allowed to complete this assignment with other classmates. Group work is not required, but encouraged.

Once completed, submit your work by doing the following:
* Rename your lab by clicking on the current name (probably something like "Untitled0.ipynb") to something related to this lab (such as "Math2040-Lab1.ipynb")
* Create a Text box at the top and list the names of all students that worked on this project
* Select the `Share` button
* In the box at the top, add my email address: `michael.olson2@snow.edu`
  * You may want to also add the email addresses of those in your group so that they have a copy as well
* If it asks you for a message, please include the names of all your group members who contributed to the lab (this is in addition to the text box you created earlier)
* Push `Send`