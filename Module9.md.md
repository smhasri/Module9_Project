Calculate Vehicle MPG (Module 9 : Developing Data Product)
========================================================
author: S.M.HASRI
date: Jan 30, 2015

Introduction
========================================================
The shiny app under development allows a user to enter some basic information about their vehicle, and obtain a prediction for its MPG.  The app relies on a simple GLM algorithm and a data set "auto MPG" from the UCI Machine Learning Repository located [here](http://bit.ly/1sgiKaS). 

The Algorithm
========================================================


```r
library(RCurl)
library(caret)
mpg <- getURL("http://robertkevinackerman.com/wp-content/uploads/2014/08/mpg.csv")
mpg <- read.csv(text = mpg)
modFit <- train(mpg ~ cyl + disp + horse + weight + accel + year + origin, method="glm", data=mpg)
```

*Credit to robertkevinackerman for hosting the dataset

Algorithm Predictions
========================================================

The simple GLM model has a $RMSE$ of 3.35, and an $R^2$ of 0.818.  While other more complex algorithms were implemented, they yielded small improvements at the cost of much longer execution times so the GLM model was chosen as the backbone of the shiny app.

Shiny App
========================================================
It was tested and worked for various combinations of numeric inputs. It is available [here](https://smhasri.shinyapps.io/Module9_Project/).



