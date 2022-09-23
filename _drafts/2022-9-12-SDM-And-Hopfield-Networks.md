---
layout: post
title: Sparse Distributed Memory and Hopfield Networks
date: 2022-09-12 16:24:0 +0000
comments: True
categories: [Education, Personal]
---

*How Sparse Distributed Memory is a generalization of Hopfield Networks and they have become more closely linked over time.*

---

We first provide background on Hopfield Networks. We then review how SDM is a more general form of the original Hopfield Network. Finally, we provide insight into how modern improvements to the Hopfield Network modify the weighting of patterns, making them increasingly convergent with SDM.

## Background on Hopfield Networks

In SDM the core primitive is neurons from which patterns are represented. We can abstract away neurons as done in \cite{SDMAttention, SDM}, considering only patterns and queries, but even then we care about the number of neurons that are expected to exist in the intersection between pattern and query hyperspheres.

In contrast, for Hopfield Networks the core primitive is patterns from which neurons are represented. Hopfield Networks before the modern continuous version all use bipolar vectors $$\bar{\mathbf{a}} \in \{-1,1\}^n$$ where the bar denotes bipolarity \cite{OGHopfield, modernHopfield, hopfieldallyouneed}. The Hopfield Network update rule in matrix form, in its typical auto-associative format where $P_p=P_a$ is:
%
\begin{equation}
    \label{eq:HopfieldUpdateRule}
    \bar{\mathbf{y}} = \bar{g}(  \bar{P}_a \bar{P}_a^T \bar{\boldsymbol{\xi}} ) \qquad \bar{g}(e)=
\begin{cases}
  1, & \text{if}\ e> 0 \\
  -1, & \text{else}
\end{cases}
\end{equation}
%
Interpreting this equation from the perspective of SDM, we first compute a re-scaled version of the Hamming distance between our query and pattern addresses $\bar{P}_a^T \bar{\boldsymbol{\xi}}$ (this can be done by taking a dot product between bipolar vectors and applying the linear transformation:  
%
\begin{equation}
    \label{eq:BipolarHammConversion}
    d(\mathbf{x}, \mathbf{y}) = \frac{n-\bar{\mathbf{x}}^T\bar{\mathbf{y}}}{2}
\end{equation}
%
We then use this distance metric to weight each pattern before mapping back into our bipolar space. Using bipolar values also removes the need of a normalizing constant where only need to check if $\bar{g}(\cdot)$ is greater than 0.

Instead of first multiplying the query with the pattern addresses, we can instead perform $\bar{P}_a \bar{P}_a^T=M$ which gives us a symmetric, $n$x$n$ dimensional matrix. We can interpret this symmetric matrix $M$ as containing $n$ neurons where each neuron's address is a row and its value vector is the corresponding column, which by symmetry is the row transpose. Therefore, the number of neurons is defined by the pattern dimensionality $n$ and the neuron address and value vectors are derived from $\bar{P}_a \bar{P}_a^T$.

## SDM as a Generalization of Hopfield Networks

It was first established in [citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262) that SDM was a generalization of Hopfield Networks. This insight was presented in the Appendix of [citation](https://arxiv.org/abs/2111.05498) and outlined in more detail, front and center here. Hopfield Networks [citation](https://www.pnas.org/doi/10.1073/pnas.79.8.2554) can be represented by SDM's neuron primitives as a special case where there are no distributed reading or writing operations [citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262). This makes the weighting of patterns in the read operation the bipolar re-scaling of the Hamming distance to the query.

The Hopfield version of SDM has neurons centered at each pattern so $$r=m$$ and $$X_a=P_a$$. Distributed writing and reading are removed by setting the Hamming distance threshold for writing to $$d_\text{write}=0$$ and for reading to $$d_\text{read}=n$$. This means patterns are only written to the neurons centered at them and the query reads from every neuron. For reading, however, rather than binary neuron activations using the Heaviside function $$b(\cdot)$$, neurons are weighted by the bipolar version of the Hamming distance from Eq. \ref{eq:BipolarHammConversion}. %Moreover, because the Hopfield Network is almost always autoassociative, $$P_p=P_a=X_a=X_v$$  ([citation](https://arxiv.org/abs/2111.05498), [citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262)).

Writing out the SDM read operation in full with bipolar vectors that make our normalizing constant unnecessary, we have:

$$\bar{\mathbf{y}} =  \bar{g} \Big ( \bar{X}_v  b \big (  d_\text{read}, \frac{n-\bar{X}_a^T \bar{P}_a}{2} \big ) \Big ) = \bar{g} \Big ( \underbrace{ \bar{P}_p b( d_\text{write}, \frac{n-\bar{X}_a^T \bar{P}_a}{2})}_{\text{Write Patterns}}  \underbrace{ b \big (  d_\text{read}, \frac{n-\bar{X}_a^T \bar{P}_a}{2} \big ) }_{\text{Read Patterns}} \Big )$$

Looking first at the write operation where $$d_\text{write}=0$$:
$$\bar{P}_p b( d_\text{write}, \frac{n-\bar{X}_a^T\bar{P}_a}{2})=\bar{P}_p I = \bar{P}_p=\bar{P}_a$$

where $$I$$ is the identity matrix and $$P_p=P_a$$ in the typical autoassociative setting. For the read operation we remove the threshold and Hamming distance scaling:
$$b(d_\text{read}, \frac{n-\bar{X}_a^T\bar{\boldsymbol{\xi}} }{2}) = \bar{X}_a^T \bar{\boldsymbol{\xi}} =\bar{P}_a^T \bar{\boldsymbol{\xi}}.$$

Together these modifications turn SDM into the Hopfield Network of Equation:  \ref{eq:HopfieldUpdateRule}.

## Differences between SDM and Hopfield Networks

While Hopfield Networks have been traditionally presented and used in an autoassociative fashion, by using a synchronous update rule they can also be heteroassociative $$ \bar{\mathbf{y}} = \bar{g}(  \bar{P}_p \bar{P}_a^T \bar{\boldsymbol{\xi}} )$$ but do not work as well \cite{[citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262)}. However, a solution is to operate autoassociatively but concatenate together the pattern address and pointer as was introduced in \cite{modernHopfield}. Figure TO ADD depicts this solution. Because heteroassociative learning is crucial from a biological perspective for organisms to learn how to respond to their environment, we consider the biological plausibility of this implementation compared to that of SDM in Section \ref{sec:SDMBioPlausibility}.

A second and more important difference between SDM and Hopfield Networks is that the latter is biologically implausible because of the weight transport problem, whereby the afferent and efferent weights are symmetric. In Fig ... this is shown by the weights going into the neurons and weights coming out of them being the transpose of each other. At the expense of biology, these symmetric weights allow for the derivation an energy landscape that can be used for convergence proofs and to solve optimization problems \cite{HopfieldTravellingSalesman, [citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262)}. Meanwhile, SDM is not only free from weight symmetry but also has its mapping onto the cerebellum outlined in Section \ref{sec:SDMBioPlausibility} \cite{SDM,SDMBookChapter1993}.\footnote{The surprise that SDM maps to the cerebellum so well should be dampened by the fact that it respected key biological constraints such as Dale's law and treated neurons as the core primitive during its development\cite{SDM}. However, this mapping remains nonetheless striking.}
% We evaluate how important weight symmetry, and by proxy this biological hurdle is by testing the Hopfield Network's performance without weight transport in Section \ref{sec:WeightSymmetry} NEED TO THINK MORE ABOUT HOW THIS CAN EVEN BE TESTED.

A third difference is in how SDM and Hopfield Networks weight their patterns. We can interpret the Hopfield update as computing the similarity between $$P_a^T \boldsymbol{\xi}$$ which, because of the bipolar values, has a maximum of $$n$$, minimum of $$-n$$ and moves in increments of 2 (flipping from a +1 to -1 or vice versa). This distance metric between each pattern and the query results in our query being attracted to patterns with high similarity and repulsed away from those dissimilar. Distinctly, all patterns aside from those completely orthogonal contribute to the query update while in SDM, it has been shown that patterns have approximately exponential weighting for nearby patterns and those further than $$d(\boldsymbol{\xi},\mathbf{p_a})>2d$$, receiving no weighting at all [citation](https://arxiv.org/abs/2111.05498).

Finally, both Hopfield Networks and SDM, while using different parameters, have been shown to have the same information content as a function of their parameter count \cite{[citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262)}. Yet, these parameters are used in different ways because of SDM's neuron primitive. Notably, SDM can increase its memory capacity up to a limit by increasing the number of neurons $$r$$ rather than needing to increase the dimensionality $$n$$. We consider the storage capacities of our models as a function of other metrics such as model sparsity in Section \ref{sec:CapacityComparisons}

%It has also been noted that small, biologically plausible modifications to SDM can allow it to maintain its original capacity while handling correlated input patterns that the Hopfield Network cannot \cite{[citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262)}. This is because SDM can learn through competitive dynamics to have neurons that are distributed through the space to match the pattern distribution and can dynamically update the Hamming distance $$d$$ so that it can still converge to the right pattern \cite{[citation](https://www.sciencedirect.com/science/article/abs/pii/0364021388900262)}. This is crucial as most, if not all, real world applications of associative memory will deal with correlated patterns.

## Modern Hopfield Networks Approximate SDM
\label{sec:modernHopfieldNet}
% Implement SDM-like Hamming Distance Thresholds

The binary modern Hopfield Network introduced in \cite{modernHopfield}, showed that using higher order polynomials to assign new pattern weightings in the read operation increased capacity. In particular, adding odd and rectified polynomials, which put more weight on memories that are closer to the query, better separating the signal of the target pattern from the noise of all others. The energy function used that we are trying to minimize is:

$$E=-\sum_{\bar{\mathbf{p}}\in \bar{P}} K_a \Big( \bar{\mathbf{p}}_a \bar{\boldsymbol{\xi}} \Big )=-\sum_{\bar{\mathbf{p}}\in \bar{P}} K_a \Big( \sum_i^n [\bar{\mathbf{p}}_a]_i \bar{\boldsymbol{\xi}}_i \Big )$$

where:
$$
K_a(x)=
\begin{cases}
  x^a, & x \geq 0 \\
  0, & x < 0
\end{cases}
$$

with $$x<0$$ being the rectified component that is optional and $$a$$ being the order of the polynomial. It can be shown that the original Hopfield Network energy function used a second order polynomial $$a=2$$ \cite{modernHopfield}. The query updates its bit in position $$i$$ by comparing the difference in energy if this bit was "on" or "off" (1, -1 when bipolar here):
$$
    \label{eq:ModernHopfieldEnergyEquation}
    \bar{\mathbf{y}}_i = \text{Sign}\Bigg[ \sum_{\bar{\mathbf{p}}\in \bar{P}} \Big ( K \big( [\bar{\mathbf{p}}_a]_i + \sum_{j \neq i} [\bar{\mathbf{p}}_a]_j \bar{\boldsymbol{\xi}}_j \big ) - K \big( - [\bar{\mathbf{p}}_a]_i + \sum_{j \neq i} [\bar{\mathbf{p}}_a]_j \bar{\boldsymbol{\xi}}_j \big ) \Big ) \Bigg]
$$

Whichever configuration between "on" and "off" gives the highest output from $$K(x)$$, corresponding to a lower energy state, will be updated towards.

Using even polynomials in the energy difference means that attraction to similar patterns (closer than orthogonal) is rewarded as much as making opposite patterns (further than orthogonal) further away. Odd polynomials reward attraction to similar patterns also but instead reward reducing the distance of opposite patterns, trying to make them orthogonal. In other words, an even polynomial would rather have a vector be opposite than orthogonal while it is the other way around for an odd polynomial. Meanwhile, the rectification of the polynomial, which empirically resulted in a higher memory capacity, simply ignores all opposite patterns \cite{modernHopfield}. Finally, the capacity of the binary modern Hopfield Network was further improved by replacing the polynomial with an exponential function $$K(x)=\exp(x)$$ \cite{exponentialHopfield}.

Fundamentally, these odd, rectified, and exponential $$K(x)$$ functions make the Hopfield Network more similar to SDM by introducing approximate Hamming distance thresholds around the query, and either ignore (in the rectified case), or penalize, vectors for being greater than orthogonal distance away. The weighting of vectors remains different between the polynomials, exponential such that they have different information storage capacities. However, by introducing their de facto Hamming distance thresholds, these Hopfield variants are all convergent with the read operation of SDM. This is particularly the case for the exponential variant because SDM weights its patterns in an approximately exponential fashion [citation](https://arxiv.org/abs/2111.05498).

Beyond the convergence in pattern weightings, we note that the last step in making the exponential variant of the modern Hopfield Network into Attention is to make it continuous \cite{hopfieldallyouneed}. This is done by modifying the energy function in Eq. \ref{eq:ModernHopfieldEnergyEquation} so that it enforces a vector norm (SDM does this too [citation](https://arxiv.org/abs/2111.05498)) and then using the Concave Convex Optimization Procedure (CCP) to find local minima (flipping bits is no longer an option). The CCP optimization is related to Expectation Maximization \cite{hopfieldallyouneed,CCP}, which can be viewed as related to the SDM query update rule: using the Hamming distance threshold we compute an expectation from neurons within the Hamming distance threshold, and then perform a maximization step by updating our query. % unsure if this is worth pointing out. Many things can be related to EM

Finally there weak indications of convergence between the range of optimal SDM Hamming distance thresholds $$d$$ and optimal polynomials $$a$$ in the modern discrete Hopfield Network \cite{modernHopfield}. It was found when pattern representations were learnt that the optimal polynomial for maximizing accuracy in a classification task was neither too small nor too large. This is also the case for optimal $$d$$, which are related via their effect on the pattern weightings. They have a useful interpretation of their system where some of the vectors could serve as prototypes to the solution and be very close, while others vectors could represent features that different components had. The best solution interpolated between these two approaches. One can view the prototypes as anchoring the solution and the features providing generalization ability. Even for SDM's neuron perspective, the same intuition may apply where it is advantageous to have some protoypes read from neurons nearby but also collect features from related patterns stored in more distant neurons. In \cite{SDMBookChapter1993}, an example of noisy patterns being stored and their combination being a noise free version is related to this line of thinking on using features from related patterns.
