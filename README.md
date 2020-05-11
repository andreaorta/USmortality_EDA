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

... to be listed.