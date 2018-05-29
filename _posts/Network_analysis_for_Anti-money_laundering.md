---
layout: post
title:  "Network analysis for Anti-money laundering (AML) - (1)"
date:   2018-05-29
categories: [Network graph analysis]
---

## 1. [Network graph analysis](https://en.wikipedia.org/wiki/Social_network_analysis)

Before we talked about detection of money laundering using network graphs, 

Let's take a moment to learn more about network graph analysis as a whole. 

The most commonly used methods for analyzing network graphs are **Path length, (Global or Local)Clustering Coefficient, Efficiency** and so on.

Among them, Local Cluster Coefficient(LCC) refers to the **connection** between participants, which means it is defined as the number of connections a participant has, divided by the total possible connections a participant could have. 

+ **Sample data**

![screenshot_0](/static/img/sample_data.jpg)

**The total possible connections** can be computed by 

![screenshot_1](/static/img/latex_1.jpg)

so, **Local Clustering Coefficent(LCC)** can be computed by 

![screenshot_2](/static/img/latex_2.jpg)

With LCC of all nodes in the graph, We can measure **Global Clustering Coefficient(GCC)** by calculating average LCC

How to measure clustering on the whole network? 

+ **Approach 1** : Average LCC over all nodes in the graph using networkx in python 

~~~python
%matplotlib notebook
import networkx as nx
import numpy as np
import pandas as pd

G = nx.Graph()

G.add_edges_from([(0, 1),
                  (0, 2),
                  (0, 3),
                  (0, 4),
                  (2, 3)])

nx.average_clustering(G) #return : 0.4333333...4
~~~

+ **Approach 2** : Transitivity - Percentage of "open triads" that are triangles in the network

![screenshot_3](/static/img/latex_3.jpg)

So let's talk about how we can compute 'Transitivity' of the network using networkx in python.

~~~python
%matplotlib notebook
import networkx as nx
import numpy as np
import pandas as pd

G = nx.Graph()

G.add_edges_from([(0, 1),
                  (0, 2),
                  (0, 3),
                  (0, 4),
                  (2, 3)])

nx.transitivity(G) #return : 0.375
~~~
