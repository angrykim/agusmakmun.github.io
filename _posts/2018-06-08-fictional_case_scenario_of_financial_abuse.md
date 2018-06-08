---
layout: post
title:  " fictional case scenario of financial abuse (1)"
date:   2018-06-08 
categories: [scenario, network graph analysis]
---


Let's check the first fictional scenario of financial abuse case.

#### Ficational case scenario - 1 : 

~~~~

We are a company called "P-wallet" that provides mobile payment service(It provides `payment, money transfer, deposit, and withdraw by bank account`).

Recently, the marketing team has confirmed that many users have entered our service through various events.

However, we have confirmed that the actual AU ratio is not significantly different from the previous one.

Details of the event are as follows.

1. During the event period, new subscribers charge $10 or more for getting an additional $5 to a P-wallet account.

2. Charge $5, regardless of the payment amount, when using the first payment service among new users (only the condition 1 is satisfied).

~~~~

First, the string is divided into the least possible number of disjoint **substrings** consisting of identical characters
for example, `"aabbbc"` is divided into `["aa", "bbb", "c"]`
Next, each substring with length greater than one is replaced with a concatenation of its length and the repeating character
for example, substring `"bbb"` is replaced by `"3b"`
Finally, all the new strings are concatenated together in the same order and a new string is returned.

#### SUBSTRING

A **substring** of a string `S` is another string `S'` that occurs in `S`. For example, `"Fights"` is a substring of `"CodeFights"`, but `"CoFi"` isn't.

**Example**

For `s = "aabbbc"`, the output should be `lineEncoding(s) = "2a3bc"`.

**Input/Output**

* [time limit] 4000ms (py)
* [input] string s (String consisting of lowercase English letters.)

_Constraints:_ `4 ≤ s.length ≤ 15.`

* [output] string (Encoded version of s.)

**Solution:**

```python
import re
def lineEncoding(s):
    grub = [ m.group(0) for m in re.finditer(r"(\w)\1*", s )]
    numb = 0
    out  = []
    for i in grub:
        numb += 1
        if len(i) > 1:
            out.append(grub[numb-1].replace(grub[numb-1], str(len(i))+i[0]))
        else:
            out.append(i)
    return ''.join(out)
```

**Result Tests:**

```python
>>>
s = "aabbbc"
>>> lineEncoding(s)
"2a3bc"
>>>
>>> s = "abbcabb"
>>> lineEncoding(s)
"a2bca2b"
>>>
>>> s = "abcd"
>>> lineEncoding(s)
"abcd"
>>>
```
