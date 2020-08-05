# **Influences of food consumption and health factors on COVID-19 fatalities**
Team Members: 
- Bailey Brown
- Karan Edikala
- Mahalavanya Sriram
- Meghana Kethidi
- Shravya Donthisaram

## Introduction

Coronavirus is caused by severe acute respiratory syndrome coronavirus 2(SARS-CoV-2).  It was initially identified in December 2019 in Wuhan, China and resulted in an ongoing worldwide pandemic.  As of July 25 2020, there have been 15.7 million cases reported worldwide and resulted in more than 640,000 deaths. COVID-19 has been especially fatal to individuals with pre-existing health conditions. According to a research study that was looking at diets around the world and their COVID-19 fatalities noted that, “The high rate of consumption of diets high in saturated fats, sugars, and refined carbohydrates (collectively called Western diet, WD) worldwide, contribute to the prevalence of obesity and type 2 diabetes, and could place these populations at an increased risk for severe COVID-19 pathology and mortality”. For this project, our group will be conducting analysis on worldwide food consumption, health factors and see how these factors influence the COVID-19 fatalities. 

## Research Question
How do food consumption and health factors around the world influence COVID-19 fatality rates?

## Relevant Domain Information
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7165103/
- https://www.mdpi.com/2072-6643/12/5/1466/htm
- https://blogs.worldbank.org/voices/how-nutrition-can-protect-peoples-health-during-covid-19
- https://www.nature.com/articles/s41430-020-0634-3

## Data Sources
https://www.kaggle.com/mariaren/covid19-healthy-diet-dataset.           
Dataset Name: datasets_618335_1356210_Food_Supply_Quantity_kg_Data.csv

## Attribute Description	

![Alt text](images/DataTable.jpeg?raw=true "Data Table")

All the Units are in percentage except Population

## Technologies
- Anaconda 4.5.12 Distribution
- Python 3.7
- Jupyter Notebook

## Libraries
- Pandas 
- Scikit-learn
- Jupyter
- Numpy
- Seaborn
- Scipy 
- Altair
- Plotly

## Approach
  
### Data understanding & Exploratory Data Analysis(EDA)

#### Describe data 
Once we have identified the data set, we need to describe its contents and explore insights to better understand the data and its business implications. To describe the data, we created a data dictionary called covid_food_data and then applied various summarizing functions such as info(), describe(), head(), etc.

#### Explore data
EDA will help to give insight of data and understand latest trends. To explore data, we can plot simple graphs on Python, e.g. to understand the trend in data or to get a graphical representation of data for better understanding to get useful insights.In our analysis, we started off by reading the dataset into a pandas dataframe and then plotted various graphs to gather various insights and trends on the data.

1. Top 15 Countries where the Death Rate is high.

![country_vs_deaths](/images/country_vs_deaths.png)

2. Countries with highest Obesity Rate.

![country_vs_obesity](/images/country_vs_obesity.png)

3. Countries that are highly undernourished.

![death_vs_undernourished](/images/country_vs_undernourished.png)

4. Death vs Obesity Pecentage for Countries with highest Death rates.

![death_vs_obesity](/images/newplot.png)

5. Percentage of food supply in COVID affected Countries.

![percent_food_supply](/images/percent_food_supply.png)

### Data Preparation 

Steps that were followed in Data Cleaning & Data Pre-processing: .

1. Gather data and Read-in: We extracted the data and converted it to the CSV format. CSV stands for Comma Separated Values. We used pandas for the read-in step.

2. Discover and assess data : After collecting the data, it is important to discover each dataset. This step is about getting to know the data and understanding what has to be done before the data becomes useful in a particular context. We discovered few missing values and understood the function of all columns in the dataset. We also figured out that few columns like 'Animal fats', 'Aquatic Products, Other', 'Eggs','Fish', 'Seafood', 'Meat', 'Milk - Excluding Butter', 'Offals' together add up to the column 'Animal Products'. Similarly, tree or plant generated products add up to the 'Vegetal Products' column. 

3. Cleanse and validate data:
  Cleaning up the data is traditionally the most time consuming part of the data preparation process, but it’s crucial for removing faulty data and filling in gaps.   Important tasks here include:
    - Removing extraneous data and outliers: We removed sub columns that add up to a generalized columns such as Animal Products and vegetal Products as discussed       earlier in data discovery.
    - Filling in missing values : Once data has been cleansed, it must be validated by testing for errors in the data preparation process.
    When we convert the dataset to the CSV format and get the information about the data it will have missing values which is usually represented by NA. There are many         ways to handle missing values. Whenever we came across minute missing values we are going to drop the rows using the .dropna function. Ex. missing values in 'Confirmed', 'Deaths', and 'Recovered' columns were dropped as most of them are geographically dispersed islands and not directly affected by COVID We handled few missing values filling it with the mean of the column like missing values in the 'Obesity' and 'Undernourished' columns by replacing with their mean. We also handled the missing values for 'Active’ column using columns 'Confirmed' and 'Recovered'- the data for confirmed COVID cases, deaths, and recovered are available (not missing) in the data, so we replaced the missing values in the 'Active' column appropriately by subtracting the confirmed cases by deaths and recovered.
   - Data reduction: Since the data in the sample has long decimal values, we rounded them to four decimal places inorder to reduce the storage capacity

4. Transform and enrich data: Transforming data is the process of updating the format or value entries in order to reach a well-defined outcome, or to make the data more easily understood by a wider audience. In our dataset, transformation is done with attribute ‘Undernourished’ where entries with '<2.5' were replaced with 2.5; object type of this column was changed to float. Enriching data refers to adding and connecting data with other related information to provide deeper insights. It is observed that cereals (excluding beer) is the highly consumed food product in our dataset; so, we included this attribute as well to gain more insights.  


### Machine Learning   

We performed Unsupervised learning using Clustering to see how different countries are grouped based on food consumption, health factors and COVID death rates. And we executed Supervised learning using Decision trees.

Unsupervised Learning (Clustering):
- Since all other foods add up to attributes 'Animal products' and 'Vegetal products', we altered the data to include only these attributes to avoid multi-colinearity
- Data was scaled with RobustScaler()
- Completed Principle Component Analysis i.e, PCA (using sklearn.decomposition) in order to see how much variability each principle component captured, and found that we could capture close to 90% of the variation from the first two components, so we decided to proceed with 2 components
- KMeans clustering (from sklearn.cluster) performed with 3 clusters 
- In KMeans clustering, we need to decide the clusters before implementing the algorithm. Sometimes, we may not correctly interpret the number of clusters and it becomes challenging to predict the number of clusters. For Hierarchical clustering, we need not know the number of clusters prior to implementing the algorithm. Due to these reasons, we chose to perform Agglomerative Hierarchial clustering.
- Before implementing Hierarchical Clustering, the data was normalized (normalize from sklearn.preprocessing) so as to maintain same for each variable. If the variables are not scaled, there are chances that the model might become biased towards the variables with a larger magnitude.
- The linkage() function was used to obtain a hierarchical clustering on the data samples, and a Dendrogram was used to visualize the result.
- We can see that the vertical line with maximum distance is the blue line and hence we can decide a threshold of 3 to cut the dendrogram. The line cuts the dendogram at two points. So, we have two clusters. Applying the Agglomerative hierarchical clustering for 2 clusters. We can visually see the two clusters in the scatter plot for Obesity Vs Covd-19 Death rate.

Supervised Learning (Decision Trees):
- Next, we decided to build a decision tree using DecisionTreeClassifier from sklearn.tree. 
- Decision tree created has 3 clusters. Based on the tree results, cluster 2 contains Countries that have the highest fatalities, and should make lifestyle / policy changes for the future.


### Evaluation 

For K means clustering, we used Elbow method for evaluation. This method of evaluation gives us the best value of k without having to assign it randomly. Also, using a 70-30 split, we were able to get 92% accuracy on predicting which cluster a Country belongs to based on food and health factors of the Country.


## Issues and Solutions

Amount of observations are limited since the data is aggregated by Country and we moved forward with the analysis with the same. There were 23 food related attributes in the data, we were able to reduce them to 3 by finding the relationship between them.

## Instructions to run the project

Install the technologies necessary and run the Jupyter Notebook from the Anaconda prompt window.

## Conclusion 

We gathered, understood and pre-processed the data. Unique trait about the dataset is that it has miniature details of all the different types of foods consumed across the world. We answered the research question by performing Exploratory Data Analysis and creating multiple visualizations to get more insights on the dataset. Top 15 countries were identified based on Death, Obesity and Undernourishment rates. Additionally, the varying  patterns of the death and Obesity percentages among these countries were recognized.
	
Machine Learning Algorithms K means Clustering, Agglomerative Hierarchal Clustering and Decision trees are performed as a part of CRISP - DM process. These algorithms were evaluated using Elbow method and performance metrics such as accuracy and recall were obtained using confusion matrix and classification report.

There might be many external factors that affect the COVID death rates  in countries across the world. However, our analysis shows that maintaining a healthy diet and consuming food products with less fat reduces the risk of Obesity and can reduce the amount of deaths resulting due to COVID-19.

For future scope, we plan to include data related to other health factors and analyze how COVID-19 deaths are affected. We will try to build Machine Learning model with better accuracy and other performance metrics.
