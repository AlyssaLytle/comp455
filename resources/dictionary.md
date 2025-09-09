---
layout: default
title: Course Dictionary
contributors: Alyssa Lytle
---

# Course Dictionary

Here are some common definitions from class!

## DFAs

### 5-Tuple DFA

A DFA can be represented as $$M = (Q, \Sigma, \delta, s, F)$$ where $$Q$$ is a set of states, $$\Sigma$$ is an alphabet, $$\delta$$ is a transition function, $$s$$ is a start state, and $$F$$ is a set of accept states.

### delta: $$\delta$$

$$\delta$$ can be expressed as a mapping: $$\delta : Q \times \Sigma \to Q$$

### delta hat: $$\hat{\delta}$$

$$\hat{\delta}$$ can be expressed as a mapping: $$\hat{\delta} : Q \times \Sigma^* \to Q  $$
        and for $$a \in \Sigma, x \in \Sigma^*$$

Inductive Definition:

$$
        \begin{eqnarray*}
        \hat{\delta}(q, \epsilon) &=& q \textrm{ (base case)} \\
        \hat{\delta}(q, a) &=& \delta(q,a) \textrm{ (optional second base case)} \\
        \hat{\delta}(q, xa) &=& \delta(\hat{\delta}(q,x),a) 
        \end{eqnarray*}
$$

## NFAs
