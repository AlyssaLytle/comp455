---
title: "P vs NP"
author: "Alyssa Lytle"
date: "November 6, 2025"
---

<!-- pandoc -t slidy -s notes/13-p-vs-np.md -o slides/13-p-vs-np.html --webtex -->

# P vs NP

## Question: 

What do you know about the "P vs. NP" problem?

## Review 

Let $t: \mathbb{N} \to \mathbb{R}^+$ be a function. Define the *time complexity class*, $\textrm{TIME}(t(n))$, to be the collection of all languages that are decidable by an $O(t(n))$ time Turing Machine. 

P is the class of languages that are decidable in polynomial time on a deterministic single-tape Turing machine. 

In other words, 

$$P = \bigcup_k \textrm{TIME}(n^k).$$ 

P is important because it describes the class of problems that are realistically solvable on a computer.

## Showing a Problem is in P

1. Express our problem as a language $A$
2. Present an Turing machine computable algorithm $M$ that decides $A$
3. Argue the runtime of $M$

## Example

Show $RELPRIME \in P$ where $RELPRIME = \{\langle x,y \rangle \mid x$ and $y$ are relatively prime$\}$.

First, what is our "problem"?

## NP

So now, let's talk about the *other* problems... 

Let's talk about the "solvability" of a problem in a different way. 

Maybe we can't produce an algorithm that solves it in polynomial time, but perhaps we can produce an algorithm that *verifies* it in polynomial time.

In other words, maybe we don't have an algorithm that produces a solution, but we have one that checks if a solution is valid.

A *verifier* for a language $A$ is an algorithm $V$, where

$$A = \{w \mid V \textrm{ accepts } \langle w, c\rangle \textrm{ for some string } c \}$$

A *polynomial time verifier* runs in polynomial time in the length of $w$.

A language $A$ is *polynomially verifiable* if it has a polynomial time verifier.
    
## Example 
Recall 

 $$PATH = \{\langle G, s, t \rangle | G \textrm{ is a directed graph that has a directed path from } s \textrm{ to } t \}$$

We showed that we could build a machine that decides $PATH$ in polynomial time.

If we wanted to build a machine $V$ that *verifies* $PATH$, you could say

$$PATH = \{ \langle G,s,t \rangle \mid V \textrm{ accepts } \langle G,s,t,e\rangle, \textrm{ where } e \textrm{ is a path from } s \textrm{ to } t \textrm{ over } G  \}$$

So $V$ should be able to take graph $G$, nodes $s$ and $t$ and a path/set of edges $e$ and verify that it is $e$ is indeed a set of edges from $G$ that forms a directed path from $s$ to $t$.

## Defining NP

Now that we have this definition of a polynomial time verifier, we can define NP.


NP is the class of languages that have polynomial time verifiers.


## P vs NP

Note that we have discussed how $PATH \in P$ and $PATH \in \textrm{NP}$. In fact, it is true that P $\subseteq$ NP.

In other words, *every problem that can be decided in polynomial time can also be verified in polynomial time*.

What about the reverse? Can every problem that can be verified in polynomial time also be decided in polynomial time? 

This is an open question. If this were true, then it would be the case that NP $\subseteq$ P, and therefore P $=$ NP.

## P vs. NP

![](../static/slide_figs/PvsNP.png)

This figure illustrates the two possibilities this creates. Either P is strictly a subset of NP (meaning there are problems in NP that cannot be decided in polynomial time) or they are the same set. 

## Nondeterministic Polynomial Time + Turing Machines

Where does NP come from?

It's shorthand for *Nondeterministic polynomial time*. 

In fact, any NP problem *could* be decided in polynomial time on a *nondeterministic* Turing machine..


* A language is in NP iff it is decided by some nondeterministic polynomial time Turing machine.




* A nondeterministic Turing Machine is defined the same as a deterministic one, except the transition function is defined as a probability mapping.
$\delta: Q \times \Gamma \to P(Q \times \Gamma \times \{\textrm{L},\textrm{R}\})$



* *Question: It's known that every nondeterministic TM has an equivalent deterministic TM, so why isn't this enough to show P=NP?*

## NTIME

$$\textrm{NTIME}(t(n)) = \{ L \mid  L \textrm{ is a language decided by an O(t(n)) time nondeterministic Turing machine} \}
$$


This allows us to define NP as 
$$\textrm{NP} = \bigcup_k \textrm{NTIME}(n^k) $$


This helps us with the question: how do I argue that a problem is in NP? 

For this, you could either design a nondeterministic turing machine that decides it in polynomial time *or* you can design a deterministic turing machine that verifies it in polynomial time.

## Example 

A clique in an undirected graph is a subgraph where every node is connected by an edge. A $k$-clique is a clique that contains $k$ nodes. 

Let $CLIQUE = \{\langle G, k \rangle | G \textrm{ is an undirected graph with a k-clique}\}$

Show $CLIQUE$ is in NP.



## Example 

Say we have a collection of numbers $S=\{x_1, x_2, \ldots, x_k\}$ and we want to know if a subset of the elements of $S$ can be summed to equal a specific value $t$. For example, can I sum a subset of $\{1,2,3,4\}$ to get $7$?

This is how we define our problem:

$$SUBSETSUM = \{\langle S, t \rangle | S = \{x_1, x_2, \ldots, x_k\}, 
\textrm{and for some } \{y_1, \ldots, y_l\} \subseteq S,
\sum y_i = t \}
$$

Show $SUBSETSUM$ is in NP.
