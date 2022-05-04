# Linear Regressions

## How to Run Linear Regression in Python

[Reading](https://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/)

In the reading he targets a variable (housing prices) as the y, and then plots all other variables as the x.
He imports linear_model from sklearn and drops the price category from x.

```
from sklearn.linear_model import LinearRegression
x = bos.drop('PRICE', axis = 1)

lm = LinearRegression()
lm
```
Explore by `LinearRegression.<tab>`
`lm.fit()` Fits a linear model
`lm.predict()` Predict Y using the linear model with estimated coefficients
`lm.score()` Returns the coefficient of determination (R^2). The proportion of total variation of outcomes explained by the model

Explore lm object by `lm.<tab>`
`lm.coef_` gives the coefficients
`lm.intercept_` give the estimated intercepts

From Reading:

In [20]: lm.fit(X, bos.PRICE)

Out[20]: LinearRegression(copy_X=True, fit_intercept=True, normalize=False)



## Introduction to simple Linear Regressions

[Video](https://www.youtube.com/watch?v=KsVBBJRb9TE&ab_channel=jbstatistics)

Regression analysis explores the relationship between a quantitative response variable and one or more explanatory variables.

On a graph x is the explanatory or independant variable.
y is the response or the dependant variable.

Data is in pairs (x1, y1), (x2, y2), etc..

Line: the true mean of y for a given value of x is equal to beta naught (y intercept) + beta 1 (slope) x



[Back](README.md)