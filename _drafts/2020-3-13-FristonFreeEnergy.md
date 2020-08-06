---
layout: post
title: Friston Free Energy Principle
#date: 2020-3-13 08:27:0 +0000
comments: True
categories: ML 
---
Borrowing the notation and formalism from Kai Ueltzhöffer's brilliant piece ... which in turn borrows from Reinforcement Learning or Active Inference

Letting $$S^*$$ be the state space:

$$H(S^*) = - \int_{\mathbf{s}^* \in S^*} p(\mathbf{s}^*) \ln p(\mathbf{s}^*) \,d\mathbf{s}^*$$

Letting $$O$$ be the observation space and defining the potentially noisy, non-bijective mapping from states to observations $$o=g(s*)$$ and $$\epsilon$$ be noise:

$$ H(S^*) \leq H(O) - \int_{\mathbf{s}^* \in S^*} p(\mathbf{s}^*) \ln |\dfrac{\partial g(s*)}{\partial \mathbf{s}^*}| \,d\mathbf{s}^* + H(S^*|O)$$

$$H(S^*) \leq H(O) - \int_{\mathbf{s}^* \in S^*} p(\mathbf{s}^*) \ln |\dfrac{\partial g(\mathbf{s}^*)}{\partial \mathbf{s}^*}| \,d\mathbf{s}^*$$

This inequality exists because $$H(S^*|O) \geq 0$$ with equality when $$S^* == O$$.
The second term 
$$\int_{\mathbf{s}^* \in S^*} p(\mathbf{s}^*) \ln |\dfrac{\partial g(s*)}{\partial \mathbf{s}^*}| \,d\mathbf{s}^*$$
 is the change of variables formula which represents the sensitivity of the organism's sensory organs to a change of state. For a fixed point in evolution we assume this term is constant and optimized.

 $$H(O^*) = - \int_{\mathbf{o}^* \in O^*} p(\mathbf{o}^*) \ln p(\mathbf{o}^*) \,d\mathbf{o}^*$$

$$D_{KL}[q(s) || p(s|o)] = \int_{s \in S} q(s) \ln \dfrac{q(s)}{p(s|o)} ds
= \int_{s \in S} q(s) \ln q(s) ds - \int_{s \in S} q(s) \ln p(s|o) ds$$

$$= \int_{s \in S} q(s) \ln q(s) ds - \int_{s \in S} q(s) \ln \dfrac{p(o|s)p(s)}{p(o)}ds$$

$$= \int_{s \in S} q(s) \ln q(s) ds -  \int_{s \in S} q(s) \ln p(o|s) ds - \int_{s \in S} q(s) \ln p(s) ds + \int_{s \in S} q(s) \ln p(o) ds$$

$$= D_{KL}[q(s)||p(s)] -  \int_{s \in S} q(s) \ln p(o|s) ds + \int_{s \in S} q(s) \ln p(o) ds$$


$$KL[p(o_{t:T}|\pi)||p^{\sim}(o_{t:T})]=E_{p(o_{t:T}|\pi)}[\ln p(o_{t:T}|\pi)|| \ln p^{\sim}(o_{t:T})]$$

$$p(o_{t:T}|\pi) = p(o_T|o_{T-1},\pi)p(o_{T-1}|o_{T-2},\pi)...p(o_{t+1}|o_{t},\pi)p(o_{t}|\pi)$$

$$p(o_{t+1}|o_t,\pi) = E_{q(s_{t}|o_t)} E_{p(s_{t+1}|s_{t}, a_t),a_t \sim \pi(o_t, s_t)}[P(o_{t+1}|s_{t+1})]$$
