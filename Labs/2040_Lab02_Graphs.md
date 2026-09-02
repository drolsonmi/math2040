# Lab 2: Graphing in Python
In Lab 1, we saw how perform basic functions in Python, including loading data. Lab 2 will explore how to create graphs.

As we go through this assignment (and the rest of the semester), remember that every needs a proper scale and proper labels.

## Instruction
### Load packages
Python uses a package of functions called `matplotlib` to create graphs. Members of the python community have developed a second package called `seaborn` to build on top of matplotlib. We will primarily use seaborn, but we will need some functions from matplotlib.

To open these packages,

```python
import matplotlib.pyplot as plt
import seaborn as sns
```

Now, any function we want from these packages will have either `plt` or `sns` in front to indicate which package houses the function we want.

We will also need pandas.

```python
import pandas as pd
```

Load the Duke Forest dataset

```python
duke = pd.read_csv('/content/duke_forest.csv')
```

### Scatterplots
Here is a basic scatterplot using seaborn:

```python
sns.scatter(data=duke, x='area', y='price')
```

The scales are determined automatically. We can adjust them if needed. However, we need labels. 

```python
sns.scatterplot(data=duke, x='area', y='price')

# Add labels
plt.title('Relationship between Area and Price')
plt.xlabel('Area (sq-ft)')
plt.ylabel('Price (US$)')

# Adjust scale
plt.xlim([1000,4000])
plt.ylim([0,1e6])

# Show the graph
plt.show()
```

We can also add another variable by coloring the points in the graph. Here is a way to color the graph by a categorical variable. Note how the colors indicate discrete categories.

```python
sns.scatterplot(data=duke,
                x='area',
                y='price',
                hue='bed',
                palette='colorblind')
plt.title('Relationship between Area, Price, and # of bedrooms')
plt.xlabel('Area (sq-ft)')
plt.ylabel('Price (US$)')
```

If we color the graph by a quantitative variable, however, the colors indicate a scale.

```python
sns.scatterplot(data=duke,
                x='area',
                y='price',
                hue='year_built')
plt.title('Relationship between Area, Price, and Age')
plt.xlabel('Area (sq-ft)')
plt.ylabel('Price (US$)')
```

That's it! You now have the basics of graphing. Now, let's see how to make other graphs.

### Bargraph
```python
sns.countplot(data=duke, x='bed')  # y-axis is count of categories
sns.countplot(data=duke, x='bed', hue='bath')
```

### Timeplot
```python
sns.lineplot(data=duke, x='year_built', y='price')
sns.lineplot(data=duke, x='year_built', y='price', errorbar=None)
```

### Histogram
```python
sns.histplot(data=duke, x='price')
sns.histplot(data=duke, x='price', binwidth=250000) # Determine bin size
sns.histplot(data=duke, x='price', bins=10)         # Determine number of bins
sns.histplot(data=duke, x='price', hue='cooling', palette='colorblind')
```

## Helps
* [Seaborn Cheatsheet](https://www.datacamp.com/cheat-sheet/python-seaborn-cheat-sheet)

## Assignment
In Lab 1, you did some basic calculations with a dataset of your choosing. You are welcome to use that dataset or to choose another. Your assignment will be to create 4 high-quality plots.
- scatterplot
- bargraph
- histogram
- timeplot

After each plot, identify one thing of note that we can learn from the graph you just made.

When completed, submit your project
* Click on the `Share` button at the top of the page
* Put in my email address: `michael.olson2@snow.edu` (*Be sure to include the '2' in the address.*)
* Copy the link and say `Done`
* In Canvas, submit the link you just copied (the address should begin with `https://colab.research.google.com`)