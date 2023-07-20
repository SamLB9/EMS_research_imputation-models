# EasyMedStat imputation methods and models research
### The aim of this project is to compare and study different imputation methods and different regression and classification models for different starting sample sizes and missing data percentages.
To do this, we chose to conduct our research using an [healthcare dataset](https://github.com/SamLB9/EMS_research_imputation-models/blob/55db256762acc0ee79d8a105aa6f61c4943150f4/rhcmod-latest-version-5735patients%20(1).csv) to have a dataset that resembles as closely as possible the dataset that can be imported into the platform.

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
To maximize the robustness of the results, we have chosen to compile the function 5 times for each case to minimize potential biased results.

I then merged all the csvs so as to be able to analyze them using graphs.

Here's an overview of the data set we obtained after this process:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/b55ea070af72228af00d16c99d8010b8c876e685/MetricsData.png)

From here, we were able to analyze the different imputation methods and models in detail.

_____________________________________________________________________________________________________

### Firstly, we will analyze the performance of the different models

Here are three boxplots representing the different classification models according to their AUC (index to maximize) and missing value percentage:

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

Here are three box plot representing the different imputation methods according to their AUC as a function of the percentage of missing value and of the data size. To do this, I decided to use the best classification model, the "Random Forest Classifier":

1000 rows:
![1000 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/758bd4fd41e809fe14d29666cdc38ad786970622/C_BoxPlot_RandomForestClassifier_Classification_1000rows.png)
500 rows:
![500 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/758bd4fd41e809fe14d29666cdc38ad786970622/C_BoxPlot_RandomForestClassifier_Classification_500rows.png)
150 rows:
![150 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/eaa13f2c3de6121fed887a4a1b647d1e4ff91ae7/C_BoxPlot_RandomForestClassifier_Classification_150rows.png)

### We immediately notice that there is a positive relationship between the number of dataset observations and model performance, and a negative relationship between the percentage of missing value and model performance. It's good to see this, despite the fact that it was to be expected. We can also see that there is no optimal imputation method. 

Here are three boxplot representing the different imputation methods according to their AUC as a function of the data size:

1000 rows:
![](https://github.com/SamLB9/EMS_research_imputation-models/blob/86b2bfa52205000c2065ce42a2b20b496ff6cfd2/C_BoxPlot_ImputationMethodComparaison_1000ROWS.png)
500 rows:
![](https://github.com/SamLB9/EMS_research_imputation-models/blob/86b2bfa52205000c2065ce42a2b20b496ff6cfd2/C_BoxPlot_ImputationMethodComparaison_500ROWS.png)
150 rows:
![](https://github.com/SamLB9/EMS_research_imputation-models/blob/86b2bfa52205000c2065ce42a2b20b496ff6cfd2/C_BoxPlot_ImputationMethodComparaison_150ROWS.png)

Here's a boxplot representing the different imputation methods performance globally:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/86b2bfa52205000c2065ce42a2b20b496ff6cfd2/C_BoxPlot_GlobalImputationMethodComparaison.png)

### We can conclude that the Multiple imputation method is globaly the best imputation method but isn't robust because it's not the better one when the datasize is small. Therefore when we want to do a classification model with a big data set it's more interresting to use the Multiple imputation method. Conversely, when the dataset is small, it's more interesting to impute by median.

_____________________________________________________________________________________________________

### Similarly, here are three boxplots comparing the performance of regression models according to their RMSE (index to minimize) and their missing value percentage:

1000 rows:
![1000 rows](https://github.com/SamLB9/EMS_research_imputation-models/blob/c843b919bf7fa7f2f62f2205616a7b38a93bae9c/R_MODELSCOMPARAISON_1000ROWS.png)
500 rows:
![500 rows](https://github.com/SamLB9/EMS_research_imputation-models/blob/b92c6e06cebf6c83d7aa0292dd25ef22c6119344/R_MODELSCOMPARAISON_500ROWS.png)
150 rows:
![150 rows](https://github.com/SamLB9/EMS_research_imputation-models/blob/b92c6e06cebf6c83d7aa0292dd25ef22c6119344/R_MODELSCOMPARAISON_150ROWS.png)

And here is a boxplot showing the different regression models in their entirety:
![Global regression models comparaison](https://github.com/SamLB9/EMS_research_imputation-models/blob/1d203bf5507b56e0d2be954e59dc3c4bb70eb3bc/R_GlobalModelsComparaison.png)

We note that the three regression models with the best performance according to the median are the 'Extra Trees Regressor', the 'Extreme Gradient Boosting' and the 'Random Forest Regressor'.

In order to analyze the performance of the different imputation methods, I have once again chosen to use boxplots. 

Here are three box plot representing the different imputation methods according to their RMSE as a function of the percentage of missing value and of the data size. To do this, I decided to use the best regression models, the 'Extreme Gradient Boosting':

1000 rows:
![1000 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/48b6145e03dbcbb2a131a711b653c92a79de8afb/R_BoxPlot_ExtremeGradientBoosting_1000rows.png)
500 rows:
![500 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/161f4537856f0915531f5b4d1c7420de0648c803/R_BoxPlot_ExtremeGradientBoosting_500rows.png)
150 rows:
![150 rows:](https://github.com/SamLB9/EMS_research_imputation-models/blob/161f4537856f0915531f5b4d1c7420de0648c803/R_BoxPlot_ExtremeGradientBoosting_150rows.png)

### We immediately notice that there is a positive relationship between the number of observations in the dataset and model performance, and a negative relationship between the percentage of missing values and model performance. This is a good thing, although not unexpected. We can also see that there is no true optimal imputation method, but that the multiple imputation method seems to be the worst imputation method for the regression model. The elimination imputation method performs better when the amount of data is small. If we consider these three box plots, the regression imputation method appears to be the most robust, although it performs less well when the amount of data is low. 

Using the three boxplots below, we're going to check our assumptions. They represent the performance of imputation methods as a function of data set size.

1000 rows:
![](https://github.com/SamLB9/EMS_research_imputation-models/blob/78a9896a5b9373fdbc73bd599793bce9ac7c97dd/R_BoxPlot_ImputationMethodComparaison_1000ROWS.png)
500 rows:
![](https://github.com/SamLB9/EMS_research_imputation-models/blob/78a9896a5b9373fdbc73bd599793bce9ac7c97dd/R_BoxPlot_ImputationMethodComparaison_500ROWS.png)
150 rows:
![](https://github.com/SamLB9/EMS_research_imputation-models/blob/78a9896a5b9373fdbc73bd599793bce9ac7c97dd/R_BoxPlot_ImputationMethodComparaison_150ROWS.png)

Here's a boxplot representing the different imputation methods performance globally:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/78a9896a5b9373fdbc73bd599793bce9ac7c97dd/R_BoxPlot_GlobalImputationMethodComparaison.png)

### Effectively by considering the impution method performance by them median, Regression imputation method is globaly the best one for regression. The Drop option is also an excellent imputation method, but is not as effective as regression when the amount of data is relatively large.

_____________________________________________________________________________________________________

### We will now analyze whether the best-performing imputation methods are the same for all models.
To achieve this, we will use imputation methods with different classification models (Random Forest Classifier, Extra Trees Classifier, Extreme Gradient Boosting and Light Gradient Boosting Machine).

1000 rows:
Random Forest Classifier:

Extra Trees Classifier: 

Extreme Gradient Boosting:

Light Gradient Boosting Machine:

500 rows:
Random Forest Classifier:

Extra Trees Classifier: 

Extreme Gradient Boosting:

Light Gradient Boosting Machine:

150 rows:
Random Forest Classifier:

Extra Trees Classifier: 

Extreme Gradient Boosting:

Light Gradient Boosting Machine:

## Conclusion:
The bottom line is there is not big differencies between the different imputation methods but according to the amount of data and the percentage of missing value we notice some trends. It's important to point out that our conclusions are not the same for regression and classification models, and the best imputation methods are not the same. As far as models are concerned, Random Forest is a good solution for both regression and classification models although there are models whose performance is relatively similar to that of Random Forest.

It makes sense to use the best parameters in Machine Learning models, as this maximizes their predictive performance. Parameters determine how the model is built and how it interprets the data. By adjusting these parameters correctly, we can improve model efficiency, reduce errors and obtain more accurate predictions. A careful search for the best parameters is therefore essential to exploit the full potential of ML models and achieve optimal results.

It is undeniable that imputation methods play an essential role in preparing data for Machine Learning models. However, it is important to bear in mind that no imputation method is universally perfect. In a context where missing data are frequent, it is vital to look at the source of missing values in order to deal with them in the best possible way.
Understanding the origin of missing data enables you to make informed decisions about the most appropriate imputation method. In some cases, simple methods such as median imputation may suffice. However, when missing data are more complex and present specific patterns, it may make sense to opt for more advanced approaches, such as regression imputation, multiple imputation or the use of methods based on specific models.
Bearing in mind that each dataset is unique, the combination of a thorough understanding of the context of the problem and the judicious use of imputation methods can greatly improve the quality of the results of our Machine Learning models.
In short, in-depth study of imputation methods and attention to the source of missing values is an indispensable lever for maximizing the reliability and relevance of our Machine Learning models. This responsible and rigorous approach will boost confidence in our results, and enable us to take on new challenges with confidence in the exciting field of Machine Learning.

### Key points to remember:
1) There is no significant difference between the performance of the different imputation methods. We can therefore conclude that it is important to have information on the reason for the missing data in order to choose the best imputation method. This information should not be neglected.
2) Generally speaking, regression and multiple imputation methods are preferable when the quantity of data is high, and conversely, when it's low, it's better to Drop or impute by the median.
3) The best imputation methods are not necessarily the same for linear regression and classification.
4) Random Forests are very good and robust models for both classification and regression.
5) Clearly, there is a positive relationship between data quantity and model performance, and a negative relationship between the percentage of missing data and model performance.


