---
layout: post
title:  "Useful feature engineering for more than one purpose"
date:   2018-06-26
categories: [Feature engineering, Machine learning]
---

When you work as a **risk analyst** in a financial company or mobile payment provider, 

you will perform various tasks such as **fraud risk analysis** with the historical transaction(activity) of customers 

as well as generating fraud detection models. 

It sounds very simillar. However it is different from each other in every way because "Fraud risk analysis" is to calculate the risk score 

through various features based on the user IDs from a specific period of data.

As for FDS, it requires streaming(real-time) analysis for fast detection, so normally we use 24 hours activities of users to extract the aggreagte features. 

Why do we need Fraud risk analysis? Although there may be various purposes, In my case, I use it for "Whitelist" purposes to reduce the false positive of FDS. 

So today, I will focus on what features we can have from payment activities of users. 

# Sample data(Table)

Let's assume that we have fllowing payment history logs of three months.

|   <center>Idx</center>   |   <center>Timestamp</center>   |  <center>Id</center>  |   <center>Stat</center>  |  <center>Amount($)</center>  |    <center>...</center>   |   <center>Fraud</center>  |
|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
|   100  |  <center> 2018-01-02 01:03:01 </center>   |  <center> id1 </center>  |   <center> payment </center>   |  <center> 300 </center>   |  <center> ... </center>   |  <center> Y </center>   |
|   101  |  <center> 2018-01-02 01:11:12 </center>   |  <center> id2 </center>   |  <center> cancel </center>    |  <center> 25 </center>   |   <center> ...  </center> |   <center> N </center>   |
|   102    |  <center> 2018-01-02 02:19:45 </center>  |   <center> id1 </center>  |  <center> payment </center>   |   <center> 100 </center>  |   <center> ... </center>   |  <center> Y </center>  |
|    103    |   <center> 2018-01-02 02:33:11 </center>  |   <center> id3 </center>  |   <center> payment </center>   |  <center> 260 </center>   |  <center> ... </center>   |  <center> N </center>   |

Suppose you have data with the above attributes so that you can understand this topic without data.

I think there are two ways to extract features from the raw data.

1. Using domain knowledge to define a hypothesis, extract features, and then verify.

2. Comparing the abuser's data with the normal user's data and create a feature.

Since I can't share the original data with you so let's use number 1. 


# Feature engineering - 1
Mean()+Std() 

# Feature engineering - 2

# How we can solve this problem?

# Summary
