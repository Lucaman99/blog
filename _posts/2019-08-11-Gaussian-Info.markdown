---
layout: post
title:  "Making Sense of Gaussian Quantum Information Day 1: Density Matrices"
tags: [software, math, physics, quantum-computing]
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<i>So right now, I'm reading one of the better-known expository papers on Gaussian Quantum Information, and in order to really understand everything that's going on, I'm trying to prove certain propositions in the paper for myself/write down a commentary on some of the main ideas. I'm going to be writing a mini-series over the next few days with all of these assorted proofs/explanations/notes. Now, I know this blog is called the **Coherent** State, but this blog series will likely be everything but coherent. I'm typing all of this stuff up mostly for my own benefit and understanding, so making it super readable isn't my number one priority, however, I will do my absolute best to not go totally off the deep end with lack of explanations!</i>

<br>

**Density Matrices**

A density matrix is a manner in which mixed quantum states can be represented. For a bit of background, a pure state is a quantum state in which our system is represented by a certain state vector with probability $$1$$, while a mixed state is a system that has certain probabilities of being represented by multiple different state vectors. We define our density matrix as:
<br><br>
<center>
$$\hat{\rho} \ = \ \displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}|$$
</center>
Now, I'm going to present a few proofs of some density matrix-related stuff. I spent a little while today working out these proofs myself, for my own understanding, so I hope they're correct!
<br><br>
**Proposition:** Density matrices have trace equal to $$1$$.
<br><br>
**Proof**
<br><br>
Recall that the trace of a matrix is defined as the sum of the diagonal entries of a matrix:
<br><br>
<center>
$$\text{Tr}(M) \ = \ \displaystyle\sum_{i} \ M_{ii}$$
</center>
Let us now take the trace of the density matrix:
<br><br>
<center>
$$\text{Tr}(\hat{\rho}) \ = \ \text{Tr} \Big( \displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}| \Big) \ = \ \displaystyle\sum_{j} \ p_{j} \ \text{Tr} (|\psi_{j}\rangle \langle \psi_{j}|)$$
</center>
But let us also consider that the trace of an $$N \ \times \ N$$ matrix can be given by finding diagonal matrix elements with the set of standard orthonormal basis vectors of $$\mathbb{R}^N$$, which we will call $$B \ = \ \{|i\rangle, \ i \ = \ 0, \ ..., \ N \}$$:
<br><br>
<center>
$$\text{Tr}(M) \ = \ \displaystyle\sum_{i} \ \langle i| M |i\rangle$$
</center>
So now we have:
<br><br>
<center>
$$\displaystyle\sum_{j} \ p_{j} \ \text{Tr} (|\psi_{j}\rangle \langle \psi_{j}|) \ = \ \displaystyle\sum_{j} \ p_{j} \ \Big (\displaystyle\sum_{i} \langle i|\psi_{j}\rangle \langle \psi_{j}|i\rangle \Big) \ = \ \displaystyle\sum_{j} \ p_{j} \ \Big (\displaystyle\sum_{i} \langle \psi_{j}|i\rangle \langle i|\psi_{j}\rangle \Big) \ = \ \displaystyle\sum_{j} \ p_{j} \ \langle \psi_{j}| \Big(\displaystyle\sum_{i} |i\rangle \langle i| \Big) |\psi_{j}\rangle$$
$$\Rightarrow \ \displaystyle\sum_{j} \ p_{j} \ \langle \psi_{j}| \Big(\displaystyle\sum_{i} |i\rangle \langle i| \Big) |\psi_{j}\rangle \ = \ \displaystyle\sum_{j} \ p_{j} \ \langle \psi_{j}|\psi_{j}\rangle \ = \ \displaystyle\sum_{j} \ p_{j} \ = \ 1$$
</center>
We know the probability of being in any one of the quantum states must be normalized (sum to one). After all, the quantum system has to be in <i>some</i> state!
<br><br>
**Proposition:** We can assert that for some observable $$\hat{A}$$, that $$\langle \hat{A} \rangle \ = \ \text{Tr}(\hat{A} \hat{\rho})$$.
<br><br>
**Proof**
<br><br>
This is a fairly natural extension of our previous proof:
<br><br>
<center>
$$\text{Tr}(\hat{A} \hat{\rho}) \ = \ \text{Tr} \Big( \displaystyle\sum_{j} \ p_{j} \ \hat{A}|\psi_{j}\rangle \langle \psi_{j}| \Big) \ = \ \displaystyle\sum_{j} \ p_{j} \ \Big (\displaystyle\sum_{i} \langle i| \hat{A}|\psi_{j}\rangle \langle \psi_{j}|i\rangle \Big) \ = \ \displaystyle\sum_{j} \ p_{j} \ \langle \psi_{j}| \Big(\displaystyle\sum_{i} |i\rangle \langle i| \Big) \hat{A}|\psi_{j}\rangle \ = \ \displaystyle\sum_{j} \ p_{j} \ \langle \hat{A} \rangle_{j} \ = \ \langle \hat{A} \rangle$$
</center>
<br><br>
**Proposition:** If we know that $$\hat{\rho}^{2} \ = \ \hat{\rho}$$ (is idempotent), then our density matrix represents one pure state.
<br><br>
**Proof**
<br><br>
<center>
$$\hat{\rho}^2 \ = \ \hat{\rho} \ \Rightarrow \ \Big(\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}|\Big)^2 \ = \ \displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}|$$
$$\Rightarrow \Big(\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}|\Big)^2 \ = \ \Big(\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}|\Big)\Big(\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}|\Big) \ = \ \displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \Big(\langle \psi_{j}|\displaystyle\sum_{i} \ p_{i} \ |\psi_{i}\rangle \langle \psi_{j}|\Big)$$
</center>
But we can assume our states are orthogonal, without any loss of generality (as we can always construct an orthogonal basis of state vectors using the Gram-Schmidt procedure), so the bra $$\langle \psi_j|$$ effectively "picks out" terms of the sum over $$i$$ where $$i \ = \ j$$:
<br><br>
<center>
$$\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \Big(\langle \psi_{j}|\displaystyle\sum_{i} \ p_{i} \ |\psi_{i}\rangle \langle \psi_{j}|\Big) \ = \
\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \Big(\displaystyle\sum_{i} \ p_{i} \ \langle \psi_{j}|\psi_{i}\rangle \langle \psi_{j}|\Big) \ = \
\displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \ p_{j} \ \langle \psi_{j}| \ = \ \displaystyle\sum_{j} \ p_{j}^2 \ |\psi_{j}\rangle \ \langle \psi_{j}|$$
</center>
<br><br>
Going back to our original statement:
<br><br>
<center>
$$\displaystyle\sum_{j} \ p_{j}^2 \ |\psi_{j}\rangle \ \langle \psi_{j}| \ = \ \displaystyle\sum_{j} \ p_{j} \ |\psi_{j}\rangle \langle \psi_{j}| \ \Rightarrow \ p_{j}^2 \ = \ p_{j}
 \ \Rightarrow \ p_{j} \ = \ 0, \ 1$$
</center>
This means that the probability of our system being in some state is $$1$$ or $$0$$. Since the probabilities sum to one, our system is in one state with complete certainty (probability $$1$$), and not in any of the other states (probability $$0$$), therefore the density matrix represents a pure state. Notice how we are allowed to say that each term in the sum is equal to the other, as we assume each of our states is orthogonal, and therefore linearly independent.
<br><br>
Alright, that's all for today, I'll be back tomorrow with some actual Gaussian Quantum Information stuff, not just background on density matrices!
