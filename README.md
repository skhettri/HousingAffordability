# HousingAffordability
Introduction

The aim of this report is to show the study on current market value of unit using statistical tools. The source of data is based on American Housing Survey (AHS) national files from 2011 and 2013, downloaded from https://www.huduser.gov/portal/datasets/hads/had s.html. 
Task 1

Following steps were used to reduce variables from the original dataset. 

Step 1: Based on observation of data set and documentation of HADS (Housing Affordability Data System), out of 99 variables, around 34 variables were selected including dependent variable to check the correlation before using in regression analysis.

Step 2: Analyzed variables using correlation heat map, to consider if they are useful to use in the model. From the correlation matrix further reduction on variable was done, only 12 dependent variables were chosen for next step analysis.
![image](https://user-images.githubusercontent.com/91941680/162767610-bd16ee69-bb07-44b8-ac39-ba1a17199d9d.png)

Revised correlation heat map is shown below:
![image](https://user-images.githubusercontent.com/91941680/162767736-99c493bd-5e1d-4505-9640-4351259e8400.png)
Step 3: Finally, one variable “BURDEN” was removed after applying “Backward Elimination” statistical tool in python to improve the model. 
![image](https://user-images.githubusercontent.com/91941680/162767793-2de646e1-ac11-4568-946d-785cc908b960.png)
Below tasks were performed before estimation regression model:
1.	When analyzing dependent variable “VALUE”, using histogram plot (first figure), it is right skewed which means mean is greater than median possibly due to outliers and other unknown factors. Therefore, after converting “VALUE” histogram (second figure) into log scale it resembled closer to Bell curve (normally distributed). This is suggesting, variable transformation is required in this dataset.
![image](https://user-images.githubusercontent.com/91941680/162767858-87dca984-511a-49a3-9f18-9066062904ea.png)
2.	For the categorical variable “METRO3”, categories were collapsed into two “Central city area” and “Not a Central city area”.
3.	All the variables were normalized using z-score method, for unbiased comparison and interpretation of the estimated model. There are independent variables such as number of rooms, household income, monthly household cost which are in different units. Thus, they had to be normalized. 
4.	Below is the estimated regression model using Ordinary Least Square regression (OLS). In the estimated model, only 46% variation in value of housing unit (dependent variable) is explained by the selected independent variables such as number of rooms, number of bedrooms, household income etc. 
Prob(F-Statistic) is equal to 0, which tells the overall significance of the regression model. 
![image](https://user-images.githubusercontent.com/91941680/162767926-36663c34-04d4-46a2-8dff-0bf2369230d6.png)
Interpretation of impact of various variables include in model

All the independent variables’ p-value is almost equal to 0, which shows relationships are statistically significant with the dependent variable (“VALUE”). The data provides enough evidence to support there is a non-zero correlation with the dependent variable. Any changes in the independent carriable are associated with the changes in the dependent variable. These variables are statically significant and probably worthwhile addition to the regression model. 
Below histogram is the residual plot to show the unbiased estimates. It is roughly normally distributed which suggests there is no problem in the variables included in the model.
![image](https://user-images.githubusercontent.com/91941680/162767975-fe116b83-b92e-4862-b63d-3d5d8574fc3d.png)

Each variable impact, used in the model are interpreted as follow:
a.	Independent variables from the model: “FMR” (fair market rent ‘average’), “ROOMS’ (number of rooms), “ZINC2” (household income), “ZSMHC” (monthly housing cost), “UTILITY” (monthly utility costs), “OTHERCOST” (Insurance, condo, land rent, other mobile home fees), “METRO3” (Type of residential area) have positive impact on market value of housing unit. Holding other variables in the model constant any one variable increment will increase the average market value of housing unit. 
b.	Meanwhile independent variables from the model: “BEDRMS” (number of bedrooms), “BUILT” (year unit was built), “PER” (number of people living in the household), “GLMED” (Growth-adjusted median income) have negative impact on market value of housing unit. Holding other variables in the model constant any one variable increment will decrease the average market value of housing unit. 
c.	Furthermore, to test the multicollinearity problem, VIF of each independent variable was carried out. Result shows all the variable less than 10. 
![image](https://user-images.githubusercontent.com/91941680/162768039-05402f9e-c46e-4ea8-a870-e594ec1887db.png)
d.	Prediction was done using dependent and independent variable from same year 2013. Data was divided into two sets (Training and Validation). For the validation 1000 records were randomly reserved from the full dataset. 
i.	The histogram of validation and training shows closer to normally distributed. 
![image](https://user-images.githubusercontent.com/91941680/162768092-30115658-c97b-4bd3-94c6-3f4a870199b4.png)
![image](https://user-images.githubusercontent.com/91941680/162768112-37c1d22a-90df-4c9a-8773-7fefbf50ce16.png)
ii.	MAPE is high, which suggest model is affected by outliers. The performance of training data is as below:
![image](https://user-images.githubusercontent.com/91941680/162768152-3691fd61-5d15-47c0-9299-f2507b5bdcb2.png)
iii.	MAPE is higher than training dataset, which is also affected by the outliers. The prediction performance of validation data is as below:
![image](https://user-images.githubusercontent.com/91941680/162768203-e8b4729f-2d6e-4f9b-b8c4-42d5f39210f0.png)
Task 2

Under this task 2011 data is taken for independent variable and 2013 data is taken for dependent variable. For the prediction, dataset is divided into training dataset and validation dataset in which 1000 random records are reserved for validation dataset.

Regression model and justification of selection of X variables 

For the selection of independent variables, all the variables applied in Task 1 from step 2 was chosen to run the regression. However, when applied “Backward Elimination” method variable “BUILT” was removed from the model. 
![image](https://user-images.githubusercontent.com/91941680/162768515-62cb3958-ad80-429b-bb14-a713cd27ea28.png)

Regression Output

All the variable data were normalized using z-score. In the estimated model, only 37.5% variation in value of housing unit (dependent variable) is explained by the selected independent variables such as number of rooms, number of bedrooms, household income etc. Prob(F-Statistic) is equal to 0, which tells the overall significance of the regression model. The regression output is after removing variable suggested in “Backward elimination” method. 

![image](https://user-images.githubusercontent.com/91941680/162768560-37849712-0002-4daa-9ff1-86320b0ac8fc.png)
All the independent variables’ p-value is almost equal to 0, which shows relationships are statistically significant with the dependent variable (“VALUE”). However, independent variable “GLMED” (Growth-adjusted median income) is the only variable which is not significant to our dependent variable. The data provides enough evidence to support there is a non-zero correlation with the dependent variable. Except “GLMED”. Any changes in the independent carriable are associated with the changes in the dependent variable. These variables are statically significant and probably worthwhile addition to the regression model. 
Below histogram is the residual plot to show the unbiased estimates. It is roughly normally distributed which suggests there is no problem in the variables included in the model.
![image](https://user-images.githubusercontent.com/91941680/162768596-7a615b4a-62b4-4144-a0b5-970a383a2984.png)
Each variable impact, used in the model are interpreted as follow:
a.	Independent variables from the model: “FMR” (fair market rent ‘average’), “ROOMS’ (number of rooms), “ZINC2” (household income), “ZSMHC” (monthly housing cost), “UTILITY” (monthly utility costs), “OTHERCOST” (Insurance, condo, land rent, other mobile home fees), “BURDEN” (Housing cost as a fraction of income), “METRO3” (Type of residential area) have positive impact on market value of housing unit. Holding other variables in the model constant any one variable increment will increase the average market value of housing unit. 
b.	Meanwhile independent variables from the model: “BEDRMS” (number of bedrooms), “PER” (number of people living in the household), “GLMED” (Growth-adjusted median income) have negative impact on market value of housing unit. Holding other variables in the model constant any one variable increment will decrease the average market value of housing unit. 
c.	Furthermore, to test the multicollinearity problem, VIF of each independent variable was carried out. Result shows all the variable less than 10. 

![image](https://user-images.githubusercontent.com/91941680/162768635-89803ab2-584a-4c83-9729-57d714ebcb3d.png)
Prediction Performance 

For the prediction, ‘β’coefficients from regression model and X variables from ‘training set’, predict VALUE for each Housing Unit in the validation set was used. Below is the performance result of prediction: 

a.	Prediction was done using dependent from 2013 data and independent variable from 2011. The histogram of validation and training shows closer to normally distributed. 
![image](https://user-images.githubusercontent.com/91941680/162768688-80f33653-9ff9-4093-9359-5bd3ba758e32.png)
![image](https://user-images.githubusercontent.com/91941680/162768692-d1413f51-c3e6-430d-a308-2ee646219547.png)
b.	MAPE is high, which suggest model is affected by outliers. The performance of training data is as below:
![image](https://user-images.githubusercontent.com/91941680/162768753-884bc057-ce7f-4f1f-94b5-241097acd836.png)
c.	MAPE is higher than training dataset, which is also affected by the outliers. The prediction performance of validation data is as below:
![image](https://user-images.githubusercontent.com/91941680/162768799-2dfd3c21-5841-4078-b76b-3909a02bdcb7.png)














