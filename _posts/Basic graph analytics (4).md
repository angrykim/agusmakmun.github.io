---
layout: post
title:  "Basic graph analytics (4)"
categories: [Network graph analysis]
---

## Network and Community unit 

I posted several topics about **basic graph analytics [(1)](https://angrykim.github.io/network%20graph%20analysis/2018/05/29/Network_graph_analysis_for_fraud_events_1.html), [(2)](https://angrykim.github.io/network%20graph%20analysis/2018/05/30/Network_graph_analysis_for_fraud_events_2.html), [(3)](https://angrykim.github.io/network%20graph%20analysis/2018/06/07/Network_graph_analysis_for_fraud_events_3.html)** before. 

However, Graph analysis technique is very useful when the entire network is categorized into community units in a data set.

If you do not understand it well, check out the following example.

<center><img src="/static/img/total_network.png" width="85%"></center>

As you can see in the picture, The one network in `the red circle` in the above picture is directly connected to a number of small networks.

Should we look at these huge networks as a single network?

Not at all, It is better for us to divid it into a number of network units(communities).

By dividing into community units, we can analyze features of each community and judge wether or not it is fraud.

As a result of analyzing community by applying **Modularity**, Please look at the following code by networkx and community.

~~~python

import numpy as np
import pandas as pd
import networkx as nx
from community import community_louvain

g = nx.from_pandas_edgelist(df, source='Source', target='Target', edge_attr= 'Weight') 
partition = community_louvain.best_partition(g, resolution=2.0)
mod = community_louvain.modularity(partition, g)
print("modularity:", mod)

# modularity: 0.9107331781739977

~~~

Here is the result of communities in the entire network. 

Modularity is defined as the fraction of edges that fall within the given network

## What is Modularity? 

In order to get an insight into the problem of detecting communities in graphs,

1) The paper titled Community detection in graphs by Santo Fortunato at **[link](https://arxiv.org/abs/0906.0612)**

2) The wikipedia page at **[link](https://en.wikipedia.org/wiki/Modularity_(networks))**

3) Modularity and community structure in networks by M.E.J. Newman at **[link](http://www.pnas.org/content/103/23/8577)**

<center><img src="/static/img/communities.png" width="85%"></center>

When modularity is applied, **85** communities can be identified, and the modularity at this time is **0.911**.

- The number of communities :  `85`
- Modularity Point :  `0.911`

Generally, in social graph analaysis, it is judged that the modularity is very well classified if it is over **0.4**. 

On a graph with a large number of abnormal networks, a very high modularity score such like this time **(0.911)** can be obtained.

## Summary

Modularity is widely used as a measure for how good a clustering is. 

You can use it to cluster a given network to a number of communities. 




