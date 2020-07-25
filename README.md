# **Influnces of food consumption and health factors on COVID-19**
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
Country - 	Countries around the world
Alcoholic Beverages - 	Percentage of food intake (kg) from alcoholic beverages
Animal fats - 	Percentage of food intake (kg) from animal fats
Animal Products - 	Percentage of food intake (kg) from animal products
Aquatic Products, Other - 	Percentage of food intake (kg) from aquatic products
Cereals - Excluding Beer -	Percentage of food intake (kg) from cereals - excluding beer
Eggs - 	Percentage of food intake (kg) from eggs
Fish, Seafood - 	Percentage of food intake (kg) from fish, seafood
Fruits : Excluding Wine - 	Percentage of food intake (kg) from fruits - excluding wine
Meat - 	Percentage of food intake (kg) from meat
Miscellaneous - 	other food
Milk - Excluding Butter - 	milk consumption except butter
Offals - 	internal organ meat 
Oilcrops - 	oil crops that are used 
Pulses - 	edible seedds like beans,lentils
Spices - 	Seasoning and spices that are used
Starchy Roots - 	foods that grow downward and holds the plant in place like potatoes, carrots and others
Stimulants - 	% of Coffee, cocoa, tea consumption 
Sugar Crops - 	crops that are major sources of sugar which includes sugar, honey, corn
Sugar & Sweeteners - 	sugar and sugar subtitutes
Treenuts - 	% of nuts consumed
Vegetal Products - 	% of vegetable products consumed
Vegetable Oils - 	prominent oil crops consumed
Vegetables - 	% of vegetables consumed
Obesity - 	people suffering from obesity
Undernourished - 	% of populations that is undernourished
Confirmed - 	No of confirmed covid cases
Deaths - 	No of deaths reported due to covid
Recovered - 	No of patients recovered from Covid
Active -	No of covid cases that are currently active
Population - 	 Total Population reported for each nation

## Approach
  
### Data understanding & EDA

#### Describe data 
Once we have identified the data set, we need to describe its contents and explore insights to better understand the data and its business implications. To describe the data, we can create a data dictionary that lists down the types of variables, the number of records, and the types of analysis. 

#### Explore data
EDA will help to give insight of data and understand latest trends. To explore data, we can plot simple graphs on Python, e.g. to understand the trend in data or to get a graphical representation of data for better understanding to get useful insights.  We will start off by reading the dataset into a pandas dataframe. We can then apply various summarizing functions to the data frame such as .info() and .describe(). Different visualization tools like Seaborn are used for EDA.  
It is also important to see the distribution of variables and for this we can plot histograms and standardize the dataset if needed.
  
### Data Preparation 
As part of the Data Preparation, to handle missing values we will be performing imputation. Any outliers will be taken care of. 
If required, scaling would be done on some of the attributes and we would be dropping any variables that are not needed. 

### Machine Learning   

We can apply a regression model with the predictor variables being different food types and health factors. The outcome variable will be the fatality rate of COVID-19.  We can also look at clustering the dataset to see how different countries are grouped based on food, health, and covid factors. 

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

## Conclusion 
