# House-Price-Prediction
House Price Prediction for kaggle competition: https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques
The project's goal is to forecast the price of residential properties in Ames, Iowa. The price of each home was estimated using linear regression. A training and testing dataset was given to us so that we could use it to run our model. To make this forecast,  79 explanatory variables were made available. The features provided different details about the house, for example the number of rooms in a house or the condition of the house. Features provided were both numerical and non-numerical data types. 


**Numerical columns**

Examples of numerical columns provides are:
```
TotRmsAbvGrd: Total rooms above grade (does not include bathrooms)
Fireplaces: Number of fireplaces
GarageArea: Size of garage in square feet
````
**Non-numerical columns**

Other columns contained categorical data i.e. ordinal and nominal data 

Example of columns with nominal data:
```
PavedDrive: Paved driveway

       Y	Paved 
       P	Partial Pavement
       N	Dirt/Gravel

Street: Type of road access to property

       Grvl	Gravel	
       Pave	Paved
```
Examples of columns with ordinal data:
```
ExterQual: Evaluates the quality of the material on the exterior 
		
       Ex	Excellent
       Gd	Good
       TA	Average/Typical
       Fa	Fair
       Po	Poor

BsmtQual: Evaluates the height of the basement

       Ex	Excellent (100+ inches)	
       Gd	Good (90-99 inches)
       TA	Typical (80-89 inches)
       Fa	Fair (70-79 inches)
       Po	Poor (<70 inches)
       NA	No Basement
```
I joined the train and test data set for the data preprocessing.
Following my exploration of the data set, I discovered the following: 
- I noticed the target variable (i.e. the sale perice) is not normally distributed. This was solved by transforming it by logging it.  
- Some columns had up to 50% of missing data. Others had just a few missing. I discarded the columns with a lot of missing data and analysed the other columns individually.
- There were either nominal or ordinal data types in the non-numeric columns. Columns with ordinal datatypes that contain information in their ordering set were converted to integers using a label encoder, whereas columns with nominal datatypes were transposed using dummy variables.

------------------------------------------------------------------------------

I have 236 features to deal with after the preprocessing and transformation of the dataset. I conducted a linear regression with all the variables and split the dataset back into the training and testing dataset that were initially provided.
After doing cross-validation using cross_val_score, which is essentially a library used to ensure that all observations are used for both testing and training of a model, the model performed reasonably well. It received an overall score of 84%.


------------------------------------------------------------------------------

I chose to use the backward elimination strategy to eliminate the variables that were the least significant after noticing some variables in the model summary had lesser significance.

------------------------------------------------------------------------------


After the feature selection process, 107 features were returned which means 129 columns were removed from the dataset. I noticed a lot of categorical columns were discared. For example, information about the Exterior covering on house played little role in the price of the house. And was taken out.


------------------------------------------------------------------------------

I created a new model using the 107 variables, and after cross-validating, it increased by 2%, going from 84% to 86%. Although it's not much of an improvement, it's still an improvement.


