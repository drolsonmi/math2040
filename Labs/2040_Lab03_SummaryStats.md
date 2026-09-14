# Lab 3: Summary Statistics
In Lab 1, we saw how perform basic functions in Python, including loading data. In Lab 2, we explored graphing within Python. Now we will look at the complete summary statistics within Python in Lab 3. We will also learn how to find the summary statistics in Microsoft Excel.

(From here on out, most of our labs will be in Excel. However, I may ask you to go back to Python and create a better graph for me.)

## Summary Statistics in Python

### Load packages and data
Just like in Lab 1 and Lab 2, we start by loading our packages and our dataset.

```python
import pandas as pd
import scipy.stats as stats

duke = pd.read_csv('/content/duke_forest.csv')
```

### Quick overview
The fastest way to see summary statistics for every quantitative variable at once is `.describe()`.

```python
duke.describe()
```

This one line gives you the count, mean, standard deviation, minimum, maximum, and the 25th/50th/75th percentiles (quartiles) for every quantitative column.

### Individual statistics
Sometimes we only want one number at a time. Pandas has a function for each of the common summary statistics.

```python
print(f"Mean:      {duke['price'].mean()}")
print(f"Median:    {duke['price'].median()}")
print(f"Std Dev:   {duke['price'].std()}")
print(f"Variance:  {duke['price'].var()}")
print(f"Minimum:   {duke['price'].min()}")
print(f"Maximum:   {duke['price'].max()}")
```

We can also pull out any percentile we want with `.quantile()`. Remember, the median is just the 50th percentile.

```python
print(f"25th percentile: {duke['price'].quantile(0.25)}")
print(f"75th percentile: {duke['price'].quantile(0.75)}")
```

* *Note*: Mode is less common for quantitative data, but if you need it, `duke['bed'].mode()` or `stats.mode(duke['bed'])` will find it.



## Summary Statistics in Excel

### Load the data
* Open Excel
* `File` -> `Open` -> select `duke_forest.csv`
  * Excel will place each variable into its own column automatically

### Individual formulas
Excel has a built-in formula for each summary statistic. Click an empty cell and type the formula, referencing the range of the column you want to summarize (e.g., `C2:C99`).

| Statistic          | Excel Formula            |
| :----------------- | :----------------------- |
| Mean               | `=AVERAGE(range)`        |
| Median             | `=MEDIAN(range)`         |
| Mode               | `=MODE.SNGL(range)`      |
| Standard Deviation | `=STDEV.S(range)`        |
| Variance           | `=VAR.S(range)`          |
| Minimum            | `=MIN(range)`            |
| Maximum            | `=MAX(range)`            |
| 25th Percentile    | `=QUARTILE.INC(range,1)` |
| 75th Percentile    | `=QUARTILE.INC(range,3)` |
| Count              | `=COUNT(range)`          |

### Descriptive Statistics all at once (Data Analysis ToolPak)
Typing one formula at a time works, but Excel has a tool that calculates everything in one step.

* Check whether `Data Analysis` appears on the `Data` tab. If it doesn't, turn it on once:
  * `File` -> `Options` -> `Add-ins` -> next to `Manage`, choose `Excel Add-ins` -> `Go` -> check `Analysis ToolPak` -> `OK`
* `Data` tab -> `Data Analysis` -> `Descriptive Statistics` -> `OK`
* Fill in the dialog box:
  * `Input Range`: select the column you want to summarize, including the header
  * Check `Labels in First Row`
  * Choose an `Output Range` (an empty cell) or `New Worksheet`
  * Check `Summary statistics`
  * `OK`

This produces the mean, standard error, median, mode, standard deviation, sample variance, kurtosis, skewness, range, minimum, maximum, sum, and count all in one table.


## Helps
* [Pandas `.describe()` documentation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html)
* [Microsoft: Use the Analysis ToolPak](https://support.microsoft.com/en-us/office/use-the-analysis-toolpak-to-perform-complex-data-analysis-6c67ccf0-f4a9-487c-8dec-bdb5a2cefab6)
* [scipy.stats list of functions](https://docs.scipy.org/doc/scipy/reference/stats.html)


## Assignment
Continue with the dataset and variables you chose in Lab 1. If you would like to change to a different dataset, that is fine. For your one or two variables of interest:
* Calculate the mean, median, standard deviation, minimum, and maximum in Python
* Repeat the same summary statistics in Excel, using either the formulas or the Data Analysis ToolPak
* Compare your Python and Excel results - do they match?
* In a `Text` cell, briefly describe what these summary statistics tell you about your data, and how they connect to the question you asked in Lab 1
    * You don't have to fully answer the question yet. We'll add more statistical tools as the semester goes on.

When completed, submit your project:
* In Colab: click `Share` -> enter my email address `molson@umatyc.org` -> copy the link -> say `Done`
* In Canvas, submit the Colab link **and** upload your Excel workbook