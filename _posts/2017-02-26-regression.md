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

Let us create a function for **performance metric** which takes the labels and the predictions as the arguments and returns the mean squared error using the metrics library from sklearn

```
def performance_metric(label, predictions):
  return metrics.mean_squared_error(label, prediction)
```

This code in numpy will generate incremental subset sizes for the length of the training set. This is to calculate the error based on training-set size.
```
sizes = np.round(np.linspace(1, len(X_train), 50))
```

Let us create another function to plot the learning curve for different tree depths and training and testing sizes.
```
def learning_curve(depth, X_train, y_train, X_test, y_test):
    """Calculate the performance of the model after a set of training data."""

    # We will vary the training set size so that we have 50 different sizes
    sizes = np.round(np.linspace(1, len(X_train), 50))
    train_err = np.zeros(len(sizes))
    test_err = np.zeros(len(sizes))

    print "Decision Tree with Max Depth: "
    print depth

    for i, s in enumerate(sizes):

        # Create and fit the decision tree regressor model
        regressor = DecisionTreeRegressor(max_depth=depth)
        regressor.fit(X_train[:s], y_train[:s])

        # Find the performance on the training and testing set
        train_err[i] = performance_metric(y_train[:s], regressor.predict(X_train[:s]))
        test_err[i] = performance_metric(y_test, regressor.predict(X_test))


    # Plot learning curve graph
    learning_curve_graph(sizes, train_err, test_err)
```




