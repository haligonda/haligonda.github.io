---
layout: post
title: Path Dependencies in Compute
date: 2022-03-23 09:37:0 +0000
comments: True
categories: [Deep Learning]
---

*Computer hardware and the cruciality of fast iteration cycles.*

---

I think often about the paper [The Hardware Lottery](https://arxiv.org/abs/2009.06489) which argues that much of the Deep Learning research agenda has been set by the research tools at our disposal. LISP being the dominant coding language until the 1990s majorly biased researchers towards symbolic approaches to AI. GPUs today bias us towards backpropagation and dense neural networks that fail to take advantage of sparsity.

> A striking example of this jump in efficiency
is a comparison of the now famous 2012
Google paper which used 16,000 CPU cores
to classify cats (Le et al., 2012) to a paper
published a mere year later that solved the
same task with only two CPU cores and four
GPUs (Coates et al., 2013).

I expand on the benefits of sparsity as an example later. But to first highlight two other path dependencies in computing:
* The Von Neumann computing architecture totally dominates all of computing. There are other perfectly valid forms of computing with different costs and benefits for different algorithms. You can think of them as using different basis functions just like a Fourier basis can make certain operations far more efficient. For example the ["Von Neumann bottleneck"](https://arxiv.org/pdf/2006.01981.pdf) where memory and compute operations are kept separate requiring them to be shuttled back and forth. This has restricted a number of other approaches to computing including using spiking neural networks and analog computing. See [this great review article on the potentials of analog computing](https://arxiv.org/abs/2106.05268) and [RAIN Neuromorphics](https://rain.ai/) that is doing something about it.

* Python only became a dominant programing language when Numpy was made fast enough.

These examples emphasize that functionality > theoretical elegance. As cool as spiking neural networks are, the field will fail to make fast enough progress and attract enough funding/researchers if it is fundamentally bottlenecked by iteration cycles[^Musk]. This makes our research tools absolutely crucial to the state space of questions that we can and will ask.

---

**Why sparsity matters**

I am biased because of my research but can point to sparsity as not only increasing memory efficiency and reducing FLOPs but also increasing [adversarial robustness](https://jov.arvojournals.org/article.aspx?articleid=2772000), performing [density estimation](https://proceedings.neurips.cc/paper/2018/hash/ee14c41e92ec5c97b54cf9b74e25bd99-Abstract.html), and enabling [continual learning](https://arxiv.org/pdf/2107.07617.pdf). However, current deep learning accelerators completely fail to take advantage of dynamic, unstructured sparsity. See [this Numenta paper](https://numenta.com/assets/pdf/research-publications/papers/Sparsity-Enables-100x-Performance-Acceleration-Deep-Learning-Networks.pdf) for the theoretical speed ups from sparsity and [this](https://towardsdatascience.com/sparse-matrices-in-pytorch-part-2-gpus-fd9cc0725b71) analysis for how PyTorch's sparse library only makes sense if you have greater than 99% sparsity! Otherwise the overhead is not worth it and you are better off explicitly using the same dense matrix operations that your accelerator is performing under the hood.

---

*Thanks to [Joey Velez-Ginorio](https://twitter.com/joeyginorio) and [Davis Brown](https://twitter.com/davisbrownr) for influential discussions and reading drafts of this piece. All remaining errors are mine and mine alone.*

---

### Footnotes
* footnotes will be placed here. This line is necessary
{:footnotes}

[^Musk]: I got to meet Max Hodak, who co-founded NeuraLink with Elon Musk about what made Musk so unique and he said it was his ability to figure out how to rapidly accelerate iteration cycles.
