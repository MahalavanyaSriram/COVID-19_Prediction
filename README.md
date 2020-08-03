# **Influences of food consumption and health factors on COVID-19 fatalities**
Team Members: 
- Bailey Brown
- Karan Edikala
- Mahalavanya Sriram
- Meghana Kethidi
- Shravya Donthisaram

## Introduction

Coronavirus is caused by severe acute respiratory syndrome coronavirus 2(SARS-CoV-2).  It was initially identified in December 2019 in Wuhan, China and resulted in an ongoing worldwide pandemic.  As of July 25 2020, there have been 15.7 million cases reported worldwide and resulted in more than 640,000 deaths. COVID-19 has been especially fatal to individuals with pre-existing health conditions. According to a research study that was looking at diets around the world and their COVID-19 fatalities noted that, “The high rate of consumption of diets high in saturated fats, sugars, and refined carbohydrates (collectively called Western diet, WD) worldwide, contribute to the prevalence of obesity and type 2 diabetes, and could place these populations at an increased risk for severe COVID-19 pathology and mortality”. For this project, our group will be conducting analysis on food consumption and health factors worldwide and see how these factors influence the COVID-19 fatalities. 

## Research Question
How do food consumption and health factors around the world influence COVID-19 fatality rates?

## Relevant Domain Information
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7165103/
- https://www.mdpi.com/2072-6643/12/5/1466/htm
- https://blogs.worldbank.org/voices/how-nutrition-can-protect-peoples-health-during-covid-19
- https://www.nature.com/articles/s41430-020-0634-3

## Data Sources
https://www.kaggle.com/mariaren/covid19-healthy-diet-dataset

## Attribute Description	

![Alt text](/Images/DataTable.jpeg?raw=true "Data Table")

All the Units are in percentage except Population

## Approach
  
### Data understanding & EDA

#### Describe data 
Once we have identified the data set, we need to describe its contents and explore insights to better understand the data and its business implications. To describe the data, we can create a data dictionary that lists down the types of variables, the number of records, and the types of analysis. 

#### Explore data
EDA will help to give insight of data and understand latest trends. To explore data, we can plot simple graphs on Python, e.g. to understand the trend in data or to get a graphical representation of data for better understanding to get useful insights.  We will start off by reading the dataset into a pandas dataframe. We can then apply various summarizing functions to the data frame such as .info() and .describe(). Different visualization tools like seaborn are used for EDA. It is also important to see the distribution of variables and for this we can plot histograms and standardize the dataset if needed.
  
### Data Preparation 
Data cleaning & pre-processing:
- checked for nulls in the dataset & handled missing values in the 'Obesity' and 'Undernourished' columns by replacing with their mean; attribute ‘Undernourished’ with entries <2.5 were replaced with 2.5; object type of this column was changed to float 
- missing values in 'Confirmed', 'Deaths', and 'Recovered' columns were dropped as most of them are geographically dispersed islands and not directly affected by COVID
- handled the missing values for 'Active’- we have the confirmed COVID cases, deaths, and recovered, so we replaced the missing values in the 'Active' column appropriately by subtracting the confirmed cases by deaths and recovered 
- it was observed (and confirmed with code) that the animal generated products, like meat, milk , eggs etc., sum up to the 'Animal Products' column; similarly, tree or plant generated products like pulses, cereals etc. including alcohol sum up to the 'Vegetal Products' column; so, for further analysis, only utilizing the 'Country', 'Animal Products', 'Vegetal Products', 'Obesity', 'Undernourished', 'Confirmed', 'Deaths', 'Recovered', 'Active', 'Population' columns  
- moreover, it is observed that cereals (excluding beer) is the highly consumed product; so, including this column as well to gain more insights
- dropped the column 'Unit' (all except Population) as it doesn't specify anything in detail
- data reduction: since the sample is relatively big with data of all of the countries around the world, we rounded off the values inorder to reduce the storage capacity

### Machine Learning   

We can apply a regression model with the predictor variables being different food types and health factors. The outcome variable will be the fatality rate of COVID-19.  We can also look at clustering the dataset to see how different countries are grouped based on food, health, and covid factors. 

Unsupervised Learning (Clustering):
- since all other foods sum up to animal products and vegetal products, we subsetted the data to include only those foods to avoid multi-coolinearity
- data was scaled with RobustScaler()
- completed PCA (using sklearn.decomposition) in order to see how much variability each principle component captured, and found that we could capture close to 90% of the variation from the first two components, so we decided to proceed with 2 components
- KMeans clustering (from sklearn.cluster) performed with 3 clusters 
- 
- In KMeans clustering, we need to decide the clusters before implementing the algorithm. Sometimes, we may not correctly interpret the number of clusters and it becomes challenging to predict the number of clusters. For Hierarchical clustering we do not need to know the number of clusters prior implementing the algorithm —> for these reasons, we choose to complete Hierarchial clustering 

### Evaluation 

For regression, we will use the root mean square error to evaluate the model. And if we plan to use clustering we can also use metrics like within cluster sum of squares for evaluation.

## Technologies/Libraries
- Python 
- Pandas 
- Scikit-learn
- Jupyter
- Numpy
- Seaborn
- Scipy 

## Known Issues

The amount of observations are limited since the data is aggregated by country.

## Conclusion 
