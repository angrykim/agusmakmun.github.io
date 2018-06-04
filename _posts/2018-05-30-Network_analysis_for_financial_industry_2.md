---
layout: post
title:  "Network analysis for financial industry - (2)"
date:   2018-05-30
categories: [Network graph analysis]
---

# [Network graph analysis - 2](https://en.wikipedia.org/wiki/Social_network_analysis)

The previous post did not mention **Directed network**. 

However, in general, when you detect fraud or abuse events in finance, 

It is a common method to use for direct network graph.  
(It is very useful for understanding **the flow of money** and others)

So today, I want to talk about how to measure the importance of the centrality of a node in a directed netowrk. 

Acutally, I'm goiing to talk about `Page Rank algorithm`. 

It was developed by the Google founders when they were thinking about how to measure the importance of webpages using the hyperlink network structure of the web.

But not just only web page, but also any type of network can use **Page Rank** to compute central(important) nodes 

Let's check the basic concept of `Page Rank algorithm`. 

![screenshot_1](/static/img/page_rank.jpg)

So the above equiation shows how to compute PageRank of a node 

![screenshot_2](/static/img/page_rank_2.jpg)

3 important concepts of PageRank (To become an important node...)

*  `There are many other nodes that tell me I'm important.` --> _The number of PR(Ti)_
*  `It is better if the node referred to me as an important node is an important node in a network` --> _Hight PR(Ti)_
*  `It would be good if the node that referred to me as an important node is only connected to an important node in a network` --> _Low C(Ti)_

## Page Rank algorithm:

*  `Assign all nodes a PageRank of 1/n`.
*  `Each node gives an equal share of its current PageRank to all the nodes it links to`. 

+ **Sample data**

~~~python
import networkx as nx
import numpy as np
import pandas as pd
%matplotlib notebook

options = {
    'node_color': 'red',
    'node_size': 1000,
    'width': 1,
}

# Instantiate the graph
G = nx.DiGraph(directed=True)
# add node/edge pairs
G.add_nodes_from([0,1,2,3,4,5])
G.add_edges_from([(0, 1),
                  (1, 2),
                  (1, 3),
                  (2, 1),
                  (3, 0), 
                  (3, 2),
                  (3, 2),
                  (4, 0),
                  (5, 4)])

# draw the network G
nx.draw_networkx(G, arrows=True, **options)
~~~

![screenshot_3](/static/img/Digraph.jpg)

Let's compute this sample data set(K=2). 

|  <center>K large</center> |  <center>Node 0</center> |  <center>Node 1</center> |  <center>Node 2</center> |  <center>Node 3</center> |<center>Node 4</center> | <center>Node 5</center> |
|:--------|:--------:|--------:|:--------|:--------:|--------:|--------:|
|**init** | <center> 1/5 </center> | <center> 1/5 </center> |<center> 1/5 </center> | <center> 1/5 </center>  | <center> 1/5 </center> |<center> 1/5 </center> |
|**K=1** | <center> 4/15 </center> | <center> 2/5 </center> |<center> 1/6 </center> | <center> 11/10 </center>  | <center> 4/15 </center> |<center> 1/5 </center> |

Node 0:  (1/3)X(1/5)+1/5 = 4/15 

Node 1:  (1/5)+(1/5) = 2/5 

Node 2:  (1/3)X(1/5)+(1/2)X(1/5) = 1/6

Node 3:  (1/2)X(1/5) = 1/10

Node 4:  (1/3)X(1/5)+1/5 = 4/15

Node 5:   1/5


| <center>K large</center> |  <center>Node 0</center> |  <center>Node 1</center> |  <center>Node 2</center> |  <center>Node 3</center> |<center>Node 4</center> |  <center>Node 5</center> |
|:--------|:--------:|--------:|:--------|:--------:|--------:|--------:|
|**init** | <center> 1/5 </center> | <center> 1/5 </center> |<center> 1/5 </center> | <center> 1/5 </center>  | <center> 1/5 </center> |<center> 1/5 </center> |
|**K=1** | <center> 1/5 </center> | <center> 1/20 </center> |<center> 1/20 </center> | <center> 1/20 </center>  | <center> 1/20 </center> |<center> 1/5 </center> |
|**K=2** | <center> 1/10  </center> | <center> 13/30   </center> |<center> 7/30  </center> | <center> 1/5  </center>  | <center> 7/30  </center> |<center> 1/5 </center> |

Node 0:  (1/3)X(1/10)+1/5 = 1/10 

Node 1:  (1/6)+(4/15) = 13/30 

Node 2:  (1/3)X(1/10)+(1/2)X(2/5)= 7/30

Node 3:  (1/2)X(2/5) = 2/10 = 1/5

Node 4:  (1/3)X(1/10)+1/5= 7/30

Node 5:   1/5

No matter how large the value of K is, the PageRank value of the Node has a unique value in the network.

So far, We are studying PageRank and the Next post is about HITS algorithm


