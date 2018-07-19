---
layout: post
title:  "Basic graph analytics (5)"
date:   2018-07-17
categories: [Network graph analysis]
---

## K-means clustering for figuring out a shape of community 

When analyzing a graph, the shape of the network can be the most dimensionally distinct element of fraud.

In fact, first, we check the shape of the network and then proceed with a detailed analysis of the individual nodes in the network.

Is there any alternative way we only use the minimun human resources to analyze the shape of network graph?

So I used these processes to figure out the shape of communities in the entire network. 

### 1. Apply Modularity

   - The number of communities : 4,118
    
   - Modularity : 0.9982


### 2. Measure the shape of community by 
    
   - `Betweenness centrality` - Mean and standard deviation of the Betweenness of each node.
  
   - `Degree` - Mean and Standard deviation of node degree in each community.
  
   - `Size` - The number of nodes in a community.
   
   - `Radius` - The radius is the minimum eccentricity (Distance)


### 3. Apply k-means clustering 

As above, K-means is applied to 6-dimensional data and in order to find appropriate K value, I use [Elbow mehtod](https://en.wikipedia.org/wiki/Elbow_method_(clustering))

The idea behind elbow method is to run k-means clustering on a given dataset for a range of values of k, and for each value of k, calculate Sum of Squared Errors (SSE).

<img src="/static/img/elbow_method.png" width="35%">

After clustering with K = 5, The following shape of communities found in the entire network graph. 

   - `Gray` - Outcase(88.65%)
  
   - `Red` - Giant Community(3.71%)
  
   - `Green` - Hierarchical Community(3.6%)
   
   - `Blue` - Star shape(2.44%)
   
   - `Light Pink` - Chain shape(1.6%)

<center><img src="/static/img/communities_color.png" width="85%"></center>

