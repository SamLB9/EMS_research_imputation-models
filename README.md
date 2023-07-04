# EasyMedStat imputation methods and models research
The aim of this project is to compare and study different imputation methods and different regression and classification models for different starting sample sizes and missing data percentages.
To do this, we chose to conduct our research using healthcare datasets.

This first dataset contains 5735 observations.
We will analyze the different models and imputation methods using 3 different sample sizes: 150, 500 and 1000 observations.
For each sample, we imputed a certain percentage of missing data (10%, 20%, 25%, 30%, 40%, 50%) and then completed the missing values using different imputation methods (Drop, Median, Regression or Multiple).
We then split the dataset into a train part and a test part (80%-20%).
Finally, we were able to train and test several models.

We recovered the best models and then tested them with a random sample of 150 observations from the initial dataset.


![](https://github.com/SamLB9/EMS_research_imputation-models/blob/6498bba2394adb60f1ae1d19b05fbca9ade664a4/Diagram_drawio.png)

