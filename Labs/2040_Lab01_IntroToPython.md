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
* Import pandas and seaborn
```python
import pandas as pd
import seaborn as sns
```

* Load data (Provide the link)
```python
duke = pd.read_csv('https://github.com/drolsonmi/math2040/Datasets/duke_forest.csv')
```

* Graph boxplots of Price and Square Footage
```python
sns.boxplot
```

* Get 5-number summary of data
```python
```

* Graph scatterplots of 