---
layout: post
title:  "Basic graph analytics (5)"
date:   2018-08-19
categories: [Network graph analysis]
---

## K-means clustering for figuring out a shape of community 

When analyzing a graph, It is required to divide the network into community units as i explained in the previous post [here](https://angrykim.github.io/network%20graph%20analysis/2018/07/06/Basic-graph-analytics-(4).html)

When figuring out a marketing fruad case in a specific period, 

One of my favorite ways to analyze network graphs is to conduct analysis on a community basis.

For instance, we normally analyze the data by user ID or log event. 

As for community based analysis, It is based on community classes, not the user IDs or event IDs.

As you can see the following graph, It is an example network graph for a week data set. 

<center><img src="/static/img/community_basis_network_1.png" width="85%"></center>

The left picture is the network graph and the right is the same one with Modularity applied. 


   - `The number of communities: 1,499` 

   - `Modularity: 0.991`


Once we compute the modularity, What's next is to find out the nodes with events of some nature constitute the community.

I check the event history of the nodes that make up the community.

#### - Checkpoint

1. Determine what kinds of event(pay, deposit, transfer, and etc) history we can find in the community like

   - `Transfer ratio` - The rate at which Transfer event occurred for each community.
  
   - `Withdraw ratio` - The rate at which Withdraw event occurred for each community.
  
   - `Deposit ratio` - The rate at which Deposit event occurred for each community.
   
   - `Payment ratio` - The rate at which Payment event occurred for each community.
   
   
2. Whether or not the nodes has same event sequence


3. Check the User ID's level, such as heavy, mid, light.


I'm sure that you will be able to detect not only the community that carried out **"marketing fraud"**, but also set rules to enable automatic detection.**

