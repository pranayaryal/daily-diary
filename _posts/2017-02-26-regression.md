---
layout: post
title:  "Predicting Housing Price (Boston Housing Dataset)"
image: histPrice.png
---
An attempt at using different regression algorithms to predict the price of houses in Boston using the Boston dataset from scikit learn library.

The code can be found <a href="https://www.github.com/pranayaryal/decisionTree" target="_blank">here</a>

This dataset is from scikit-learn library of python. We wil use various techniques for linear regression. We will use the Ridge Regression
and Lasso and compare them

1. CRIM:     per capita crime rate by town       
2. ZN:       proportion of residential land zoned for lots over 25,000 sq.ft.
3. INDUS:    proportion of non-retail business acres per town
4. CHAS:     Charles River dummy variable (= 1 if tract bounds river; 0 otherwise)
5. NOX:      nitric oxides concentration (parts per 10 million)
6. RM:       average number of rooms per dwelling        
7. AGE:      proportion of owner-occupied units built prior to 1940
8. DIS:      weighted distances to five Boston employment centres\n        
9. RAD:      index of accessibility to radial highways        
10. TAX:     full-value property-tax rate per $10,000        
11. PTRATIO: pupil-teacher ratio by town        
12. B:       1000(Bk - 0.63)^2 where Bk is the proportion of blacks by town        
13. LSTAT:   percentage of lower status of the population        

The target variable is the price of the house.

Let us create a function for performance metric which takes the labels and the predictions as the arguments and returns the mean squared error using the metrics library from sklearn
```
def performance_metric(label, predictions):
  return metrics.mean_squared_error(label, prediction)
```




