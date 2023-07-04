# EasyMedStat imputation methods and models research
The aim of this project is to compare and study different imputation methods and different regression and classification models for different starting sample sizes and missing data percentages.
To do this, we chose to conduct our research using healthcare datasets.

This first dataset contains 5735 observations.
First, we had to clean up the data by deleting rows containing missing data and transforming categorical variables into numerical variables using OneHotEncoder's SckLearn function, so that they could be taken into account in the models.
We will analyze the different models and imputation methods using 3 different sample sizes: 150, 500 and 1000 observations.
For each sample, we imputed a certain percentage of missing data (10%, 20%, 25%, 30%, 40%, 50%) and then completed the missing values using different imputation methods (Drop, Median, Regression or Multiple).
We then split the dataset into a train part and a test part (80%-20%).

Finally, we were able to train and test the various models.
We recovered the best models and then tested them with a random sample of 150 observations from the initial dataset.
From the metrics of the various models, we created a csv file for subsequent analysis via graphs and other means.

Here's a diagram to help you clearly understand our process:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/6498bba2394adb60f1ae1d19b05fbca9ade664a4/Diagram_drawio.png)

Here's an overview of the data set we obtained after this process:

![](https://github.com/SamLB9/EMS_research_imputation-models/blob/b55ea070af72228af00d16c99d8010b8c876e685/MetricsData.png)

From here, we were able to analyze the different imputation methods and models in detail.
