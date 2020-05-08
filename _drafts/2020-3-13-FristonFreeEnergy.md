---
layout: post
title: Friston Free Energy Principle
#date: 2020-3-13 08:27:0 +0000
comments: True
categories: ML 
---
Borrowing the notation and formalism from Kai Ueltzhöffer's brilliant piece ... which in turn borrows from Reinforcement Learning or Active Inference

Letting $$S^*$$ be the state space:

$$H(S^*) = - \int_{s^* \in S^*} p(s^*) \ln p(s^*) \,ds^*$$

Letting $$O$$ be the observation space and defining the potentially noisy, non-bijective mapping from states to observations $$o=g(s*)$$ and $$\epsilon$$ be noise:

$$H(O) \geq H(S^*) + \int_{s^* \in S^*} p(s^*) \ln |\dfrac{\delta g(s*)}{\delta s^*}| \,ds^* + \epsilon$$

The second term $$\int_{s^* \in S^*} p(s^*) \ln |\dfrac{\delta g(s*)}{\delta s^*}| \,ds^*$$ is the change of variables formula which represents the sensitivity of the organism's sensory organs to a change of state. For a fixed point in evolution we assume this term is constant and optimized.