---
layout: post
title: COVID Immune Suppression Genes
date: 2021-3-3 10:27:0 +0000
comments: True
categories: [COVID, Publications]
---

For posterity's sake I am sharing a Tweet thread for the paper I was involved with [High-content screening of coronavirus genes for innate immune suppression reveals enhanced potency of SARS-CoV-2 proteins](https://www.biorxiv.org/content/10.1101/2021.03.02.433434v1):

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Very excited to have been involved in this SARS-CoV-2 research that introduces new assays to detect viral gene immune suppression capabilities and even discovers a potential new gene overlapping with Spike.<br><br>Read the pre-print here: <a href="https://t.co/8NAGIEgoAk">https://t.co/8NAGIEgoAk</a><br><br>Thread 🧵 1/n</p>&mdash; Trenton Bricken (@TrentonBricken) <a href="https://twitter.com/TrentonBricken/status/1367141915666317312?ref_src=twsrc%5Etfw">March 3, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

In case you would rather read the full text rather than the Tweet thread it is below:

Very excited to have been involved with some new SARS-CoV-2 research that makes the following contributions:
1. Many SARS-CoV-2 proteins are discovered to have enhanced immune suppression compared to other coronaviruses including SARS-CoV-1 and MERS.
2. A potential gene is discovered overlapping the Spike gene that shows immune suppression capabilities.  
3. A suite of high-content cell-based assays are introduced that can be used to rapidly characterize immune suppression of viral genes. These assays should be useful for pandemic responses and virology research more broadly.
Read the pre-print here: <https://www.biorxiv.org/content/10.1101/2021.03.02.433434v1>


![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FTrentonIdeas%2F7fpT0zrllt.png?alt=media&token=b451c4f7-8a93-449a-8961-a312ca0f31c7)

Diving deeper into the paper:

Viruses are cleared from the body unless they counter the innate immune system. The degree of that counteraction may help us predict the transmissibility and pathogenicity of future viruses. For instance, SARS-CoV-2 is more transmissible and often has weaker symptoms than SARS-CoV-1 or MERS. This might be explained in part by greater immune suppression by SARS-CoV-2 genes.

What are these immune responses? In humans, there are a number of intracellular signaling pathways responsible for detecting if the cell is infected. These pathways do things like tell the cell to kill itself (apoptosis) and warn other cells there is an infection.

This figure shows highly simplified IRF3, STAT1 and NFkB pathways. All of these are transcription factors that translocate from the cytoplasm into the nucleus to express the proteins necessary to respond to infection.
![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FTrentonIdeas%2FgETIiAkgXK.png?alt=media&token=e6ce4768-434c-4ddc-bc10-257d73d813b5)

The first assay developed uses high throughput fluorescent microscopy to identify if a specific gene prevents translocation of the aforementioned transcription factors into the nucleus.

For example, see how for IRF3 and NFkB the left most column below shows these transcription factors fluorescing in the cytoplasm but not in the nucleus. Upon stimulation, in the middle and right columns these transcription factors translocate to the nucleus making them light up and the cytoplasm becomes darker.
![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FTrentonIdeas%2F8g2bnPO9-P.png?alt=media&token=0701b3b3-efe9-48e1-9336-4dab7f29de17)

Using this approach we show for each gene across many different coronaviruses how much each suppresses the different transcription factors (in the heat-map red is reduced and green is increased translocation):

![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FTrentonIdeas%2F1fKcVZukuk.png?alt=media&token=4ab0a14f-9261-421b-9570-9a1dbab191dc)

The second assay takes a very different (and super cool) approach to identifying immune suppression genes. One yeast cell expresses the Herpes Simplex Virus-1 (HSV-1) genome. Another yeast cell expresses the viral gene of interest. Both of these yeast cells are fused with a mammalian (HeLa) cell which will become infected *only* if the viral gene of interest is capable of immune suppression (see paper for more details).

This successful infection by HSV-1 is indicated by fluorescence. This protocol and its results for the different coronaviruses are summarized:
![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FTrentonIdeas%2Fu5ymt87fEu.png?alt=media&token=f43c1604-c3d9-4d6b-9608-bdfc5bf4e6df)

A final assay uses flow cytometry and the NFkB pathway specifically to further investigate how it is affected by the different genes (these results support the findings of the first assay outlined).

Moving on to the discovery of the putative novel SARS-CoV-2 gene! It is inside the spike protein, 87-AA long and in a different reading frame. It is found to be highly conserved with the bat RatG13 sequence and have IRF3 and STAT suppression.
![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FTrentonIdeas%2FFEI3QZ1pSo.png?alt=media&token=a7356b82-5f56-4bef-a203-4d6b20d5d5ac)

There are two really cool things to me about the discovery of this gene. First, it is amazing just how optimized viruses are where their genome is capable of simultaneously encoding for Spike and an immune suppression gene (we know SARS-CoV-2 already does this in the N protein and ORF9b with leaky scanning).

Second, it is noted that Spike protein is used in all of our approved SARS-CoV-2 vaccines. For our DNA and mRNA based vaccines, encoding for Spike could also secretly encode for, and potentially express, this novel immune suppression gene. However, the exact Spike nucleotide sequence must be used for this novel gene to be encoded. For example, Pfizer's vaccine is codon optimized in such a way that it does not encode for this novel gene. Moreover, it is very important to emphasize that the FDA approved vaccines have been shown to be safe and so in this case there are not any problems with whether this novel gene is expressed.

However, that we could in the future accidentally encode additional viral proteins hidden inside our vaccines does give support to smaller, epitope based vaccine designs of the sort I have been previously involved with. Rather than using the entire Spike protein that is 1273-AA long, we can hypothetically get even better population coverage with just a handful of epitopes of only between 8 and 25-AA long. Work showing these results: https://www.cell.com/cell-systems/fulltext/S2405-4712(20)30238-6

I am very grateful to have had the chance to play a small part in this work through contributing to image processing portion via a summer internship with the Marks (@deboramarks) and Silver labs. Thanks also to friends, mentors and collaborators @JCVenterInst, @harvardmed, @_nathanrollins, @joshuaerollins and funding from IARPA (@IARPAnews).

Consider reading the full paper as it contains a lot more details!
Also note that this is a preprint. If you read the paper do send feedback. Doing COVID research is too important for mistakes to be made.

------> Paper: <https://www.biorxiv.org/content/10.1101/2021.03.02.433434v1>
