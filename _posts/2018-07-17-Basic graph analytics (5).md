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

1. Apply Modularity

<img src="/static/img/community_unit_new.png" width="65%">


2. Measure the shape of community by 
    
    - `Betweenness centrality` - Mean and standard deviation of the Betweenness of each node.
  
    - `Global Clustering Coefficient` - Density of connections in each community.
  
    - `Average of Path` - Average shortest path length.
  
    - `Diameter` - Maximum distance between any pair of nodes.


3. Apply k-means clustering 

As above, K-means is applied to 4-dimensional data and in order to find appropriate K value, I use [Elbow mehtod](https://en.wikipedia.org/wiki/Elbow_method_(clustering))

The idea behind elbow method is to run k-means clustering on a given dataset for a range of values of k, and for each value of k, calculate Sum of Squared Errors (SSE).


