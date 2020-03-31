# Project 2 - Ames Housing Sale Price Prediction

## Problem statement

Ames is a city in Iowa, United States.The dataset provides information about the various factors that influence the sale price of house in ames city. Most of the variables are exactly the type of information that a typical home buyer would want to know about a potential property. This project will study the various features which affects the sale price of the house and create a regression model based on the Ames Housing Dataset, which can be used to predict the sale price of a house based on those influential features.


## Executive Summary
     Contents
- [Train Data Import & Cleaning](#Train-Data-Import-and-Cleaning)
>1.Reading train Data<br>
>2.Display data<br>
>3.Data types<br>
>4.Data description<br>
>5.Null values<br>
>6.Overview of dataset<br>
>7.Dropping Unnecessary Rows<br>
>8.Filling Missing values<br>
>9.Complete Dataset<br>
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
>1.Summary Statistics<br>
>2.Exploratory Visualizations<br>
- [Pre-processing](#Pre-processing)
>1.Categorical columns<br>
>2.Ordinal Columns<br>
>3.Nominal Columns<br>
>4.Numerical Columns<br>
>5.Label Encoding<br>
>6.One Hot Encoding<br>
- [Modeling](#Modeling)
>1.Creating features matrix (`X`) and target vector (`y`)<br>
>2.Train/test split<br>
>3.Scaling<br>
>4.Instantiating Models<br>
>5.Model Fitting and Evaluation<br>
>6.Final Model<br>
- [Inferential Visualizations](#Inferential-Visualizations)<br>
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)<br>
- [Kaggle Submission](#Kaggle-Submission)
>1.Reading test Data<br>
>2.Display Data<br>
>3.Data types<br>
>4.Number of null Values<br>
>5.Filling Null values<br>
>6.Summary Statistics<br>
>7.Label Encoding<br>
>8.One Hot Encoding<br>
>9.X_test<br>
>10.Predictions<br>
>11.Creating .csv file<br>



### Train Data Import & Cleaning

This involves importing the train dataset and process of detecting and correcting inaccurate records of the data and then replacing, modifying and deleting the coarse data.The datset has numerous null values which are imputed based on statistics and dropping outliers to attain a ccomplete dataset without any null values.

### Data Dictionary
**train data**

The data has 81 columns which include 22 nominal, 21 ordinal, 38 numeric variables 


| Feature | Description |
| --- | ---|
ID (Discrete)| Identification number
PID (Nominal)| Parcel identification number  - can be used with city web site for parcel review. 
MS SubClass (Nominal)| Identifies the type of dwelling involved in the sale.       
MS Zoning (Nominal)| Identifies the general zoning classification of the sale.	
Lot Frontage (Continuous)| Linear feet of street connected to property
Lot Area (Continuous)| Lot size in square feet
Street (Nominal)| Type of road access to property      	
Alley (Nominal)| Type of alley access to property		
Lot Shape (Ordinal)| General shape of property      
Land Contour (Nominal)| Flatness of the property		
Utilities (Ordinal)| Type of utilities available	
Lot Config (Nominal)| Lot configuration	
Land Slope (Ordinal)| Slope of property     
Neighborhood (Nominal)| Physical locations within Ames city limits (map available)			
Condition 1 (Nominal)| Proximity to various conditions	
Condition 2 (Nominal)| Proximity to various conditions (if more than one is present)      
Bldg Type (Nominal)| Type of dwelling	
House Style (Nominal)| Style of dwelling	
Overall Qual (Ordinal)| Rates the overall material and finish of the house	
Overall Cond (Ordinal)| Rates the overall condition of the house		
Year Built (Discrete)| Original construction date
Year Remod/Add (Discrete)| Remodel date (same as construction date if no remodeling or additions)
Roof Style (Nominal)| Type of roof		
Roof Matl (Nominal)| Roof material		
Exterior 1 (Nominal)| Exterior covering on house	
Exterior 2 (Nominal)| Exterior covering on house (if more than one material)	
Mas Vnr Type (Nominal)| Masonry veneer type     
Mas Vnr Area (Continuous)| Masonry veneer area in square feet
Exter Qual (Ordinal)| Evaluates the quality of the material on the exterior 		
Exter Cond (Ordinal)| Evaluates the present condition of the material on the exterior		
Foundation (Nominal)| Type of foundation		
Bsmt Qual (Ordinal)| Evaluates the height of the basement		
Bsmt Cond (Ordinal)| Evaluates the general condition of the basement
Bsmt Exposure	(Ordinal)| Refers to walkout or garden level walls      
BsmtFin Type 1	(Ordinal)| Rating of basement finished area		
BsmtFin SF 1 (Continuous)| Type 1 finished square feet
BsmtFinType 2	(Ordinal)| Rating of basement finished area (if multiple types)
BsmtFin SF 2 (Continuous)| Type 2 finished square feet
Bsmt Unf SF (Continuous)| Unfinished square feet of basement area
Total Bsmt SF (Continuous)| Total square feet of basement area
Heating	(Nominal)| Type of heating		
HeatingQC (Ordinal)| Heating quality and condition
Central Air (Nominal)| Central air conditioning		
Electrical (Ordinal)| Electrical system		
1st Flr SF (Continuous)| First Floor square feet 
2nd Flr SF (Continuous)	| Second floor square feet
Low Qual Fin SF (Continuous)| Low quality finished square feet (all floors)
Gr Liv Area (Continuous)| Above grade (ground) living area square feet
Bsmt Full Bath (Discrete)| Basement full bathrooms
Bsmt Half Bath (Discrete)| Basement half bathrooms
Full Bath (Discrete)| Full bathrooms above grade
Half Bath (Discrete)| Half baths above grade
Bedroom (Discrete)| Bedrooms above grade (does NOT include basement bedrooms)
Kitchen (Discrete)| Kitchens above grade
KitchenQual (Ordinal)| Kitchen quality      	
TotRmsAbvGrd	(Discrete)| Total rooms above grade (does not include bathrooms)
Functional (Ordinal)| Home functionality (Assume typical unless deductions are warranted)		
Fireplaces (Discrete)| Number of fireplaces
FireplaceQu (Ordinal)| Fireplace quality		
Garage Type (Nominal)| Garage location     
Garage Yr Blt (Discrete)| Year garage was built		
Garage Finish (Ordinal)	| Interior finish of the garage		
Garage Cars (Discrete)| Size of garage in car capacity
Garage Area (Continuous)| Size of garage in square feet
Garage Qual (Ordinal)| Garage quality		
Garage Cond (Ordinal)| Garage condition		
Paved Drive (Ordinal)| Paved driveway		
Wood Deck SF (Continuous)| Wood deck area in square feet
Open Porch SF (Continuous)| Open porch area in square feet
Enclosed Porch (Continuous)| Enclosed porch area in square feet
3-Ssn Porch (Continuous)| Three season porch area in square feet
Screen Porch (Continuous)| Screen porch area in square feet
Pool Area (Continuous)| Pool area in square feet
Pool QC (Ordinal)|Pool quality		
Fence (Ordinal)| Fence quality	
Misc Feature (Nominal)| Miscellaneous feature not covered in other categories		
Misc Val (Continuous)| Value of miscellaneous feature
Mo Sold (Discrete)| Month Sold (MM)
Yr Sold (Discrete)| Year Sold (YYYY)
Sale Type (Nominal)| Type of sale		
Sale Condition (Nominal)| Condition of sale
SalePrice (Continuous)| Sale price $

Click here to view complete data description(http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

### Exploratory Data Analysis

 This explores the descriptive and inferential statistics.
The following relationship has been graphically visualised: <br>
**Histogram**-the spread of Sale Price  <br>
**Scatter plot** -to understand the relationship between Sale Price and Living Area and the relationship between Sale price and Year Sold <br>
**Pair plot**- to understand the relationship between Sale Price and Garage area,Living Area and Basement Area<br>	


## Pre-processing
This involves seperating the columns into nominal,ordinal and numerical values.Using Label encoding to impute values into ordinal columns based on the rating of the category and One hot Encoding to impute values on nominal columns.

## Modeling

This involves creating features matrix (`X`) and target vector (`y`),Spliting the data into train and test set,scaling the features and instatiating the models.This table shows the models with corresponding r2 value.

| Regression Type | R2 Values |
| --- | ---|
Linear Regression| -1.56852
Lasso Regression| 0.79699423
Ridge Regression| 0.839138
Elastic Net Regression| 0.84045

Based on r2 value,Elastic Net is choosen as final model to fit and evaluate.Highly coefficient features are selected based on this model which is again trained and tested.

## Inferential Visualizations
This shows graphical representation of features that highly influence sale Price and Elastic Net residual plot.

## Conclusions and Recommendations
The top feature that highly influence the sale price at a coefficient of 16790.143356 is **Overall Quality** which  represents the overall material and finish of the house.The other top features include size of **Living Area**, followed by  **Garage** and **Basement area**.This is obvious as the potential buyer will look forward for all these qualities in his/her dream home.**Fireplace** is also one of the most influencing feature, as the temperature in winter drops to average 12 degree Farenhiet.

Another top feature that highly influences the price is properties located at Stone Brooks neighbourhood.It is clearly evident as Stone Brooke is a residential community in Ames, Iowa.Conveniently located on the north side of the city, it is within a few minutes drive or public transport ride to the Iowa State University campus and the Ames Shopping Mall.

However it is interesting to note that Exterior qulaity and kitchen quality is negatively related to Sale price.

All these features will enable property developers to better target buyers, or educate home owners on the Sale price of the houses.

This project is developed based on Ames housing dataset,It can be generalized to other cities by removing certain columns like neighbourhood which is specific to Ames city and also by gaining additional data like population, educational institutions near the property and pollution index etc.

## Kaggle Submission
Test data is imported and cleaned similar to train dataset.Only the features which have been slected from train data is retained in test dataset.This is trained and scaled to predict y values which is stored in .csv file along with id of the property and submitted to kaggle competititon.
