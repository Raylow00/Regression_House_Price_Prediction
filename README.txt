Regression
1. Never use the test set until after you have trained your model - any EDA is 
to be done on the TRAIN SET ONLY.
	- If given only one dataset, split it in the beginning to a train, validation and test set. The validation set is used for evaluation or model tweaking.
2. Transformations done on the train set should be done also on the test set.
3. Impute numerical features with median when the data is not skewed.
4. The metrics for regression are usually RMSE, MSE, MAE, and R2 score.
5. Perform feature scaling when the features have different scales, since regression usually depends on distance-based algorithms.
6. When detecting outliers, we can make use of a pipeline - *make_pipeline()* from *sklearn*.
7. To streamline the process better, we can add *StandardScaler()/RobustScaler()* into the pipeline.

--------------------------------------------------------------------------------------------------------------------------

1. In cases where there are too many features to handle, looking at the correlation(abs) helps to remove unnecessary features. Convert categorical features to numerical with one-hot encoding/label encoding to see their correlation.
2. Not all features of integer data types are numerical features, some could be ordinal features - beware of these features when performing any scaling or transformations.
3. Perform as few transformations to the features as possible.
4. When there are missing values, we usually impute with mean/median/mode depending on the data type of the features. However, if the percentage of missing data is high, imputing may not be a good solution. First, check if the feature is useful(check correlation). Second, check if it is possible to remove the data points altogether instead of imputing them. Take note of "numerical" features like YearBuilt - imputing with median/mean does not sound logical.
5. After throwing away some unnecessary features, check for multicollinearity. Perform feature engineering to select one from the multicorrelated features.
6. We can check for skewness/distribution of features at a much later stage, especially after checking for outliers. If outliers are still present when performing log transformation, the resultant distribution still consists of outliers. Beware of performing log transformation on all "skewed" features. Some do not make sense, like ordinal features. 
7. Skewness threshold
	- between -1 and 1 - highly skewed
	- between -1 and -0.5 or between 1 and 0.5 - moderately skewed
	- between -0.5 and 0.5 - considerably symmetric
8. Plotting the residual graph can help us understand the model better - if it is performing as expected.