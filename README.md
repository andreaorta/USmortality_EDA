# Project: US mortality 1962-2016

I'm practicing exploratory data analysis (EDA) on a database reporting the number of deaths across 122 cities in the US, over the course of several decades (1962-2016).

The analysis is based on a .csv database, downloadable from [data.gov](https://catalog.data.gov/dataset/deaths-in-122-u-s-cities-1962-2016-122-cities-mortality-reporting-system).

The notebook makes extensive use of the *pandas* and *matplotlib* libraries.

## Summary of the notebook

#### Exploring the DataFrame

* Renaming the columns
* Adjusting the data types of the columns
* Understanding the *Region* column

#### Improvements to the DataFrame

* Imputation of missing values in the *state* and *city* columns
* Better labelling of the data about Kansas City
* Checking consistency of the data stored in the DataFrame

#### Handling the missing values in the mortality data

* Qualitative analysis of the distribution of NaN's, both by year and by city
* Discarding unsalvageable rows, investigation of how many rows there are containing a given number of NaN's
* Imputation of missing values

#### Plotting functions

* Total deaths per week in the US in a given year by age group (line plot + bar plot + comparison line plots)
* Total deaths per year in a given city by age group (line plot + bar plot + comparison line plots)
* Total deaths per year in a given state by age group (line plot + bar plot + comparison line plots)
* Incidence of pneumonia/influenza deaths over total number of deaths per year by state/city (comparison line plots) 
Analysis of outliers with respect to the national distribution with boxplots by year

## Tricks and takeaways

* Index Alignment 

In imputing some missing values in the `state` and `city` columns for `Region 3`, I replaced a number of pairs of rows of the DataFrame with rows containing the average of each pair. 
I constructed a replacement DataFrame with the desired data, dropped some of the rows from the part of the original DataFrame that I wanted to edit and substituted the values in the others with those stored in the replacement DataFrame.
For the replacement to work I needed to make sure that the row indices in the two DataFrames were matching.

* `subset`, `thresh` parameter in pd.DataFrame.dropna

When analysing the rows with missing values, I learned about the possibility of dropping rows containing `NaN`'s only if they contain fewer than `thresh` non-missing values across the columns in `subset`.
By taking differences of the number of rows left in the DataFrame after dropping with `thresh` and `thresh`, one can quickly count how many rows contain exactly `k` non-missing values (and hence the complementary number of `NaN`'s).

* Avoiding duplicate entries in the legend in comparison plots

Plotting the same graph for e.g. three years/cities and using the standard `fig.legend(loc=...)` would result in three copies of the same legend for the individual plot.
The problem was solved thanks to the `plt.gca().get_legend_handles_labels()` command, followed by the creation of a dictionary of all the collected handles and labels, which would remove the duplicates. See [Stackoverflow](https://stackoverflow.com/questions/13588920/stop-matplotlib-repeating-labels-in-legend).

* Avoiding superfluous entries in the legend of PI_cities plots

When drawing the *PI_cities* plots, I didn't want the state average curve to be drawn on top of the city curve, when that city was the only representative of its state. Nor did I want any mention of the state average curve in the legend, obviously.
The `ax.get_legend_handles_labels()` command was sufficient to collect exactly the handles and labels I needed.

* Customising the title of some plots
Essentially tinkering with string formatting. In particular, for the *PI_cities* plots, one of four different title formats is selected, depending on the input given to the function.