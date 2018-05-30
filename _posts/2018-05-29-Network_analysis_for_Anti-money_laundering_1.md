---
layout: post
title:  "Network analysis for Anti-money laundering (AML) - (1)"
date:   2018-05-29
categories: [Network graph analysis]
---


+ # [Network graph analysis - 1](https://en.wikipedia.org/wiki/Social_network_analysis)


Before we talked about detection of money laundering using network graphs, Let's take a moment to learn more about network graph analysis as a whole. 

The most commonly used methods for analyzing network graphs are **Path length, Global Clustering Coefficient, and Local Clustering Coefficient.**

Let's take a look at the basic concepts one by one.

First, **Local Clustering Coefficient(LCC)** refers to the **connection** between nodes, which means it is defined as the number of connections a node has, divided by the total possible connections a node could have. 

+ **Sample data**

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

nx.draw_networkx(G)
~~~

![screenshot_0](/static/img/sample_data.jpg)

**Total possible connections of each node** can be computed by 

![screenshot_1](/static/img/latex_1.jpg)

**Local Clustering Coefficent(LCC) of each node** can be computed by 

![screenshot_2](/static/img/latex_2.jpg)

The reason for obtaining Local Clustering Coefficent (LCC) is to compute **Global Clustering Coefficient(GCC)**.


There are several ways to compute Global Clustering Coefficient(GCC).

The one is to compute **"Average of LCC"** over all nodes in the graph, and this can be easily done with networkx.

+ **Approach 1** : Average LCC over all nodes in the graph using networkx in python.

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

The ohter one is to calculate [Transitivity](https://www.sci.unich.it/~francesc/teaching/network/transitivity.html)

![screenshot_3](/static/img/latex_3.png)


+ **Approach 2** : Transitivity (Percentage of "open triads" that are triangles in the network)

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
The global clustering coefficient is 3/8 = 0.375
 - First cofunt how many configurations of the form in the network 
   - node 0 : 6
   - node 1 : 0
   - node 2 : 1
   - node 3 : 1
   - node 4 : 0
  - Secound count how many triangles there are in the network: only one 

### Differences in Clustering Measures

- The avarage clustering is **0.43** while the transitivity is **0.375**.
- Accourding to network shapes, the measurements above can differ from each other 
   (To figure out the shpe of abnormal networks, I use both) 

