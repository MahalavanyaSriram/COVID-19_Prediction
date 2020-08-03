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
Once we have identified the data set, we need to describe its contents and explore insights to better understand the data and its business implications. To describe the data, we created a data dictionary called covid_food_data and then applied various summarizing functions such as info(), describe(), head(), etc.

#### Explore data
EDA will help to give insight of data and understand latest trends. To explore data, we can plot simple graphs on Python, e.g. to understand the trend in data or to get a graphical representation of data for better understanding to get useful insights.In our analysis, we started off by reading the dataset into a pandas dataframe. Then ploted various graphs to gather various insights on the given data

1. Top 15 countries where the Death Rate is high.
![country_vs_deaths](/Images/country_vs_deaths.png)

2. Contries with highest Obesity Rate.
![country_vs_obesity](/Images/country_vs_obesity.png)

3. Countries that are highly undernourished
![death_vs_undernourished](/Images/country_vs_undernourished.png)

4. Death vs Obesity Pecentage for countries with highest Death rates
![death_vs_obesity](/Images/newplot.png)

5. Percentage of food supply in covid affected countries
![percent_food_supply](/Images/percent_food_supply.png)

### Data Preparation 

Steps that were followed in Data cleaning & pre-processing: .

1. Gather data: We extracted the data and converted it to the CSV format. CSV stands for Comma Separated Values. We used pandas for this step

2. Discover and assess data : After collecting the data, it is important to discover each dataset. This step is about getting to know the data and understanding what has to be done before the data becomes useful in a particular context. We discovered few missing values and understood the function of all columns in the dataset. We also figured out few columns like 'Animal fats', 'Aquatic Products, Other','Eggs','Fish, Seafood', 'Meat', 'Milk - Excluding Butter', 'Offals' together sum up to the column Animal Products and Similarly tree or plant generated products sum up to the 'vegetal Products' column. 

3. Cleanse and validate data:
  Cleaning up the data is traditionally the most time consuming part of the data preparation process, but it’s crucial for removing faulty data and filling in gaps.   Important tasks here include:
    - Removing extraneous data and outliers: We removed sub columns that sums up to a generalised columns such as Animal Products and vegetal Products as discussed       earlier in data discovery.
    - Filling in missing values : Once data has been cleansed, it must be validated by testing for errors in the data preparation process up to this
    When we convert the dataset to the CSV format and get the info about the data it will have missing values which is usually represented by NA. There are many         ways to handle missing values. Whenever we come across minute missing values we are going to drop the rows using the .dropna function. Ex. missing values in 'Confirmed', 'Deaths', and 'Recovered' columns were dropped as most of them are geographically dispersed islands and not directly affected by COVID We handled few missing values filling it with the mean of the column like missing values in the 'Obesity' and 'Undernourished' columns by replacing with their mean. We also handled the missing values for 'Active’- we have the confirmed COVID cases, deaths, and recovered, so we replaced the missing values in the 'Active' column appropriately by subtracting the confirmed cases by deaths and recovered.
   - Data reduction: since the sample is relatively big with data of all of the countries around the world, we rounded off the values inorder to reduce the storage capacity

4. Transform and enrich data
Transforming data is the process of updating the format or value entries in order to reach a well-defined outcome, or to make the data more easily understood by a wider audience. In our dataset transformation is done with attribute ‘Undernourished’ where entries '<2.5' were replaced with 2.5; object type of this column was changed to float. Enriching data refers to adding and connecting data with other related information to provide deeper insights. It is observed that cereals (excluding beer) is the highly consumed product in our dataset; so, we included this column as well to gain more insights.  


### Machine Learning   

We can apply a regression model with the predictor variables being different food types and health factors. The outcome variable will be the fatality rate of COVID-19.  We can also look at clustering the dataset to see how different countries are grouped based on food, health, and covid factors. 

Unsupervised Learning (Clustering):
- since all other foods sum up to animal products and vegetal products, we subsetted the data to include only those foods to avoid multi-coolinearity
- data was scaled with RobustScaler()
- completed PCA (using sklearn.decomposition) in order to see how much variability each principle component captured, and found that we could capture close to 90% of the variation from the first two components, so we decided to proceed with 2 components
- KMeans clustering (from sklearn.cluster) performed with 3 clusters 
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
