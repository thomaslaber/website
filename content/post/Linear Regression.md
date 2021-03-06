---
title: "Linear Regression"
date: 2018-04-02
tags: ["R", "regression"]
draft: false
---


Source <https://www.analyticsvidhya.com/blog/2017/09/common-machine-learning-algorithms/>

It is used to estimate real values (cost of houses, number of calls, total sales etc.) based on continuous variable(s). Here, we establish relationship between independent and dependent variables by fitting a best line. This best fit line is known as regression line and represented by a linear equation 
$$Y= a *X + b$$
The best way to understand linear regression is to relive this experience of childhood. Let us say, you ask a child in fifth grade to arrange people in his class by increasing order of weight, without asking them their weights! What do you think the child will do? He / she would likely look (visually analyze) at the height and build of people and arrange them using a combination of these visible parameters. This is linear regression in real life! The child has actually figured out that height and build would be correlated to the weight by a relationship, which looks like the equation above.

In this equation:

>    Y - Dependent Variable
>    a - Slope
>    X - Independent variable
>    b - Intercept

These coefficients a and b are derived based on minimizing the sum of squared difference of distance between data points and regression line.

Look at the below example. Here we have identified the best fit line having linear equation 
$$y=0.2811x+13.9$$ 
Now using this equation, we can find the weight, knowing the height of a person.

Linear Regression is of mainly two types: Simple Linear Regression and Multiple Linear Regression. Simple Linear Regression is characterized by one independent variable. And, Multiple Linear Regression(as the name suggests) is characterized by multiple (more than 1) independent variables. While finding best fit line, you can fit a polynomial or curvilinear regression. And these are known as polynomial or curvilinear regression.

## R Code

```{r}
#Load Train and Test datasets
#Identify feature and response variable(s) and values must be numeric and numpy arrays
x_train <- input_variables_values_training_datasets
y_train <- target_variables_values_training_datasets
x_test <- input_variables_values_test_datasets
x <- cbind(x_train,y_train)
# Train the model using the training sets and check score
linear <- lm(y_train ~ ., data = x)
summary(linear)
#Predict Output
predicted= predict(linear,x_test) 
```

## R Code applied

Mean squared error:

$$MSE = \displaystyle\frac{1}{n}\sum_{t=1}^{n}res_t^2$$ 

Root mean squared error:

$$RMSE = \displaystyle\sqrt{\frac{1}{n}\sum_{t=1}^{n}res_t^2}$$

Mean absolute error:

$$MAE = \displaystyle\frac{1}{n}\sum_{t=1}^{n}|res_t|$$

Mean absolute percentage error:

$$MAPE = \displaystyle\frac{100\%}{n}\sum_{t=1}^{n}\left |\frac{res_t}{y_t}\right|$$

```{r}
# install.packages("tidyverse")
# trace(utils:::unpackPkgZip, edit=TRUE)
library(titanic)
library(tidyverse)
titanic_train = titanic_train %>%
  mutate_at(.vars =  c("Sex", "Survived", "Pclass", "Embarked"),
            .funs = as.factor)
str(titanic_train)

x_train <- titanic_train
y_train <- titanic_train$Survived
x_test <- titanic_test
x <- cbind(x_train,y_train)

# Train the model using the training sets and check score
linear <- lm(Survived ~ ., data = x_train)
summary(linear)

#Predict Output
predicted = predict(linear,x_test)

rmse <- sqrt(mean(residuals ^ 2))


```

