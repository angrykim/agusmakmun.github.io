---
layout: post
title:  "Basic graph analytics (5)"
date:   2018-08-19
categories: [Network graph analysis]
---

## K-means clustering for figuring out a shape of community 

When analyzing a graph, It is required to divide the network into community units as i explained in the previous post [here](https://angrykim.github.io/network%20graph%20analysis/2018/07/06/Basic-graph-analytics-(4).html)

When figuring out a marketing fruad case in a specific period, One of my favorite ways to analyze network graphs is to conduct analysis on a community basis.

For instance, we normally analyze the data by user ID or log event. 

As for community based analysis, It is based on community classes, not the user IDs or event IDs.

As you can see the following graph, It is an example network graph for a week data set. 

<img src="/static/img/network_graph_example.png" width="35%">

And this is the same graph divided into community units. 

<img src="/static/img/community_basis_network.png" width="35%">

So I used these processes to figure out the shape of communities in the entire network. 

### 1. Apply "Modularity"

   - The number of communities : 1,499
    
   - Modularity : 0.991

### 2. Event analysis of communities by 
    
   - `Transfer ratio` 
  
   - `Withdraw ratio` 
  
   - `Deposit ratio`
   
   - `Payment ratio`

