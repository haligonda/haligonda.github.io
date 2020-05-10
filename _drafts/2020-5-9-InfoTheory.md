---
layout: post
title: Information Theory Questions
# date: 2020-9-1 14:02:0 +0000
comments: True
categories: ML
---

I am really enjoying reading David MacKay's [Information Theory, Inference and Learning Algorithms](https://www.inference.org.uk/itprnn/book.pdf) which is available to read online for free.

The book has a number of great exercises in each chapter and I thought I would share a running list of my favourites. (I think and hope that this is legal as I am giving full credit to David MacKay and not profiting off of this). I list the questions by chapter and the answers in a lower down section. I also add some of my own questions where I think they would be useful to check the understanding of certain concepts/equations which are covered in the book before questions leveraging them are asked. My questions are denoted (M#), questions from the book by (Chapter#.Question#). If anyone knows how to hyperlink between questions and answers in Markdown please let me know!

## Questions

M1. What is the information content of an unbiased dice roll?

M2. What are the equations for expectation and variance of a Random Variable?

2.16 (hint: use the Central Limit Theorem)

![DiceThrows](../images/InfoTheory/DiceThrows.png)

M3. A coronavirus serology test (for having previously had an infection) has a 98% specificity and 95% specificity. Your mother, an upstanding citizen who has obeyed quarantine rules, takes the test and it comes back positive. What is the probability your mother has coronavirus?

M . "Frequentists argue that you can only use probabilities to describe the ____ of outcomes ____ experiments"

A: frequencies; random 

M . "Forward probability problems involve a _____ model that describes a process that is assumed to give rise to some data"

A: generative

M . "Like forward probability problems, inverse probability problems involve a _____ of a process, but instead of computing the probability distribution of some quantity produced by the process, we compute the ______ of one or more of the _______ in the process, given the observed variables. This invariably requires the use of ______."

A: generative model; *conditional* probability; unobserved variables; Bayes’ theorem

M . What is the Bayesian response to Frequentist claims that they make  assumptions about the prior? 

A: assumptions are necessary no matter what. Bayesian priors are more transparent. There are assumptions with the likelihood as much as the prior, data collection etc etc etc. 

M4: What is Jensen's Inequality?

M5. What is Kullback-Leibler Divergence?

2.25 Take the hint into account but there is another (less elegant) way to solve it!

![MaxEntropy](../images/InfoTheory/ProveEntropyMax.png)

3.8 Try to calculate the probabilities of being correct under the different scenarios too.

![MH1](../images/InfoTheory/MonteHall1.png)

3.9

![MH2](../images/InfoTheory/MonteHall2.png)

4.1 First try to find what the minimum number of necessary weighting steps is for the optimal solution.

![BallWeights](../images/InfoTheory/BallWeights.png)

## Answers

2.16

![DiceThrowsS](../images/InfoTheory/DiceThrowsS.png)

2.25

![MaxEntropyS1](../images/InfoTheory/ProveEntropyMaxS1.png)
![MaxEntropyS2](../images/InfoTheory/ProveEntropyMaxS2.png)

3.8

![MonteHallS1a](../images/InfoTheory/MonteHallS1a.png)
![MonteHallS1b](../images/InfoTheory/MonteHallS1b.png)

3.9

![MonteHallS2](../images/InfoTheory/MonteHallS2.png)

4.1 
![BallWeights](../images/InfoTheory/BallWeightsHint.png)
![BallWeights](../images/InfoTheory/BallWeightsS.png)