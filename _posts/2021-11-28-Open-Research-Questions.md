---
layout: post
title: Open Research Questions
date: 2021-11-28 09:23:0 +0000
comments: True
categories: [Neuroscience, Misc]
---

*Research Questions I am interested in/confused by but am not actively researching.*

---

I will try to keep this post up to date as more questions come up or are resolved. I'm really trying to not let perfect be the enemy of good here. Last updated: March 23rd, 2021.

---
<br>
<div style="margin-left:20px">
  <b>1. The effects of neuron number on cognition.</b>
</div>

Something doesn't add up with the evidence that I am aware of here. Having more neurons is known to boost intelligence with two examples given below. However, missing neurons or entire brain regions seems not to matter so much in two other cases given. One additional case has fortunately been disproven. I have not researched this space as much as I would like but am flagging it as a current area of interest and confusion:

More neurons increase intelligence/task performance:

* There is a small but robust correlation between neuron number and intelligence. Something like [~15% variance explained](https://en.wikipedia.org/wiki/Neuroscience_and_intelligence). I say "number of neurons" not "brain size" because birds [have many more neurons](https://www.scientificamerican.com/article/bird-brains-have-as-many-neurons-as-some-primates/) proportional to their brain size (to be lighter weight for flying of course).

* It was known that the visual cortex of the brain is utilized in blind braille readers and that this utilization is functional as targeted [TMS](https://en.wikipedia.org/wiki/Transcranial_magnetic_stimulation) was able to interfere with performance. An [interesting experiment](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2516172/) was done where sighted people were kept in total darkness for five days straight. During this time they were taught braille and within the first few days of having no visual stimulation, their visual cortex also appeared to be used for braille and functionally important to its comprehension. By the 5th day they performed better than sighted controls. When they returned to light after the five days, the visual cortex was no longer used for braille processing and their performance declined somewhat, being less statistically different to those never blindfolded. This is strong evidence for rapid plasticity between brain regions and weak evidence for more neurons increasing performance. Original source, [After Phrenology](https://smile.amazon.com/After-Phrenology-Neural-interactive-Bradford/dp/0262028107?sa-no-redirect=1), which I have a book review of [here](https://www.trentonbricken.com/After-Phrenology/). This study was done in 2008 and I am curious what related work exists.

Fewer neurons don't decrease intelligence/task performance?!:

* Missing left temporal lobe causes language processing to move into the right temporal lobe. Missing an entire lobe seems to have no tradeoff in cognitive processing. The patient is an above average IQ professional who picked up Russian for fun later in life. What gives? I have spoken to an author on the paper and they don't know what tradeoff exists with the patient even after having interacted with them quite a bit. Paper [here](https://www.biorxiv.org/content/10.1101/2021.05.28.446230v1).

  - One important nuance here that is different from the next case study is that it is suspected the left temporal lobe atrophied due to a micro-stroke very early in development. This gave the brain more time to adapt? But there are still fewer neurons for processing.

---
<br>
<div style="margin-left:20px">
  <b>2. What is the metabolic cost of a neuron in proportion to its size?</b>
</div>

Granule cells in the cerebellum make up [80% of all neurons in the brain](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2776484/). This is an incredible amount for a brain region that has been given far less attention than the neocortex or hippocampus and until recently was thought to only help with fine motor coordination. While these granule cells are small, they must require a huge metabolic cost. This leads to the question of what is the metabolic cost of a neuron in proportion to its size? In other words, how expensive and by proxy significant is this concentration of granule cells?
  - A bonus question is what is the metabolic cost of neuron maintenance versus firing of action potentials? Maybe there is a large fixed cost during development to create and wire up these granule cells but a low variable cost as action potentials are cheap or sparse activations mean they don't fire often?
  - Shameless plug: see my [recent paper](https://arxiv.org/abs/2111.05498) for an overview of Sparse Distributed Memory and its relation to the Transformer Deep Learning model for a hypothesis on why these granule cells may be so important...

  ---
  <br>
  <div style="margin-left:20px">
    <b>3. Why do SSRIs take so long to start working?</b>
  </div>

Selective Serotonin Reuptake Inhibitors (SSRIs) take weeks or months to start working when used to treat depression. This is weird because their known mechanism of action -- keeping more serotonin in synaptic juctions -- starts working immediately. More info on them and the question of how much better they are than placebos [here](https://slatestarcodex.com/2014/07/07/ssris-much-more-than-you-wanted-to-know/) and [here](https://slatestarcodex.com/2018/11/07/ssris-an-update/).

---

  **Other weird/fun/interesting facts that may hint at something more:**
* Elephants have [20 copies of p53 which may be why they never get cancer](https://www.nature.com/articles/nature.2015.18534). More than half of human cancers have a mutation to P53 and almost all cancers have functional inactivation of it. This is because it is the main controller protein for if a cell should replicate or repair itself.  

* The brain may have such[ redundant and Byzantine control mechanisms partly to fight off parasitic control](https://slatestarcodex.com/2019/08/19/maybe-your-zoloft-stopped-working-because-a-liver-fluke-tried-to-turn-your-nth-great-grandmother-into-a-zombie/). Rabies and toxoplasma are the two most impressive parasites for controlling complex mammalian brains. Rabies is capable of inducing a fear of water while toxoplasma makes rats attracted to cats and even sexually aroused by their urine. Meanwhile in ants the parasitic fungus [Ophiocordyceps](https://www.theatlantic.com/science/archive/2017/11/how-the-zombie-fungus-takes-over-ants-bodies-to-control-their-minds/545864/) turns them into "zombies" where they will find the nearest tree, climb to the top, lock their jaws onto a branch and dangle from it. This is all to allow the fungus to sprout a fruiting body from its head releasing its spores from on high to more victims.

* The vagus nerve (connecting your brain to your gut) is in constant war with your microbiome. We have enzymes to break down bacterially produced dopamine and serotonin. We have antibodies to target bacterially produced neuropeptides. The microbiome can influence mood, make babies cry, direct our food cravings, and help us break down lactic acid so we can [run farther and longer](https://www.nature.com/articles/s41591-019-0485-4#:~:text=atypica%20improves%20run%20time%20via,process%20that%20enhances%20athletic%20performance.). ([Source](https://onlinelibrary-wiley-com.ezp-prod1.hul.harvard.edu/doi/10.1002/bies.201400071))

* Infectious diseases may be the cause of neuro-degeneration and disorder. After long suspicions, Epstein Barr virus (EBV) was recently validated as causing multiple sclerosis by inducing an autoimmune response. ["In the United States, about half of all five-year-old children and about 90% of adults have evidence of previous infection."](https://en.wikipedia.org/wiki/Epstein%E2%80%93Barr_virus). Meanwhile, there is growing evidence that [strep throat](https://ajp.psychiatryonline.org/doi/full/10.1176/appi.ajp.2020.20111598) can cause OCD and [herpes virus is correlated with Alzheimers](https://twitter.com/TrentonBricken/status/1483482760522215425). And remember that viruses persisting throughout your life is the [normal way of things](https://www.trentonbricken.com/GreatestHost/) (it is only with the advent of high density cities that short lived, hard hitting viruses like the flu or common cold are viable).
