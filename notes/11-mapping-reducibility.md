---
title: "Mapping Reducability"
author: "Alyssa Lytle"
date: "October 23, 2025"
---

<!-- pandoc -t slidy -s notes/11-mapping-reducibility.md -o slides/11-mapping-reducibility.html --webtex -->

# Mapping Reducibility

## Mapping Reducibility

* The goal of this lesson: formalize the concept of reducibility

* We define the *mapping reducibility* of problem $A$ to problem $B$ as the ability to define a function mapping from $A$ to $B$. (We will formalize this more!)

## Computatability

* First let's define the *type* of function we will be talking about here. 


A function $f: \Sigma^* \to \Sigma^*$ is a *computable function* if some turing machine $M$, on every input $w$, halts with just $f(w)$ on its tape.


* E.g. We can show that $m + n$ is a computable function by designing a TM that takes $\langle m, n \rangle$ as input and outputs $m + n$.

* Note: A computable function can be a transformation of a machine description. In other words, a TM can take a string description of a turing machine $M$ as input and return a string description of another machine $M'$.

## Mapping Reducibility

![](../static/slide_figs/mapping-reducibility.png)[^sipser]

Language $A$ is ***mapping reducible*** to language $B$, denoted $A \leq_m B$, if there is a computable function $f: \Sigma^* \to \Sigma^*$, where for every $w$,

$$ w \in A \iff f(w) \in B $$.

The function of $f$ is called the ***reduction*** from $A$ to $B$.

If $A$ is the solution set of one problem, and $B$ is the solution set to another problem, we can convert questions about membership in $A$ to questions about membership in $B$!

## Reducibility + Decidability

If $A \leq_m B$ and $B$ is decidable, then $A$ is decidable.



## Reducibility + Decidability

If $A \leq_m B$ and $B$ is decidable, then $A$ is decidable.


If $A \leq_m B$ and $A$ is undecidable, then $B$ is undecidable.

## Example

Let's again show $HALT_{TM}$ is undecidable by showing $A_{TM}$ can be reduced to $HALT_{TM}$.

Recall: 

$A_{TM} = \{\langle M, w \rangle | M$ is a Turing Machine and accepts $w \}$

$HALT_{TM} = \{\langle M, w \rangle | M$ is a Turing Machine and halts on input $w \}$

## Workspace

## Example

Recall:
    
$E_{TM} =  \{\langle M \rangle | M$ is a Turing Machine and $L(M) \neq \emptyset \}$

and

$EQ_{TM} = \{\langle M_1, M_2 \rangle | M_1$ and $M_2$ are Turing Machines and $L(M_1) = L(M_2) \}$

Let's assume we know $E_{TM}$ is undecidable, and let's use that to show $EQ_{TM}$ is also undecidable.

## Workspace

[^sipser]: Sipser, Michael. "Introduction to the Theory of Computation." ACM Sigact News 27.1 (1996): 27-29.