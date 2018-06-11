---
layout: post
title:  "How to evaluate imbanaced classfication model"
date:   2018-06-11
categories: [Machine learning]
---

If you have spent some time in applying machine learning, you would have definitely come across imbalanced binary classfication problem
(class imabalance). 

# What is class imbalance?

> It is the problem in machine learning where the total number of a class of data (positive) is far less than the total number of another class of data (negative). This problem is extremely common in practice and can be observed in various disciplines including fraud detection, anomaly detection, medical diagnosis, oil spillage detection, facial recognition, etc.

The conventional model evaluation methods do not accurately measure model performance when faced with imbalanced class.

Let's take a look at the sample confusion matrix of fraud events. 

![screenshot_1](/static/img/confusion_matrix.jpg)

Normally, When evaluating a binary classfication model, we use `PRECISION`, `RECALL`, and `ACCURACY`.

![screenshot_2](/static/img/model_evaluation.jpg)

Using the exmaple of confusion matrix above, the `PRECISION`, `RECALL`, and `ACCURACY` are all over 99%.

Have you noticed? 

Even if the model can not detect a single fraud event, the conventional model evaluation method shows a detection rate of 99% or more.

In other words, Existing conventional model evaluation methods do not fit the imbalanced class.

# How we can solve this problem?

There are the number of way to deal with this problem. but i normally use **MCC**. 

I will not explain everything above, but you can get the information you need through Google.

I will be able to explain just one of these, which is **Local & Global Clustering Coefficient**.

`Local Clustering Coefficient(LCC)`refers to the `Connection` between nodes, which means it is defined as the number of connections a node has, divided by the total possible connections a node could have. 

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

The reason for obtaining Local Clustering Coefficent (LCC) is to compute `Global Clustering Coefficient(GCC)`.

What is `Global Clustering Coefficient(GCC)`?

It is known that the connections between nodes in the real network have relatively high density of connections, which means nodes in a real network tend to cluster well compared to a random network.

So, In the graph theory, `Global Clustering Coefficient(GCC)` is used as a measure of how each node tends to cluster together. 

The first method that we can compute GCC is `Average of LCC` over all nodes in a graph, and this can be easily done with networkx.

+ `Approach 1` : Average LCC over all nodes in the graph using networkx in python.

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


+ `Approach 2` : Transitivity (Percentage of "open triads" that are triangles in the network)

![screenshot_4](/static/img/triangles.jpg)

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

 - First cofunt how many configurations of the form in the network 
   - node 0 : 6
   - node 1 : 0
   - node 2 : 1
   - node 3 : 1
   - node 4 : 0
  - Secound count how many triangles there are in the network: **only one**
  - The global clustering coefficient is 3/8 = `0.375`

     
   
   
        
