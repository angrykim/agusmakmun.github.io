---
layout: post
title:  "Network graph analysis (3)"
date:   2018-06-07 
categories: [Network graph analysis]
---

Let's learn a little more about network analysis(A.K.A Graph Theory).

**Centrality**

One of the most widely used concept for Network Analysis is "Centrality".
It aims to find the most important nodes in a given network. There may be differeint notations of "important" so there are many centrality meatusre. 

* `Degree Centrality`- The first and conceptually the simplest Centrality definition. This is the number of edges connected to a node. 
                        In the case of a directed graph, we can have 2 degree centrality measures(inbound, outbound)

* `Closeness Centrality` - Closeness centrality of a node is the average length of the shortest path from the node to all other nodes

* `Betweenness Centrality` - Number of times a node is present in the shortest path between 2 other nodes. 

**Network Density(Local Clustering Coefficient)**

* A measure of how many edges a Graph has.
  It is defined as the number of edges in a portion of a social network to the maximum number of edges that theoretically make up the network. 
  
  The following **formula** is used to calculate the relative density of a portion of network. 
 
  For a complete undirected Graph the Density is 1, while it is 0 for an empty Graph.
  
  `c - the number of observed edges.`
  
  `n - the total number of nodes in the network.`
  
 ![screenshot_1](/static/img/Density.jpg)

* ***What is the purpose of Network density?***

  * Density measures are extremely useful in <U>determining potential fraud hotspots</U> in retail banking from a maze of account transactions and applied control measures. 
 
  * Credit card transaction monitoring and money-laundering are potentially two areas where density metrics could trigger the necessity for deeper investigations. 
 
* Please refer to the previous post of **[Local Clustering Coefficient](https://github.com/angrykim/angrykim.github.io/blob/master/_posts/2018-05-29-Network_graph_analysis_for_fraud_events_1.md)** with the acutal example.


**Graph Randomizations**

* While the definitions of some Graph metrics maybe easy to calculate, it is not easy to understand their relative importance. 
We use Network/Graph Radomizations in such cases. We calculate the metric for the Graph at hand and for another similar Graph that is randomly generated. This similarity can foir example be the same number of density and nodes. Typically we generate a 1000 similar random graphs and caculate the Graph metric for each of them and then compare it with the same metric for the Graph at hand to arrive at some  notion of a banchmark 

* **[output] integer**

**My Solution:**

```python
def numberOfEvenDigits(n):
    return len(filter(lambda m: m.isdigit() and int(m) % 2 == 0, str(n)))
```

**Rests Tests:**

```
n: 1010
Output: 2

n: 123
Output: 1

n: 135
Output: 0
```
