---
layout: post
title: Open Research Questions
date: 2021-11-28 09:23:0 +0000
comments: True
categories: [Neuroscience, Misc]
---

*Research Questions I am interested in/confused by.*

---

I will try to keep this post up to date as more questions come up or are resolved. Last updated: November 28th, 2021.

---

1. The effects of neuron number on cognition.

Something doesn't add up with the evidence that I am aware of here. Having more neurons is known to boost intelligence with two examples given below. However, missing neurons or entire brain regions seems not to matter so much in two cases given. One additional case has fortuantely been disproven. I have not researched this space as much as I would like but am flagging it as a current area of interest and confusion:

More neurons increase intelligence/task performance:

* There is a small but robust correlation between neuron number and intelligence. Something like [~15% variance explained](https://en.wikipedia.org/wiki/Neuroscience_and_intelligence). I say "number of neurons" not "brain size" because birds [have many more neurons](https://www.scientificamerican.com/article/bird-brains-have-as-many-neurons-as-some-primates/) proportional to their brain size (to be lighter weight for flying of course).

* It was known that the visual cortex of the brain is utilized in blind braille readers and that this utilization is functional as targeted [TMS](https://en.wikipedia.org/wiki/Transcranial_magnetic_stimulation) was able to interfere with performance. An [interesting experiment](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2516172/) was done where sighted people were kept in total darkness for five days straight. During this time they were taught braille and within the first few days of having no visual stimulation, their visual cortex also appeared to be used for braille and functionally important to its comprehension. By the 5th day they performed better than sighted controls. When they returned to light after the five days, the visual cortex was no longer used for braille processing and their performance declined somewhat, being less statistically different to those never blindfolded. This is strong evidence for rapid plasticity between brain regions and weak evidence for more neurons increasing performance. Original source, [After Phrenology](https://smile.amazon.com/After-Phrenology-Neural-interactive-Bradford/dp/0262028107?sa-no-redirect=1), which I have a book review of [here](https://www.trentonbricken.com/After-Phrenology/). This study was done in 2008 and I am curious what related work exists.

Fewer neurons don't decrease intelligence/task performance?!:

* Missing left temporal lobe causes language processing to move into the right temporal lobe. Missing an entire lobe seems to have no tradeoff in cognitive processing. The patient is an above average IQ professional who picked up Russian for fun later in life. What gives? I have spoken to an author on the paper and they don't know what tradeoff exists with the patient even after having interacted with them quite a bit. Paper [here](https://www.biorxiv.org/content/10.1101/2021.05.28.446230v1).

  - One important nuance here that is different from the next case study is that it is suspected the left temporal lobe atrophied due to a micro-stroke very early in development. This gave the brain more time to adapt? But there are still fewer neurons for processing.

* Removing an entire hemisphere from epileptic patients doesn't diminish their cognitive abilities? On [Twitter](https://twitter.com/roboso/status/1465061418735222784?s=20) it has been mentioned that the hemispheres removed were already damaged by the seizures. Moreover, these patients are not neuro-typical in having severe enough seizures to justify such an invasive surgery at such a young age. Paper [here](https://academic.oup.com/brain/article/126/3/556/321214).

* Missing 95% of brain volume in hydrocephalus patients was claimed to not have any effect on cognitive function with an examlpe of a 126 IQ patient. This result was disproven by Gwern [here](https://www.gwern.net/Hydrocephalus).

---

2. What is the metabolic cost of a neuron in proportion to its size?

Granule cells in the cerebellum make up [80% of all neurons in the brain](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2776484/). This is an incredible amount for a brain region that has been given far less attention than the neocortex or hippocampus and until recently was thought to only help with fine motor coordination. While these granule cells are small, they must require a huge metabolic cost. This leads to the question of what is the metabolic cost of a neuron in proportion to its size? In other words, how expensive and by proxy significant is this concentration of granule cells?
  - A bonus question is what is the metabolic cost of neuron maintenance versus firing of action potentials? Maybe there is a large fixed cost during development to create and wire up these granule cells but a low variable cost as action potentials are cheap or sparse activations mean they don't fire often?
  - Shameless plug: see my [recent paper](https://arxiv.org/abs/2111.05498) for an overview of Sparse Distributed Memory and its relation to the Transformer Deep Learning model for a hypothesis on why these granule cells may be so important...
