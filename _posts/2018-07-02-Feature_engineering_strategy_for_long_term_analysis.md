---
layout: post
title:  "Feature engineering strategy for long term analysis"
date:   2018-07-02
categories: [Feature engineering, Machine learning]
---

When you work as a **Fraud analyst** in a financial company or mobile payment service provider, 

you will perform various tasks such as **Real-time fraud analysis** with the historical transaction of customers 

as well as **long term fraud analysis**.

It sounds very simillar. However it is different from each other in every way because **long term fraud analysis** is to calculate the risk score through various features based on the user IDs from a specific period of data.

As for  **Real-time fraud analysis**, it requires streaming(real-time) analysis for fast detections, so in the case of us, we normally use 24 hours activities of users to extract the aggreagte features. 

# Why do we need long term fraud analysis?

Although there may be various purposes, In my case, I use it for "Whitelist" purposes to reduce the false positive ratio of FDS. 

So today, I will focus on what features we can have from payment activities of users. 

Let's have some example of feature engineering with the fictional payment data set.

![screenshot_1](/static/img/sample_data_image_1.png)

This screenshot shows us the normal pattern of user in the data set 

![screenshot_2](/static/img/sample_data_image_2.png)

This screenshot shows us the fraudster. 

Let's pretend that all normal users have the same pattern of the first screenshot, whereas the second screenshot is for fraudsters. 

What features you can extract from those screenshots? 

As you can see from the bar plot graph, there is a very clear difference between a normal user and a fraudster.

# Feature engineering for payment  
The normal users use the charged amount several times over a certain period of time, while the fraudsters use the charging amount very quickly with only a few payments. (Same as below equations) 


# Feature engineering for deposit
The normal users have long charge cycles, while the fraudsters have very short charge cycles.
In the above bar plot, there are three simple ways to draw the difference between normal and fraud as a feature. 
(You can choose one among them)

![screenshot_3](/static/img/difference_feature.png)


# Feature engineering for Royalty
While the normal users use the payment service steadily, the fraudsters show high activity only for a certain period of time.

![screenshot_4](/static/img/royalty.png)


# Summary
Feature engineering is the basic concept that data analysts must have in analyzing data. In the analysis of binary data, it is necessary to be able to change class differences to codes or formulas.
