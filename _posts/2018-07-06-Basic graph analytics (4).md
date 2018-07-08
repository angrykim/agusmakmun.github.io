---
layout: post
title:  "Basic graph analytics (4)"
date:   2018-07-06
categories: [Network graph analysis]
---

I posted about basic graph analytics before.

But sometimes, We need to divide a huge network into a community.

This is the case.

We need to reduce the size of the indirectly connected network. and that for we use Modularity to divide the network units into community units. 

Modularity is a measure of the structure of graphical networks. It determines the strength of the network as a whole. It describes how easily a network could be clustered into communities or modules.

Please be noted that A network with high modularity points to strong relationships within the same communities but weaker relationship across different communities. It is one of the fundamental methods used during community detection in graphs. Modularity  nds its applications in a wide range of areas such as social networks, biological networks, and collaboration networks.

Tips: Nomally, In social graph analysis, Over the score of 0.4 modularity, it represents that the network is very well devided. (however, if it is related to fraud data set, it should be at least over 0.6 ) 

![screenshot_1](/static/img/total_network.png)

For example, the one network in the red circle in the above picture is directly connected to the entire network.

Should we analyze these huge networks in a single network unit?

Of course, it is better for us to divid it into a number of network units(communities) and that for we can analyze each unit and probably find the most important network unit like this. 

<center><img src="/static/img/main_network.png" width="75%"></center>

in this netowrk,  There are three broker nodes and a banker group.

Each broker receives small amount of money from other nodes and delivers the money to the banker group.
