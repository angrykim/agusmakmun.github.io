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

Please be noted that modualrity is a score that allows you to consider how valid your community is when you select the number of communities in your entire data set. 

Tips: Nomally, Over the score of 0.4 modularity, it represents that the network is very well devided. 
