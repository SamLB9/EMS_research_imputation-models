# EasyMedStat imputation methods and models research
The aim of this project is to compare and study different imputation methods and different regression and classification models for different starting sample sizes and missing data percentages.
To do this, we chose to conduct our research using healthcare datasets to have a dataset that resembles as closely as possible the dataset that can be imported into the platform.

This first dataset contains 5735 observations.
First, we had to clean up the data by deleting rows containing missing data and transforming categorical variables into numerical variables using OneHotEncoder's SckLearn function, so that they could be taken into account in the models.
We will analyze the different models and imputation methods using 3 different sample sizes: 150, 500 and 1000 observations. These data sizes will be randomly selected from the cleane dataset with a size of 5735 rows.
For each sample, we imputed a certain percentage of missing data (10%, 20%, 25%, 30%, 40%, 50%) and then completed the missing values using different imputation methods (Drop, Median, Regression or Multiple).
We then split the dataset into a train part and a test part (70%-30%).

Finally, we were able to train and test the various models.
We recovered the best models and then tested them with a random sample of 150 observations from the initial dataset.
From the metrics of the various models, we created a csv file for subsequent analysis via graphs and other means.

Here's a diagram to help you clearly understand our process:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/6498bba2394adb60f1ae1d19b05fbca9ade664a4/Diagram_drawio.png)

To carry out this process, I've created a tool with several functions that allow me to compare different models using the Pycaret library.
In the files attached to this project you'll find two jupyter .ipynb files containing my code.
([Classification.ipynb](https://github.com/SamLB9/EMS_research_imputation-models/blob/fba7c93533dedf7a8dfc9d13b1a829bb195d5b3a/Classification_EMS.ipynb),
[Regression.ipynb](https://github.com/SamLB9/EMS_research_imputation-models/blob/05eff37eee9a2cae4e3b94e603c1a4c453b99316/Regression_Pycaret.ipynb))

My tool consists of a data cleaning function called "Prep()", a function that imputes missing values in different ways called "impute()", a "fitting()" function that compares different regression or classification models by testing them with a random sample of the original dataset and returns the metrics of the different models, a "save()" function that saves the metrics of the different models in a csv file and a "glob()" function that calls the above functions iteratively.

To compile my process, all I have to do is call the glob function, setting as parameters the address of the original dataset, the imputation method and the address of the various csvs that the function will create for me.

I then merged all the csvs so as to be able to analyze them using graphs.

Here's an overview of the data set we obtained after this process:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/b55ea070af72228af00d16c99d8010b8c876e685/MetricsData.png)

From here, we were able to analyze the different imputation methods and models in detail.

_____________________________________________________________________________________________________

Firstly, we will analyze the performance of the different models.

Here are three boxplots representing the different classification models according to their AUC and missing value percentage:

1000 rows:
![1000 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/4dd325cda9184cbe3060fc2635a6ac8fe1ce89b8/C_MODELSCOMPARAISON_1000ROWS.png)
500 rows:
![500 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/4dd325cda9184cbe3060fc2635a6ac8fe1ce89b8/C_MODELSCOMPARAISON_500ROWS.png)
150 rows:
![150 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/4dd325cda9184cbe3060fc2635a6ac8fe1ce89b8/C_MODELSCOMPARAISON_150ROWS.png)


And here is a boxplot showing the different classification models in their entirety:
![Global classification models comparaison](https://github.com/SamLB9/EMS_research_imputation-models/blob/1d203bf5507b56e0d2be954e59dc3c4bb70eb3bc/C_GlobalModelsComparaison.png)

We note that the two classification models with the best performance according to the median are the 'Random Forest Classifier' and the 'Extra Trees Classifier'.

In order to analyze the performance of the different imputation methods, I have once again chosen to use boxplots. 

Here's a box plot representing the different imputation methods according to their AUC as a function of the percentage of missing value. To do this, I decided to use the best classification model, the "Random Forest Classifier":

1000 rows:
![1000 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/758bd4fd41e809fe14d29666cdc38ad786970622/C_BoxPlot_RandomForestClassifier_Classification_1000rows.png)
500 rows:
![500 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/758bd4fd41e809fe14d29666cdc38ad786970622/C_BoxPlot_RandomForestClassifier_Classification_500rows.png)
150 rows:
![150 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/eaa13f2c3de6121fed887a4a1b647d1e4ff91ae7/C_BoxPlot_RandomForestClassifier_Classification_150rows.png)

_____________________________________________________________________________________________________

Similarly, here are three boxplots comparing the performance of regression models according to RMSE:

1000 rows:
![1000 rows](https://github.com/SamLB9/EMS_research_imputation-models/blob/b92c6e06cebf6c83d7aa0292dd25ef22c6119344/R_MODELSCOMPARAISON_1000ROWS.png)
500 rows:
![500 rows](https://github.com/SamLB9/EMS_research_imputation-models/blob/b92c6e06cebf6c83d7aa0292dd25ef22c6119344/R_MODELSCOMPARAISON_500ROWS.png)
150 rows:
![150 rows](https://github.com/SamLB9/EMS_research_imputation-models/blob/b92c6e06cebf6c83d7aa0292dd25ef22c6119344/R_MODELSCOMPARAISON_150ROWS.png)

And here is a boxplot showing the different regression models in their entirety:
![Global regression models comparaison](https://github.com/SamLB9/EMS_research_imputation-models/blob/1d203bf5507b56e0d2be954e59dc3c4bb70eb3bc/R_GlobalModelsComparaison.png)

We note that the three regression models with the best performance according to the median are the 'Extra Trees Regressor', the 'Extreme Gradient Boosting' and the 'Random Forest Regressor'.

In order to analyze the performance of the different imputation methods, I have once again chosen to use boxplots. 

Here's a box plot representing the different imputation methods according to their RMSE as a function of the percentage of missing value. To do this, I decided to use the best regression models, the 'Extreme Gradient Boosting':

1000 rows:
![1000 rows:]()
500 rows:
![500 rows:]()
150 rows:
![150 rows:]()

_____________________________________________________________________________________________________


