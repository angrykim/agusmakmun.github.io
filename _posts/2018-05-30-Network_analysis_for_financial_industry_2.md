---
layout: post
title:  "Network analysis for financial industry - (2)"
date:   2018-05-30
categories: [Network graph analysis]
---

# [Network graph analysis - 2](https://en.wikipedia.org/wiki/Social_network_analysis)

The previous post did not mention **Directed network**. 

However, in general, when you detect fraud or abuse events in finance, 

It is a common method to use for direct network graph.  
(It is very useful for understanding **the flow of money** and others)

So today, I want to talk about how to measure the importance of the centrality of a node in a directed netowrk. 

Acutally, I'm goiing to talk about `Page Rank algorithm`. 

It was developed by the Google founders when they were thinking about how to measure the importance of webpages using the hyperlink network structure of the web.

But not just only web page, but also any type of network can use **Page Rank** to compute central(important) nodes 

Let's check the basic concept of `Page Rank algorithm`. 

![screenshot_1](/static/img/page_rank.jpg)

![screenshot_2](/static/img/page_rank_2.jpg)

3 important concepts of PageRank (To become an important node...)
*  `There are many other nodes that tell me I'm important.`  
   --> _The number of PR(Ti)_
*  `It is better if the node referred to me as an important node is an important node in a network` 
   --> _Hight PR(Ti) value_
*  `It would be good if the node that referred to me as an important node is only connected to an important node in a network` 
   --> _Low C(Ti) value_

## Page Rank algorithm:

*  `Assign all nodes a PageRank of 1/n` 
*  `A good authority(in-degree)` represented a page(node) that was linked by **many different hubs.**

**Input/Output**

* [time limit] 4000ms (py)
* [input] integer mo (A non-negative integer).
* **Constraints:** `0 ≤ mo ≤ 15`.
* **[output] string**

A `3`-letter abbreviation of month number `mo` or `"invalid month"` if the month doesn't exist.

Here are abbreviations of all months:

**My Solution:**

```python
def getMonthName(mo):
    months = {
        1: "Jan", 2: "Feb", 3: "Mar", 4:"Apr", 
        5: "May", 6: "Jun", 7: "Jul", 8:"Aug", 
        9: "Sep", 10: "Oct", 11: "Nov", 12: "Dec"
    }
    if mo in months.keys():
        return months.get(mo)
    return "invalid month"
```

**Result Tests**:

```python
>>> getMonthName(1)
"Jan"
>>> getMonthName(0)
"invalid month"
>>>
```
