---
layout: post
title:  "Network analysis for Anti-money laundering (AML) - (1)"
date:   2018-05-29
categories: [Network graph analysis]
---


## 1. [Network graph analysis - 1](https://en.wikipedia.org/wiki/Social_network_analysis)


Before we talked about detection of money laundering using network graphs, Let's take a moment to learn more about network graph analysis as a whole. 

The most commonly used methods for analyzing network graphs are **Path length, (Global or Local)Clustering Coefficient, Efficiency** and so on.

Among them, Local Cluster Coefficient(LCC) refers to the **connection** between participants, which means it is defined as the number of connections a participant has, divided by the total possible connections a participant could have. 

+ **Sample data**

![screenshot_0](/static/img/sample_data.jpg)

**The total possible connections of each node** can be computed by 

![screenshot_1](/static/img/latex_1.jpg)

so, **Local Clustering Coefficent(LCC) of each node** can be computed by 

![screenshot_2](/static/img/latex_2.jpg)

In order to calculate **Global Clustering Coefficient(GCC)** in the network graph, We can compute average LCC of all nodes

There are acutally 2 ways to compute GCC.

The one is to compute **"Average of LCC"** over all nodes in the graph, and the ohter one is **"Transitivity"** 

![screenshot_3](/static/img/latex_3.jpg)

1) **Approach 1** : Average LCC over all nodes in the graph using networkx in python 

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


2) **Approach 2** : Transitivity (Percentage of "open triads" that are triangles in the network)

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


