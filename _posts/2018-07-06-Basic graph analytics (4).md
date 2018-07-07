---
layout: post
title:  "Basic graph analytics (4)"
date:   2018-07-06
categories: [Network graph analysis]
---

Today, let's talk about a more advanced topic of graph analysis.

I talked about graph analysis in the previous post.

But if one graph is linked to another graph and this graph represents the entire data, 

will the Graph analysis method we have discussed so far apply effectively? 

Is this huge graph only one fraud? 

Which Node is the most effective to detect?

We need to reduce the size of the indirectly connected network. and that for we use Modularity to divide the network units into community units. 

Modularity is a measure of the structure of graphical networks. It determines the strength of the network as a whole. It describes how easily a network could be clustered into communities or modules.

Please be noted that A network with high modularity points to strong relationships within the same communities but weaker relationship across different communities. It is one of the fundamental methods used during community detection in graphs. Modularity  nds its applications in a wide range of areas such as social networks, biological networks, and collaboration networks.

Tips: Nomally, In social graph analysis, Over the score of 0.4 modularity, it represents that the network is very well devided. (however, if it is related to fraud data set, it should be at least over 0.6 ) 

