# Lab 1: Intro to Python

## Different programming languages for statistics
* SAS (For very large and professional statistics)
* R (Created specifically for statistics - Great as an introduction)
* Python (Broad application language - Has become equal in most respects to R)
* SQL (Not specifically for statistics, but integral with R and Python)
* Julia
* Matlab
* ...

You can choose the language you want, but I'll demonstrate Python
* Can use Python online with a Google account for free
    * You can install python and other 
* Statistics majors may want to consider learning R - I have resources for you

## Example: Duke Forest
* Create new Colab
  * `+ New` --> `More` --> `Google Colaboratory`
* Import pandas and seaborn
```python
import pandas as pd              # Handles the Data
import matplotlib.pyplot as plt  # Graphing programs
import seaborn as sns            # Graphs the Data
import scipy.stats as stats      # Statistics calculations
```
* *Note 1*: Using a `#` allows you to make comments within your code. The program will ignore comments
* *Note 2*: In addition to cells with code, you can add cells with text. This is helpful when it comes to reports.

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



## Helps
* Seaborn Cheatsheet
* SciPy Cheatsheet

# Assignment
Go to the textbook's website, select a website, then find a dataset you'd like to analyze. In your analysis:
* Identify quantitative variables
* Find 5-number summaries of at least two quantitative variables
* 