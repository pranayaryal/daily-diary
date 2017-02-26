---
layout: post
title:  "Predicting Housing Price (Boston Housing Dataset)"
image: histPrice.png
---

This dataset is from scikit-learn library of python. I have used Decision Tree Regressor to decide on the home price. The various features in the dataset used to predict price are:


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
18. LSTAT:   percentage of lower status of the population        

The target variable is the price of the house.

We will first split the data into training and test sets. We will train our algorithm on the training set and then test it on the test set.
Let's do some exploratory data analysis. 

Let's look at a histogram of the house price for the training set.

