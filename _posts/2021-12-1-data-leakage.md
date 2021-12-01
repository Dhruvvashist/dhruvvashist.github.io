---
title:  "Data Leakage"
layout: post
---

##Introduction

---

Data leakage is one of the most overlooked yet important concepts in Machine Learning. All we want from our model is to score as high as possible on some metric. We although take care of not underfitting/overfitting but things take a turn when deploying the model into production when the model sees a real world data.

Such inconsistency by the model for real world data is explained by data leakage.

##Data Leakage

---

As the name suggests, it the leakage of data from training data to testing data. Test set is used to simulate unseen real world data. But what if training set has already seen the data from the test set? The model will learn that data and the accuracy for the test set will be extremely high as it has already learned the data.

##Causes

---

The main problem is leaking knowledge from the training set to test set. This can be done in various ways -

1.  Target and Feature leakage(Column Leakage)-
    We should be careful which columns/features we want to include for the model. Features that include a duplicate, proxy for the target label ,or the label itself should be excluded. 
    E.g. When predicting "Yearlysalary", "MonthlySalary" will be indirectly giving information about the target label.
    
    Features providing knowledge after the time of prediction should be avoided. Any future knowledge about the future shouldn't be used to predict the past. 
	E.g. Using amount of leather used for predicting the no. of laces made a company. The amount of leather used is usually known after the laces are made for a amount of time. This gives the future knowledge which indirectly gives the information.

    This is why one should always research and study the features about the problem to avoid these situations.
    
2.  Training example leakage(Row leakage)-
        
	1.  Premature Featurization-
		We often do EDA on the dataset before the train-test split. This leads the data to leak  in the test set. When doing Normalstion for the dataset, we unknowingly leak the knowledge from the test set when taking the mean. Similarly, when filling missing values, we tend to leak the data when replacing the mean of the whole dataset fir missing values.
       
	2.  Duplicate rows-
		This usually occurs when the data is less and we try to oversample it for training. If train-test split is not done before duplicating, part of duplicated training data is present in the test set. 
		
	3. Time leakage-
		Imagine having a training set with two data points, 1 and 3. Let’s have the test set with a single data point labeled 2. Let’s assume that the temporal sequence of these points is 1, 2, then 3. There is a likelihood that we have introduced data leakage thanks to how we created our test and training sets. Since point 3 is in the training set, and 2 is in the test set. In this situation, we are unrealistically training our model on future information compared to the position of the test data in time. We inadvertently end up leaking information about the future into the past.
		
	4. Group Leakage-
		This usually happened in medical fields or whenever there is groups of data for a single user.
		e.g. Andrew Ng's group had 100k x-rays of 30k patients, meaning ~3 images per patient. The paper used random splitting instead of ensuring that all images of a patient was in the same split. Hence the model partially memorized the patients instead of learning to recognize pneumonia in chest x-rays.
        
        For this reason, test set should be taken out before doing the EDA on the train set.
        

##Best practices and Solutions

---

The most important practice is to do through research about the problem and the dataset in hand, to reduce Target/Feature leakage. Always make it a habit to first split the data in train-test and then do EDA and feature engineering on the training set.

Use of pipelines and cross-validations is extremely useful when dealing with complex problems and avoiding data leakage. Also one should look out for "too-good-to- be-true" model scores and check data leakage.

##Conclusion

---

Data leakage is one of the most common mistakes and is often not realised untill model is in production and is feed the real world data. It is important to not let test set knowledge leak in the training set. It is in best practice to avoid proxy features, doing splits before EDA and using pipelines and cross-vaidations.




