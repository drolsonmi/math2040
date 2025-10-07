# MATH 2040 - Applied Statistics
# Applied Statistics: Data Analysis Project
This project requires students to select a topic, acquire or use an existing dataset, conduct a thorough statistical analysis using Python, Microsoft Excel, or Desmos, and submit a final comprehensive report.

This project can be completed in groups.

## Project Goal
To apply data loading, graphing, quantitative calculation, and normal distribution techniques learned in the course to a real-world dataset to answer a specific research question.

## Tools Requirement
Students must use Python (e.g., `pandas`, `matplotlib`/`seaborn`, `scipy.stats`) or Microsoft Excel for the data loading, at least one plot, and the normal distribution calculations. Excel and/or Desmos may be used for supplementary analysis, data organization, and visualization.

## Project Phases & Requirements
### Phase 1: Data Acquisition & Exploratory Data Analysis (EDA)
1. __Topic Selection__: Choose a real-world topic and formulate a clear research question that can be answered using data (e.g., "Is there a relationship between a country's GDP and its life expectancy?").
2. __Data Acquisition__: Obtain a suitable dataset. It must contain at least 50 observations and 2 quantitative variables.
    * Data can be gathered by you (and your group). Be aware that this may take additional time. 
      * If you choose to collect your own data, be sure you decide how to make collecting the data as efficient as possible.
      * Be sure to account for any possible lurking variables.
3. __Data Loading & Cleaning__ (Python or Excel):
    * Load the data into a Python environment (e.g., using pandas) or into Excel
    * Inspect and handle any missing values or obvious data errors
4. __Summary Statistics & Visualization__ (Python or Excel):
    * Calculate summary statistics (mean, median, standard deviation, quartiles, range) for all key quantitative variables.
    * Generate appropriate graphical displays (e.g., histograms, box plots, scatter plots) to visualize the variables' distributions and relationships.

### Phase 2: Deep Statistical Analysis
1. __Distribution Analysis__ (Python or Excel):
    * Select one primary quantitative variable.
    * Assess if the data for this variable appears to follow a normal distribution using both graphical evidence (histogram) and quantitative checks (e.g., comparing mean/median, calculating the percentage of data within 1, 2, and 3 standard deviations).
2. __Probability Calculation__ (Python or Excel):
    * Assuming the chosen variable is approximately normally distributed, or using the data's calculated mean (μ) and standard deviation (σ):
        1. Calculate the Z-score for a specific data point.
        2. Use the `scipy.stats` package (specifically `norm.cdf` and/or `norm.ppf`) to find the __probability__ of an observation falling within a specific range ($P(a<X<b)$) and/or the value corresponding to a specific percentile.

### Phase 3: Final Report Submission
Submit a single, coherent document (e.g., a formal report or a well-structured Jupyter Notebook) that serves as the final submission.

The Final Report must include:
1. Introduction:
    * Topic and Data Source.
    * Clear statement of the Research Question(s).
2. Data & Methods:
    * Description of the variables used.
    * Detailed presentation of the Python code used for data loading and cleaning.
3. Results and Discussion:
    * Tables of summary statistics and the generated graphs with brief interpretations.
    * Distribution Analysis: Discussion of the variable's distribution and evidence for/against normality.
    * Probability Calculations: Clear presentation of the normal distribution calculations, including Z-scores, probabilities, and the Python output.
4. Conclusion:
    * A summary answer to the initial research question(s).
    * Discussion of any limitations (e.g., sampling bias, non-normality) and suggestions for future research.

### Grading Focus
* __Accuracy__: Correct calculation of statistics and probabilities.
* __Application__: Appropriate use of the required Python packages and statistical methods.
* __Interpretation__: Clear, insightful, and correct explanation of the numerical results in the context of the chosen topic.
* __Completeness__: All required components (data, code, graphs, analysis) are included and well-documented.