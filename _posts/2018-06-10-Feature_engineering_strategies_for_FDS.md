---
layout: post
title:  "Feature engineering strategies for FDS"
date:   2018-06-10
categories: [Statistics]
---

I have recently read interesting *thesis* so i wanted to implement it in code.

The title is **Feature engineering strategies for credit card fraud detection**, and the paper author is **AlejandroCorrea Bahnsen**.

If you want to see brief information, Please check his **[blog](https://blog.easysol.net/feature-engineering-for-fraud-detection/).**

As the title shows us that this paper introduces various feature engineering strategies for creidt card fraud detection.

Most of features in this paper have been used in the current Fraud Detection System (at least we have already implimented it internally).

However, There was an interesting analysis of the payment time, which attracted my attention.

![screenshot_1](/static/img/PeriodicTime1.png)

Motivation was as follows. 

A customer is expected to use their credit cards at very similar hours so the confidence interval for individuals can be calculated.

And to illustrate this, the commonly used **"arithmetic mean"** shows that it does not fit into data consisting of repeated(periodic) behavior of the time feature like the above screenshot.


So the proposed way is to use **Von-Mises Distribution** to calculate confidence intervals for each user.

> What is [Von Mises Distribustion ?](https://en.wikipedia.org/wiki/Von_Mises_distribution) 

The von Mises distribution of a subset of transactions made by the same customer is calculated as

![screenshot_2](/static/img/PeriodicTime-Formula2.png)

where and are the periodic mean and periodic standard deviation, respectively. Moreover, the Von Mises distribution is calculated using the first order Bessel function.

![screenshot_3](/static/img/PeriodicTime-Formula3.png)

So far, It seems really reasonable for us to use so let's implement it in Python code.

To better understand the code, I splitted it into some specific parts.

+ **Sample code**

~~~python

from scipy.stats import vonmises

def get_mu_kappa(time):
    a = np.sin(time).sum()
    b = np.cos(time).sum()
    c = len(time)
    std = np.sqrt(np.log(1/(((a/c))**2 + (((b/c))**2))))
    mean = 2*(np.arctan(a/((((b**2) + (a**2))**0.5)+b)))
    kappa = (1/std)
    return mean, kappa
    
def getCI(input_list, alpha = 0.95):
    mu, kappa = get_mu_kappa(np.array(input_list) * math.pi / 12)
    temp = list(map(lambda x: round(x*12/math.pi, 2) if x*12/math.pi > 0 else round(x*12/math.pi, 2) + 24, vonmises.interval(alpha, kappa, loc=mu, scale=1)))
    return temp[0], temp[1] 
~~~

As you can see the code block above, I implemented the formula intuitively with Python.

Using the vonmises of the Python library, you can easily compute the interval of each customer.

Also, using scipy's `circmean`, and `circstd` makes code much easier and more concise than the above code.

        
