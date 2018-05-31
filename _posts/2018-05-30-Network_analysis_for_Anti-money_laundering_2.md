---
layout: post
title:  "Network analysis for Anti-money laundering (AML) - (2)"
date:   2018-05-30
categories: [Network graph analysis]
---

# [Network graph analysis - 2](https://en.wikipedia.org/wiki/Social_network_analysis)

Previous posts did not mention **Directed network**. However, in general, when you detect fraud or abuse events in finance, We use a directed network. This is very useful for understanding the flow of money and others

So today, I want to talk about a little difficult topic of directed network graph.

Acutally, I'm goiing to talk about `HITS algorithms`. it is nomally used in Network graph analysis for the purpose of 

**"Extracting important web pages from link structure"** 

Once you understand `HITS algorithms`, You will see how we can apply it to financial data set to detect abuse, fraud, and others. 

**Example:**

* For `mo = 1`, the output should be `getMonthName(mo) = "Jan"`,
* For `mo = 0`, the output should be `getMonthName(mo) = "invalid month"`.

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
