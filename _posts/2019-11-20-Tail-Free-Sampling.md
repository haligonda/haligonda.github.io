---
layout: post
title: Tail Free Sampling
date: 2019-11-20 12:58:0 +0000
comments: True
categories: ML 
---

### Abstract

With the increasing ability for neural networks to model natural language accurately, there is likely to be a growing number of applications for open-ended neural generation tasks. Yet, recent efforts in open-ended generation continue to present questions as to why likelihood-maximization methods such as greedy search produce degenerate outputs. This issue, and the natural replaceability of words, motivates the use of stochastic, sampling based approaches. However, sampling in a way that generates both high quality and diverse outputs remains a non-trivial problem. 

I have developed Tail Free Sampling , we give theoretical and empirical evidence for why existing approaches to sampling are not robust enough across generation contexts and problem domains. We propose a new sampling algorithm, Tail Free sampling, which uses the second derivative of the model's probability distribution over its tokens to ensure that only those above a certain probability threshold are sampled from. We show through computational [and human (NEED TO DO)] evaluation that this results in generations that are on average of a higher quality and less degenerate than those from other methods, namely Top-K and Nucleus sampling. This is because samples more often come from only the subset of tokens that are replaceable in a given context, reducing the probability the generation is derailed and better representing the underlying replaceability of similar tokens seen in many language tasks.

### Intro