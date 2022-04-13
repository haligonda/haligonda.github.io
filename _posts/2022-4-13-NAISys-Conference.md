---
layout: post
title: NAISys Conference Notes
date: 2022-04-13 09:29:0 +0000
comments: True
categories: [ML, Neuroscience]
---

*Notes and themes from NAISys 2022 - Neuroscience to Artificially Intelligent Systems Conference*

---

I had the pleasure of attending NAISys at Cold Spring Harbor Laboratory this April. Going from Tuesday evening to until Saturday midday, it was jam packed with talks and poster sessions.

There were approximately 150 people in attendance and I was impressed by how kindred everyone's latent interests were, right at the intersection of neuroscience and AI. There were many unique and varied expressions of this latent interest, from the circuitry of the Drosophila mushroom body to how insights from sleep can improve deep learning models. But everyone still saw the brain and state of the art deep learning models through a similar lens. Especially post COVID, finding this tribe was both refreshing and highly motivating.

Notable speakers/attendees (I am highly biased) included: Matthew Botvinick (DeepMind), Sam Gershman (Harvard), Joseph Marino (DeepMind), David Ha (Google Brain), Andrew Barto (co-author of *the* textbook on Deep Reinforcement Learning), Dileep George (Vicarious AI, formerly Numenta), Josh Tenenbaum (MIT).

There were a few themes that many of the official talks, posters, and general discussions seemed to circulate around. Many of these should not be surprisingly to those already familiar with the neuro-inspired AI research space:
* **Neurons as independent agents** - neurons compete with each other and have their own utility functions yet ultimately cooperate to achieve the goals of the greater network.
* **Alternatives to backpropagation** - this space feels very saturated and nothing seems to work as well as backprop still. I think we need another review paper like *[Backpropagation and the brain](https://www.nature.com/articles/s41583-020-0277-3)* to summarize all the new models. Ranking them in terms of their biological plausibility and even just summarizing what biology they bring in or neglect would also be cool.
* **Frustrations with weight sharing** - this complaint was mentioned in passing but there wasn't much discussion of methods to resolve it. However, there was a really nice talk by Madineh Sedigh-Sarvestani on retinotopic maps and topography of the visual system. Basically we don't need spatial invariance that is hailed as an advantage of weight sharing because we can move our eye to always put e.g. faces in the center of our vision where our face detectors can reside.
* **Modeling temporality** - modeling multiple foveations, predicting the next token, recurrent network dynamics.
* **Top down feedback connections** - we have been modelling these for some time without any major SOTA results. There was a talk by Anima Anandkumar that did seem to suggest some SOTA results on robustness but I need to read the paper in full.
* **Reward prediction error and dopamine** - a true classic. TD learning for the win etc.
* **Spiking neural networks** - still trying to get the analog computing infrastructure to work and still performing worse than backprop. [Hardware lotteries](https://www.trentonbricken.com/ComputingPathDependencies/)!
* **Canonical circuitry** - I was expecting some discussion of canonical circuits in the brain but not the amount of focus that there was during the poster sessions on the cerebellum/mushroom body! This is because not many people know that the cerebellum has 80% of all neurons in the entire brain or does anything beyond fine motor function. It was refreshing that many attendees knew all of this and more. Maybe because it is a clean circuit there is so much interest? It was definitely encouraging.
* **Connectomics** - another exciting trend in the poster sessions was work using the Fly Hemibrain dataset! There is so much incredible information in this dataset but it all looks like spaghetti. It was motivating to see some groups starting to simulate specific circuits and untangle this neural spaghetti. The most interesting result here out of Johns Hopkins (presented as a poster by Justin Joyce) was learning that there are strong recurrent connections between Kenyon cells in the mushroom body that were previously under-appreciated(maybe entirely unknown?) and these are capable across a wide range of possible synaptic strengths of inducing recurrent dynamics that converge to fixed points in the system.

---

**A plea for thresholds of biological plausibility** -- The number of times I heard the word "biologically plausible" was ear ringing. I really wish that the field would lay out a biological plausibility spectrum ranging from the dubious "this algorithm has two different phases so I will call it a wake sleep cycle!" to rigorous "we implemented the Granule cell -> Purkinje cell -> Deep Cerebellar Nuclei circuitry of the cerebellum along with its inhibitory interneurons as a deep learning model." Even just having a list of what work the field considers to be the most biologically realistic work would be very useful as a touchstone. An even bigger ask would be a list of all the different biologically plausible components that our Deep Learning models are still missing that we can use as a reference for how many "boxes" a particular approach ticks.

---

I got a few things out of this conference: First and foremost, motivation. There are a lot of people out there interested in similar questions who share a conviction that this work is interesting and powerful. Second, some short term research ideas for new angles to take on my current project. Third, more context for the field, who is working on what and why they think it matters. I look forward to seeing many of the attendees at future events as the conference circuit is (hopefully!) now back to life.

*Thanks to [Joe Choo-Choy](https://twitter.com/joechoochoy) and [Miles Turpin](https://twitter.com/milesaturpin) for reading drafts of this piece. All remaining errors are mine and mine alone.*
