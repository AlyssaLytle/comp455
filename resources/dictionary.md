---
layout: default
title: Course Dictionary
contributors: Alyssa Lytle
---

# Course Dictionary

Here are some common definitions from class!

## DFAs

### 5-Tuple DFA

A DFA can be represented as $M = (Q, \Sigma, \delta, s, F)$ where $Q$ is a set of states, $\Sigma$ is an alphabet, $\delta$ is a transition function, $s$ is a start state, and $F$ is a set of accept states.

### $\delta$

* $\delta : Q \times \Sigma \to Q$

### $\hat{\delta}$

* $\dhat : Q \times \Sigma^* \to Q  $$
        and for $a \in \Sigma, x \in \Sigma^*$

Definition:

        \begin{eqnarray*}
        \dhat(q, \epsilon) &\defeq& q \textrm{ (base case)} \\
        \dhat(q, a) &\defeq& \delta(q,a) \textrm{ (optional second base case)} \\
        \dhat(q, xa) &\defeq& \delta(\dhat(q,x),a) 
        \end{eqnarray*}


## NFAs
