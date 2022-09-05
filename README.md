# Earthquck_damage_prediction
## Overview of the Project
<div align="justify">
The purpose of the project was to use machine learning to predict the damage classification of buildings as a result of the Gorkha earthquake in Nepal in April 2015. The Gorkha earthquake was 7.8 in magnitude and occurred near the Gorkha district of Gandaki Pradesh, Nepal. Almost 9,000 lives were lost, millions of people were instantly made homeless, and $10 billion in damages about half of Nepal's nominal GDP was incurred.


<div align="center">

![image](https://user-images.githubusercontent.com/103223944/188395209-6972ab81-017b-4f8a-8456-df3e2f2ab7c0.png)

Figure1: Buildings destroyed in the 2015 Nepal earthquake (Source: Hilmi Hacaloğlu)

<div align="justify">

The dataset used for the project is one of the largest post-disaster datasets ever collected. The dataset includes more than 760,000 buildings inspected after the earthquake. The entry for each building contains valuable information on earthquake impacts, household conditions, and socio-economic-demographic statistics. The target variable is the damage grade and that has 5 classes, labelled as 'Grade 1' to 'Grade 5', each representing different scale of the damage sustained to the building. Damage grade can be used as a metric to decide about the level of the retrofit needed for each building.

## Data Extract, Transform and Load 
The first step in data preparation included downloading the raw data in form of CSV files from 2015 Nepal Earthquake: Open Data Portal (npc.gov.np). Then, PostgreSQL was used to import the CSV files into the SQL database, modify them as needed and then combine them into a table that then exported as CSV file for performing exploratory data analysis using Python. 
## Exploratory Data Analysis
The original dataset included about 760,000 rows and 120 columns. Each row included information such as the district id, building id, damage grade, building age, building height, building plinth area, building structural component types and geotechnical condition of the site. 
Jupyter Notebook and Python libraries were used for the exploratory data analysis (EDA) to better understand the dataset. Understanding the relationships between the damage grade and other variables, identifying outliers, binning the data, removing null values, and identifying the relevant features were among the steps taken to understand and prepare the dataset before using it as an input to the machine learning models. 
Data exploration started with screening the variables (columns) that were obviously uncorrelated to the building damage such as the occupancy classifications. Then, EDA was used to analyze the distribution of the remaining variables to find outliers and bin the data as needed. An example of the variables with extremely unbalanced distribution is shown in Figure 2 where it seems necessary to bin the building age data. This was found to have a meaningful impact on the performance of the machine learning models. 

<div align="center">

![image](https://user-images.githubusercontent.com/103223944/188395949-6aae54b1-ef5f-453d-a30c-d2515589b8f7.png)

Figure 2: Building age distribution 

<div align="justify">
  
EDA was also used to visualize the damage distribution as well as the correlation between the damage grade and other variables. Based on the damage grade distribution shown in Figure 3, it was decided to use the oversampling algorithm to create a balanced training dataset. Although the original dataset was not severely unbalanced, oversampling the data was found to have a meaningful impact on the performance of the machine learning models. Figure 4 shows an example plot for the correlation between the damage grade and the building floor type.   
  
<div align="center">

![image](https://user-images.githubusercontent.com/103223944/188397741-4860dc84-79af-4b94-bd6f-7871c263d923.png)

Figure 3: Damage grade distribution   
  
![image](https://user-images.githubusercontent.com/103223944/188396298-890a9fa6-15be-43a8-86ad-b015e14d9f67.png)

Figure 4: Correlation between damage grade and floor type  

<div align="justify">

## Machine Learning Models
Once the dataset was cleaned and ready to be used in the machine learning models, OneHotEncoder was used to convert the non-continuous data to categorial data and then the dataset was split into the train and test datasets. Three different models namely Multinominal Logistic Regression model, Balanced Random Forest Classifier and Neural Network were used to predict the damage grade based on the considered features such as the district, age, height, structural type, and site condition. 
Figure 5 through Figure 7 and Table 1 summarize the performance of the three models.  Looking at the accuracy and F1 score, the first and last model yielded similar performance. However, it should be noted that the first model was significantly faster than the last model. 

<div align="center">
  
![image](https://user-images.githubusercontent.com/103223944/188396709-319554d9-7b7d-4eb9-af5f-54adcf37ee25.png)
 
Figure 5: Balanced Random Forest Classifier model performance

![image](https://user-images.githubusercontent.com/103223944/188396735-b357ad89-992b-4395-88a6-488ca264f7a8.png)
 
Figure 6: Balanced Random Forest Classifier model performance

![image](https://user-images.githubusercontent.com/103223944/188494670-a5796e97-25e1-4021-beb9-acf314c8f0b4.png)
  
Figure 7: Neural Network model performance

Table 1: Performance of different models (weighted average)

![image](https://user-images.githubusercontent.com/103223944/188494733-a58ebe3a-bf96-49ab-9f57-23a32d8b43ce.png)
