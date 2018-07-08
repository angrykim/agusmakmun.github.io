---
layout: post
title:  "Basic graph analytics (4)"
date:   2018-07-06
categories: [Network graph analysis]
---

I posted several topics about **basic graph analytics** before. 

However, Graph analysis technique is very useful when the entire network is categorized into community units in a data set.

If you do not understand it well, check out the following example.

<center><img src="/static/img/total_network.png" width="85%"></center>

As you can see in the picture, The one network in `the red circle` in the above picture is directly connected to a number of small networks.

Should we look at these huge networks as a single network?

Not at all, It is better for us to divid it into a number of network units(communities).

By dividing into community units, we can analyze features of each community and judge where or not it is fraud.

As a result of analyzing community by applying **Modularity**, I found strong negative patterns in network of `red circle`.

In the next post, I will explain "`Modularity` and `the negative pattern` that I found in the follwoing network. 

<center><img src="/static/img/main_network.png" width="75%"></center>

Tip: I give you little bit information of `broker` and `banker` in the picture.
