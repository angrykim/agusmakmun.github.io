---
layout: post
title:  "Fictional case scenario of financial abuse (1)"
date:   2018-06-08 
categories: [scenario, network graph analysis]
---


Let's check the first fictional scenario of financial abuse case.

## Scenario - 1 

> _We are a company called **"P-wallet"** that provides mobile payment service_
>
> _(It provides payment, money transfer, deposit, and withdraw by bank account)._
>
> _Recently, the marketing team has confirmed that many users have entered our service through various events._
>
> _However, we have confirmed that the actual AU ratio is not significantly different from the previous one._
>
> _Details of the event are as follows._
>
> _1. During the event period, new subscribers charge $10 or more for getting an additional $5 to a P-wallet account._
>
> _2. Charge $5, regardless of the payment amount, when using the first payment service among new users (only the condition 1 is satisfied)._

You should be able to determine that you only need to check the patterns of users registered during the event period. 

From my point of view, There are __two approaches__ to find abuser groups. 

### 1. Draw network graph.

Drawing a network graph for `Money transfer event` will teach you if there is any suspicous `Network node` that can integrate small amount money from the number of account to the one that can withdraw it.  

Let's see the graph that i made up for you to better understand. 
    
![screenshot_1](/static/img/sample_abuser.jpg)

As you can see, the pattern is quiet straightforward. 

  - ***The thickness of the edge, is the amount of money transferred.***

  - ***The size of a node is related to the number of times money is received from another node.***
    
A similar amount is being transferred from a few dozen user accounts to a brown account, and a brown account is a pattern that transfers all of the collected money to the final destination.

Here we can see the brown account linked to multiple accounts as `BROKER` and the final destination account as `BANKER`.   

In fact, in the case of cashback events, there is a strong tendency to use **money transfer** to collect the money splitted into several accounts. 

Be aware of that **this pattern is also very likely to be money laundering depending on the amount of money and the size of the network.**

One last thing, Drawing network graphs and building an automated detection model is a completely different matter.

I'll talk about it later in another post. 

### 2. Event pattern recongnition.

You can find a pattern for users who get `the cheapest goods` or `cashable items` and if the same goods were purchased by many different users(at the very similar time). 

We are able to reasonably suspect the users as abusers 

In fact, when combined with the network graph, It is stronger than any other methods to find organized crimes(abusing). 
