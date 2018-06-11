---
layout: post
title:  "How to evaluate imbanaced classfication model"
date:   2018-06-11
categories: [Machine learning]
---

If you have spent some time in applying machine learning, you would have definitely come across imbalanced binary classfication problem
(class imabalance). 

# What is class imbalance?

> It is the problem in machine learning where the total number of a class of data (positive) is far less than the total number of another class of data (negative). This problem is extremely common in practice and can be observed in various disciplines including fraud detection, anomaly detection, medical diagnosis, oil spillage detection, facial recognition, etc.

The conventional model evaluation methods do not accurately measure model performance when faced with imbalanced class.

Let's take a look at the sample confusion matrix of fraud events. 

![screenshot_1](/static/img/confusion_matrix.jpg)

Normally, When evaluating a binary classfication model, we use `PRECISION`, `RECALL`, and `ACCURACY`.

![screenshot_2](/static/img/model_evaluation.jpg)

Using the exmaple of confusion matrix above, the `PRECISION`, `RECALL`, and `ACCURACY` are all over 99%.

Have you noticed? 

Even if the model can not detect a single fraud event, the conventional model evaluation method shows a detection rate of 99% or more.

In other words, Existing conventional model evaluation methods do not fit the imbalanced class but it fits to a balanced measure.

# How we can solve this problem?

There are the number of ways to deal with this problem. but i normally use [Matthews Correlation Coefficient(MCC)](https://en.wikipedia.org/wiki/Matthews_correlation_coefficient). 

![screenshot_3](/static/img/MCC.jpeg)

> The MCC is in essence a correlation coefficient between the observed and predicted binary classifications; it returns a value between −1 and +1. A coefficient of +1 represents a perfect prediction, 0 no better than random prediction and −1 indicates total disagreement between prediction and observation.

Let's check the MCC result with the example above. 

![screenshot_4](/static/img/MCC_score.jpg)

Normally, when i use the MCC, I want 0.7 or more! (That is the minimum score when i apply binary classfication model to fight fraud and abuse events). 

# Summary

The Class Imbalance Problem is a common problem affecting machine learning due to having disproportionate number of class instances in practice. To check the performance of the model we generated, we will use alternative measure(`MCC`) instead of general methods such as `PRECISION`, `RECALL`, and `ACCURACY`.
