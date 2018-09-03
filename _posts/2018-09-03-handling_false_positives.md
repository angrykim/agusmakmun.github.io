---
layout: post
title:  "Handling false positives"
date:   2018-09-03
categories: [Network graph analysis]
---

## Handling false positives

There are four outcomes of the quality of predictions when data is evaluated.

<img src="/static/img/confusion_matrix_1.png" width="65%">

- `True Positive` : These refer to the positive tuples that were correctly labeled by the classifier. 

- `True Negative` : These are the negative tuples that were correctly labeled by the classifier. 

- `False Positive` : These are the negative tuples that were incorrectly labeled as positive

- `False Negative` : These are the positive tuples that were mislabeled as negative 

Let's look at the false positives today.

I think there are two types of false positives in data analysis.

#### CASE - 1

First, **It happens because it is a pattern matched to the pattern that we generated to detect fraud.**

In this case, What we can do is to make them whitelisted. (It is the simplest and most accurate method)

Of course, before you do, you have to create a way to reduce false positives.

If there are so many false positives and you want all of them whitelisted, it does not make sense.

You need to create an accurate model by tuning the algorithm or adding or removing other features.

With every effort, a small number of false positives can still arise.

In that case, you can whitelist the false positives.

#### CASE - 2

The other one is that false positives happen becase of lack of information. 

Do not you know what I mean?

For example, let's say you want to solve a problem with a statistical approach. 

Obviously there will be history of various users in the data you use.

Some users have just subscribed to the service, and some users have used the service for a very long time.

Also, there may be some users who have not used the service for a long time but have used it for a short period of time.

I am not talking about normalization.

To extract patterns, it is necessary to have a certain history of use, but there are users who do not have enough information.

And because of the lack of information, this case we can not tell whether it is "True" or "False".

In other words, you need more data.

For example of the filtering rule for real data, Users who do not satisfy the following conditions can be removed from the data,

The filtering (User Removal) Conditions.

- `Less than 7 Payment_counts in about 6 months of data`

- `The active day was less than 7 days`

- `Less than 3 Deposit events by bank for about 6 months`

Of course, you'll need to share details about how many users are filtered out in the entire data.

Depending on the purpose of the data analysis, filtering may not be necessary but may be very important.

Depending on the purpose of the data analysis, filtering may not be necessary but may be very important.

So for what purpose do you analyze your current data and you have to check the status of the current data accurately.


