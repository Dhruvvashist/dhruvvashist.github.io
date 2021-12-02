---
title:  "Ensemble Learning- Bagging and Boosting"
layout: post
---

## Introduction
---
Most of out time in Machine Learning goes into tackling the problem of overfitting or underfitting. We all want our models to find that sweet trade off between bias and variance. This is where ensemble learning comes to rescue.

## Ensemble Learning
---
Before we dive into different techniques, the first question we need to ask ourselves is -
What is ensemble learning and what is the need.

Ensemble learning is a machine learning paradigm where multiple models (often called weak learners or base models) are trained to solve the same problem and combined to get better performance.

Ensemble learning helps us to solve the problem of overfitting and underfitting. We use an Ensemble(a group of things/people acting or taken together as a whole) to combine different complex/simple models to affectively use them as one. The main principle is that a group of weak models combine together to form strong models, increasing the performance of the final model.

## Bias and variance
---
To find that sweet spot we 2 techniques depending on model we are dealing with. We use Bagging when dealing with high variance and Boosting when dealing with high bias.

## Bagging
---
Also known as Bootstrap aggregation, Bagging is used to deal with overfitting/high variance in the model. It takes a numerous independent models of homogenous/non- homogenous nature and combines them to give a final prediction.

This includes 2 main processes -

1. ### Bootstrap -
This is process of making independent models and giving them random data from the original dataset. This is done by sapling with replacement. Each data point has equal probability/weight to get picked for a given model. The models are the trained on these datasets produced for them and give a prediction of their own.

2. ### Aggregation - 
We now aggregate the prediction given by the independent models into one. This is done by voting. The final prediction given has much less variance and is better than most of the independent models.

But why does bagging decrease variance?

Each model is centered around the true density, but is overly complicated (low bias, high variance). By averaging them out, we get a smoothed version of them (low variance), still centered around the true density (low bias).

## Boosting
---
Boosting unlike bagging takes simple model(High bias) and makes them complex(low bias)  keeping variance low. It takes various simple models/learners and makes them learn sequentially. Early learners are trained and give errors on the dataset provided. Earlier each data point has equal weight/probability to get selected in the first learner. Each misclassification increases the weight of that datapoint  and reduces weight of ones correctly classified so that misclassified data has higher chance of getting selected for the next model.

Iteratively sequence of model are trained the final model is more complex than the one we started on and thus decreases bias. One should be careful not to overfit the model and increase variance in the process.

## Conclusion
---
* Ensemble learning is combining models to make better and stronger models. Bagging and boosting are 2 techniques used.
* Bagging takes several independent models and trains them in parallel. It them aggregates the models to give a learner which has low bias as well as low variance. Bagging is    used for model with high variance.
* Boosting takes several base models and trains them iteratively. The model improves on the weakness of the previous model. These iteration create models that have low             variance    as well as low bias. Boosting is used for model with high bias.



