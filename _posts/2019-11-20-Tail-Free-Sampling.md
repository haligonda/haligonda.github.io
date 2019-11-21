---
layout: post
title: Tail Free Sampling
date: 2019-11-20 12:58:0 +0000
comments: True
categories: ML 
---

With the increasing ability for neural networks to model natural language accurately, there is a growing number of applications for open-ended neural generation tasks. Yet, recent efforts in open-ended generation continue to present questions as to why likelihood-maximization methods such as greedy search produce degenerate outputs. This issue, and the natural replaceability of words, motivates the use of stochastic, sampling based approaches. However, sampling in a way that generates both high quality and diverse outputs remains a non-trivial problem.

As a result, I have developed Tail Free Sampling, a new sampling method that I argue is more theoretically sound than the existing sampling approaches: Top-K and Nucleus (CITE THESE). It also requires less hyperparameter tuning and these hypereparameters generalizes better across language generation domains.

This blog post provides: 
1. A summary of the problem of open-ended generation and motivation behind Tail Free Sampling
2. Background on previous approaches
3. The Tail Free Sampling algorithm
4. Comparisons between Tail Free Sampling, Top-K, and Nucleus Sampling
5. Attempts at empirical validation of Tail Free Sampling to show it produces superior results. 

This project is currently stuck at the empirical validation stage. The interesting reasons and my attempts to validate are outlined at length in Section 5, however the underlying source of difficulty is that sampling methods improve the quality of the average generation not by increasing the quality of the very best generations, but raising the quality of the worst. I would be very interested in collaborating with anyone who has ideas for how to validate different open-ended generation sampling methods, to my knowledge this is something that has not been done to date in any paper utilizing Top-K or Nucleus sampling.

## Summary

Say you're an avid Dungeons and Dragons (D&D) player and have trained an autoregressive neural network on lots of existing examples of D&D adventures. You now want to use machine learning to generate new adventures that have never existed before. 

How do you generate new text from the trained model? This turns out to be a difficult problem. For close-ended generations, where the length of the output is predictable from the input, likelihood-maximization strategies such as greedy and beam search perform well. Examples of close-ended generation include image captioning and machine translation. 

However, for something like a D&D adventures, which can be of very different lengths, there is no clear point at which the generation should stop, thus making it "open-ended". 
Trying to use likelihood-maximization strategies to approximate the highest probability generations currently fails, resulting in highly repetitive and nonsensical outputs.

As a result, sampling strategies must be used to create diversity, however sampling from the whole distribution of words risks derailing the model because of sampling low probability words. Therefore, sampling must be constrained to a promising subset of high probability words. But what is the correct trade-off between sampling enough words to create diversity and not too many to ensure quality?

BLOG POST STILL BEING FINISHED