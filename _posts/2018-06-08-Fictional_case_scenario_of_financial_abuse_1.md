---
layout: post
title:  "Fictional case scenario of financial abuse (1)"
date:   2018-06-08 
categories: [scenario, network graph analysis]
---


Let's check the first fictional scenario of financial abuse case.

### ----------------------------------------------------

# Scenario - 1 

We are a company called **"P-wallet"** that provides mobile payment service(It provides `payment, money transfer, deposit, and withdraw by bank account`).

Recently, the marketing team has confirmed that many users have entered our service through various events.

However, we have confirmed that the actual AU ratio is not significantly different from the previous one.

Details of the event are as follows.

*1. During the event period, new subscribers charge $10 or more for getting an additional $5 to a P-wallet account.*

*2. Charge $5, regardless of the payment amount, when using the first payment service among new users (only the condition 1 is satisfied).*

### ----------------------------------------------------

You should be able to quickly determine that you only need to check the patterns of users registered during the event period. 

But let's keep in mind that this scenario is for new users and there is no historical transaction data because they are new users.

From my point of view, There are two approach to find abuser groups. 

**1. Draw network graph.**

Drawing a network graph for `Money transfer event` will teach you if there is any suspicous `Network node` that can integrate small amount money from the number of account to the one that can withdraw it.  

Let's see the graph that i made up for you to better understand. 
    
![screenshot_1](/static/img/sample_abuser.jpg)

As you can see, the pattern is quiet straightforward. 

  - ***The thickness of the edge, is the amount of money transferred.***

  - ***The size of a node is related to the number of times money is received from another node.***
    
A similar amount is being transferred from a few dozen user accounts to a brown account, and a brown account is a pattern that transfers all of the collected money to the final destination.

Here we can see the brown account linked to multiple accounts as `BROKER` and the final destination account as `BANKER`.   

In fact, in the case of cashback events, there is a strong tendency to use money transfer function to collect the money divided into several accounts. 

And this pattern is very likely to be money laundering depending on the amount of money and the size of the network.

One last thing, Finding patterns in a negative network and building an automated negative graph detection system is a completely different matter.

I'll be able to mention this again later.

**2. Event pattern recongnition.**

You can find a pattern for users who get `the cheapest goods` or `cashable items` and if the same goods were purchased by many different users(at the similar time). 

We are able to reasonably suspect the users as abusers 

In fact, when combined with the network graph, It is stronger than any other methods. 
