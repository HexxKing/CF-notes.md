# [How to Run Linear Regression in Python](https://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/)
- you can do linear regression using numpy, scipy, stats model and sckit learn
- Scikit-learn is a powerful Python module for machine learning that contains function for regression, classification, clustering, model selection and dimensionality reduction. 
- the sklearn.linear_model module contains “methods intended for regression in which the target value is expected to be a linear combination of the input variables”

### Import the required Python libraries
- `import numpy as np`
- `import pandas as pd`
- `import scipy.stats as stats`
- `import matplotlib.pyplot as plt`
- `import sklearn` - this is a data set. not sure I'll need it everytime I run linear regression yet.

### SciKit Learn
- `y` = target data
- `x` = independent variables
- `from sklearn.linear_model import LinearRegression`
- ` lm = LinearRegression()`
- If you want to look inside the linear regression object, you can do so by typing LinearRegression. and the press <tab> key. This will give a list of functions available inside linear regression object.
- lm.fit() -> fits a linear model
- lm.predict() -> Predict Y using the linear model with estimated coefficients
- lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.
- You can also explore the functions inside lm object by pressing lm.<tab>
- .coef_ gives the coefficients and .intercept_ gives the estimated intercepts.
- Two other parameters that you can pass to linear regression object are fit_intercept and normalize.

### Predicting 
- `lm.predict`
- `np.mean` to calculate the mean squared error 
- a single feature is not a good predictor 

### Training and Validation Data Sets 
- In practice you wont implement linear regression on the entire data set, you will have to split the data sets into training and test data sets. So that you train your model on training data and see how well it performed on test data.
- You can create training and test data sets manually, but this is not the right way to do, because you may be training your model on less expensive houses and testing on expensive houses.
- You have to divide your data sets randomly. Scikit learn provides a function called `train_test_split` to do this.

### Residual Plots
- Residual plots are a good way to visualize the errors in your data. 
- If you have done a good job then your data should be randomly scattered around line zero. 
- If you see structure in your data, that means your model is not capturing some thing. 
  - Maye be there is a interaction between 2 variables that you are not considering, or may be you are measuring time dependent data. 
    - you should go back to your model and check whether you are doing a good job with your parameters.