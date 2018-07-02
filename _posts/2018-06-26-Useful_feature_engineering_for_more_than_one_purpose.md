---
layout: post
title:  "Useful feature engineering for more than one purpose"
date:   2018-06-26
categories: [Feature engineering, Machine learning]
---

When you work as a **risk analyst** in a financial company or mobile payment service provider, 

you will perform various tasks such as **fraud risk analysis** with the historical transaction(activity) of customers 

as well as generating fraud detection models. 

It sounds very simillar. However it is different from each other in every way because "Fraud risk analysis" is to calculate the risk score 

through various features based on the user IDs from a specific period of data.

As for FDS, it requires streaming(real-time) analysis for fast detections, so normally we use 24 hours activities of users to extract the aggreagte features. 

Why do we need Fraud risk analysis? Although there may be various purposes, In my case, I use it for "Whitelist" purposes to reduce the false positive of FDS. 

So today, I will focus on what features we can have from payment activities of users. 

Let's have some example of feature engineering with the fictional payment data set.

![screenshot_1](/static/img/sample_data_image.png)

This screenshot shows us the normal pattern of user in the data set 

![screenshot_2](/static/img/sample_data_image_2.png)

This screenshot shows us the fraudster. 

Let's pretend that all normal users have the same pattern of the first screenshot, whereas the second screenshot is for fraudsters. 

What features you can extract from those screenshots? 

# Feature engineering - 1


# Feature engineering - 2

# How we can solve this problem?

# Summary
