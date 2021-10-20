---
layout: post
title: Attention Approximates Sparse Distributed Memory
date: 2021-10-20 07:027:0 +0000
comments: True
categories: [ML, Neuroscience, Publications]
---

*We show the heuristic Attention operation can be implemented with simple properties of high dimensional vectors, in a biologically plausible fashion.*

**Paper Abstract:** While Attention has come to be an important mechanism in deep learning, it emerged out of a heuristic process of trial and error, providing limited intuition for why it works so well. Here, we show that Transformer Attention closely approximates Sparse Distributed Memory (SDM), a biologically plausible associative memory model, under certain data conditions. We confirm that these conditions are satisfied in pre-trained GPT2 Transformer models. We discuss the implications of the Attention-SDM map and provide new computational and biological interpretations of Attention.

Work done in collaboration with [Cengiz Pehlevan](https://pehlevan.seas.harvard.edu/).

**Paper Link:** (coming by the end of October 2021!)

**MIT Center for Brains Minds+ Machines Talk and [Slides](https://docs.google.com/presentation/d/1gGErBUIDM5SQCroovgTGmwgaz61EZ6RdN-eg8niCb0w/edit?usp=sharing):**<br>

<iframe width="560" height="315" src="https://www.youtube.com/embed/THIIk7LR9_8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



*Thanks to Alex Cuozzo, Pentti Kanerva, Joe Choo-Choy, Beren Millidge, Jacob Zavatone-Veth, Blake Bordelon, Nathan Rollins, Alan Amin, Max Farrens, David Rein, Sam Eure, Grace Bricken, and Davis Brown for providing invaluable inspiration, discussions and feedback. Special thanks to Miles Turpin for help working with the Transformer model experiments.*

*I would also like to thank the open source software contributors that helped make this research possible, including but not limited to: Numpy, Pandas, Scipy, Matplotlib, PyTorch, HuggingFace, and Anaconda.*
