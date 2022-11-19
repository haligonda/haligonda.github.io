---
layout: post
title: HRRs Can't Recast Self Attention
date: 2022-11-19 10:24:0 +0000
comments: True
categories: [ML, Neuroscience]
---

*Why Holographic Reduced Representations cannot be used to "Recast Self Attention".*

---

A [paper](https://kdd-milets.github.io/milets2022/papers/MILETS_2022_paper_5942.pdf) was recently posted that claims to use the Holographic Reduced Representations to "recast" Transformer Self Attention. While the paper shows some interesting empirical results, I explain why I think the work is flawed in its theoretical underpinnings.

I'm taking the time to write this critique because I believe it is a critical period for Vector Symbolic Architectures (VSAs) to interface with Deep Learning and that this work represents VSAs poorly.  

---

For some background, the Transformer Self Attention equation for a single query vector is the following:

$$V \text{softmax}(K^T \mathbf{q}_t)$$

where our values and keys are vectors of dimension $$d$$ stored columnwise in matrices $$K \in \mathbb{R}^{d\times T}$$, $$V \in \mathbb{R}^{d\times T}$$, and we are only considering a single query vector $$\mathbf{q}_t \in \mathbb{R}^{d}$$. $$T$$ is used for the number of tokens in the receptive field of the model and $$t$$ subscript is the current time point that we are predicting the next token from. This time point determines the current query and will become crucial later.

We will write:

$$\mathbf{\hat{a}}_t = K^T \mathbf{q}_t = [ \mathbf{k}_1^T \mathbf{q}_t, \mathbf{k}_2^T \mathbf{q}_t , \dots,  \mathbf{k}_T^T \mathbf{q}_t ]^T,$$

to be the attention vector before the softmax operation. Creating this vector takes $$O(dT)$$ compute ($$T$$ dot products each of $$d$$ dimensional vectors).

---

Now here is what the [paper](https://kdd-milets.github.io/milets2022/papers/MILETS_2022_paper_5942.pdf) is doing:

#1. Bind keys and values across the sequence together using the VSA bind operator $$\otimes$$ to create the superposition vector $$\mathbf{s}_{kv}$$:

$$\mathbf{s}_{kv} = \sum_i^T \mathbf{k}_i \otimes \mathbf{v}_i$$

All you need to know about the bind operator is that it produces another n dimensional vector and is invertible where $$ (\mathbf{a} \otimes \mathbf{b}) \otimes \mathbf{a}^{-1} = \mathbf{b} $$.

#2. Create a superposition of all queries across the sequence:

$$\mathbf{s}_q = \sum_i^T \mathbf{q}_i$$

#3. Unbind the query superposition from the key value superposition (this computes the query key dot products between all queries and keys but in superposition):

$$
\begin{align}
\mathbf{z} &= \mathbf{s}_{kv} \otimes \mathbf{s}_q^{-1} = \Big ( \sum_i^T ( \mathbf{k}_i \otimes \mathbf{v}_i ) \Big ) \otimes \Big (\sum_i^T \mathbf{q}_i \Big )^{-1} \\
&= \mathbf{q}_1^{-1} \otimes \Big ( \mathbf{k}_1 \otimes \mathbf{v}_1 + \dots + \mathbf{k}_T \otimes \mathbf{v}_T   \Big ) + \dots + \mathbf{q}_T^{-1} \otimes \Big ( \mathbf{k}_1 \otimes \mathbf{v}_1 + \dots + \mathbf{k}_T \otimes \mathbf{v}_T   \Big )
\end{align}
$$

#4. Extract the attention weights by doing a cosine similarity (CS) between each value vector and $$\mathbf{z}$$ where $$\epsilon$$ is a noise term for everything that doesn't have the corresponding $$\mathbf{v}_i$$ match.

$$
\begin{align}
 \mathbf{\tilde{a}}_t &= [ \text{CS}(\mathbf{v}_1, \mathbf{z}), \dots,  \text{CS}(\mathbf{v}_T, \mathbf{z})  ]^T \\
 &= [ \mathbf{k}_1 \otimes \sum_i^T \mathbf{q}_i^{-1} +\epsilon, \dots, \mathbf{k}_T \otimes \sum_i^T \mathbf{q}_i^{-1} +\epsilon  ]^T \\
 &\approx [ \sum_i^T \mathbf{k}_1^T \mathbf{q}_i +\epsilon, \dots, \sum_i^T \mathbf{k}_T^T \mathbf{q}_i+\epsilon  ]^T \\
\end{align}
$$

Can you spot the difference between this $$\mathbf{\tilde{a}}_t$$ and the original Self Attention $$\mathbf{\hat{a}}_t$$?

$$\mathbf{\tilde{a}}_t$$ computes the dot product between the key vector and **every** query! Not the current query $$\mathbf{q}_t$$ that should be the *only* query used to predict the next token. This means that every attention weight vector is the same across the entire sequence: $$\mathbf{\tilde{a}}_i == \mathbf{\tilde{a}}_j \forall i,j \in [1,T]$$.

There are two solutions to modify this approach so that it is a true recasting of Attention, however, both of them remove the speedup claimed by the paper, leaving only the increase in noise from $$\epsilon$$!

First, if a masked language setting is implemented correctly[^Masking], at e.g. $$t=5$$ we don't have access to the keys, queries and values for $$t>5$$. This means that as we move across the sequence, we incrementally add queries to our query superposition and keys/values to our key+value superposition and compute all of the above equations (#1-#4) each time. This means we have $$O(dT^2)$$ where $$d$$ is the dimensionality and $$T$$ is the sequence length ($$dT$$ operations for a single query because we compute cosine similarity using every value vector and we repeat this for every incremental query in the sequence).

Second, rather than adding more vectors to the superposition, making it noisier, we can keep each query separate when we perform the above operations. However, this is again $$O(dT^2)$$ complexity and reveals how using VSAs here doesn't make sense. We bind together every key and value vector to compute a noisy dot product with the query in superposition, only to then unbind all of them again? This is more expensive and noisier than merely doing a dot product between every key and query as in the original attention operation!

To conclude, while I share with the paper authors the desire to integrate VSAs into Deep Learning, the way it has been done here is ineffective and misleading. What is created is not a re-casting of the Attention operation. It is surprising that it does better than baselines on some idiosyncratic benchmarks and this may also be due to an implementation error.

Please reach out if I am missing something about this paper as I am happy to discuss it and revise this blog post.

## Citation

If you found this post useful for your research please use this citation:
```
@misc{SDMHopfieldNetworks,
  title={HRRs Can't Recast Self Attention},
  url={https://www.trentonbricken.com/Contra-Recasting-Attention/},
  journal={Blog Post, trentonbricken.com},
  author={Trenton Bricken},
  year={2022}, month={November}}
```

### Footnotes
* footnotes will be placed here. This line is necessary
{:footnotes}
[^Masking]: I am concerned that the results in the paper that beat benchmarks are the result of incorrect masking.

---
