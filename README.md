# Advanced Regression: Dimension Reduction and Clustering Analysis on Housing data
For this project, we will be applying the dimension reduction and clustering techniques on the dataset containing both numerical as well as categorical features. For this purpose we are using the well known housing dataset on Kaggle.

Source: https://www.kaggle.com/c/house-prices-advanced-regression-techniques/overview

## Dimension Reduction
To perform PCA and MCA, we are using the methods provided by prince library and will tune the same set of parameters for both PCA and MCA. Our dataset has around 1500 observations and we chose only a few parameters as the number of resulting combinations to check were way more than the number of observations in the dataset. Still we ended up with 4000+ combinations. Below mentioned are the parameters that will be tuned:
1. Number of components (n_components): It denotes the number of components used to perform PCA or MCA.
2. Number of iterations (n_iter): The number of iterations used for computing the SVD.

To standardize the numerical data we will be setting the **rescale_with_mean** and **rescale_with_std** parameters to **True**.

As we are tuning parameters for PCA and MCA, we are also going to tune the alpha value for the ridge regression to determine the best alpha value for the specific parameter pair. If we get the lowest validation MSE for the pair, then we can use the best value for alpha that we determined while hyperparameter tuning.

We performed dimensionality reduction on the dataset containing both numerical as well as categorical features and tuned the parameters to perform regression. The below mentioned table shows the validation and test MSE for the Ridge regression using reduced features and original baseline dataset.

MSE |	Ridge Baseline	| Ridge Reduced Features
Validation Data |	896261228.21 | 765992669.03
Test Data	| 716644289.46	| 738752163.81

From the above table we can see that the MSE on the validation data was much lower for Ridge regression model with reduced features as compared to baseline Ridge regression model. However the performance of both the models on the test set is comparable. Lower MSE on the test data is obtained for baseline Ridge regression model as compared to the Ridge regression model having reduced features.

## Cluster Analysis
Response variable 'SalePrice' are binned into 5 bins which contain almost same number of observations. NMI score is very low i.e. 0.24 which clearly indicates that the cluster assignment was only partially correct. Since, the observations got assigned to clusters disproportionately and cluster 3 (620) and cluster 5 (439) got the major chunk of the observations the low NMI score is understandable.

