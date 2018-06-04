---
layout: post
title:  "Network analysis for financial industry - (2)"
date:   2018-05-30
categories: [Network graph analysis]
---

# [Network graph analysis - 2](https://en.wikipedia.org/wiki/Social_network_analysis)

The previous post did not mention **Directed network**. 

However, in general, when you detect fraud or abuse events in finance, It is a common method to use for direct network graph.  
(It is very useful for understanding **the flow of money** and others)

So today, I want to talk about a little difficult topic of directed network graph with a really useful algorithm.

Acutally, I'm goiing to talk about `HITS(Hypertext induced Topic Selection) algorithm`. 

it is nomally used in Network graph analysis for the purpose of 

**"Extracting important web pages from directed link structure"**. 

It is develped in the context of how a search engine might go about finding importatnt web pages(central nodes).

In other words, with HITS algorithm, we can find central nodes over all nodes in the network. 

Once you understand `HITS algorithm`, You will see how we can apply it to financial data set to detect abuse, fraud, and others. 

Let's check the terms first 

## Hubs and Authorities:

*  `A good hub(out-degree)` represented a page(node) that pointed to **many other pages(nodes).**
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
