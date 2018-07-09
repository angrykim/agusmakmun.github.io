---
layout: post
title:  "Basic graph analytics (4)"
date:   2018-07-06
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

As a result of analyzing community by applying **[Modularity](https://en.wikipedia.org/wiki/Modularity_(networks))**, Here is the result of communities in the entire network. 

<center><img src="/static/img/communities.png" width="75%"></center>

When modularity is applied, 95 communities can be identified, and the modularity at this time is **0.906**.

- A number of communities :  `95`
- Modularity Point :  `0.906`

Generally, in social graph analaysis, it is judged that the modularity is very well classified if it is **0.4 or more**. 

On a graph with a large number of abnormal networks, a very high value such like this time **(0.906)** can be obtained.

What is next for analyzing communities? 

I will explain more details later on my blog. 




