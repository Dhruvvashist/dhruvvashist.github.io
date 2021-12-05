---
title:  "Random Forest"
layout: post
mathjax: true

---

## Introduction
---
When learning decision trees, one of the main drawbacks was that decision trees had very high variance and was not flexible. So to reduce the variance, we use a bagging technique called Random forest. Random forest especially uses decision trees as the base models for learning.

## Random Forest
---
A bagging technique where we make a 'forest' of decision 'trees'. 

First step is bootstraping. We split data into $m$ data sets through sampling with replacement. For each $m$data set, we create a decision tree. Now we do a simple modification i.e we split on $$ k dimensions rather than splitting on all the $d$ dimensions for a node. We do this for every node in the tree. The hyperparameter $k$ has the best value of $k= /sqrt[2]{d}$. 
But how do we evaluate our forest? Out-of-the-bag(OOB) error is what makes bagging techniques so useful. Earlier when doing the model selection, we used training and validation set for estimating how good our model is. Here we will use our training set for estimating the error. We used a part of the training set for each model in our RF. We always have out-of-the-bag samples. We use these samples to get the testing error.

For each data point in the training set, we calculate the loss on the model which doesn't use that point. This data point acts as a sample in the validation set but it actually a part of the training set. 
For each data point, I go through each classifier with doesn't have that sample in the training set and calculate the loss. this is done for all samples in the training set.

## Conclusion
---
* Ensemble learning is combining models to make better and stronger models. Bagging and boosting are 2 techniques used.
* Bagging takes several independent base models and trains them in parallel. It then aggregates the models to give a learner which has low bias as well as low variance. Bagging is used for model with high variance.
* Boosting takes several base models and trains them iteratively. The model improves on the weakness of the previous model. These iteration create models that have low             variance as well as low bias. Boosting is used for model with high bias.

The RF only has two hyper-parameters, m and k. It is extremely insensitive to both of these. A good choice for k is $k=/sqrt[2]{d}$ (where d denotes the number of features). You can set m as large as you can afford.
Decision trees do not require a lot of preprocessing. For example, the features can be of different scale, magnitude, or slope. This can be highly advantageous in scenarios with heterogeneous data, for example the medical settings where features could be things like blood pressure, age, gender, ..., each of which is recorded in completely different units
