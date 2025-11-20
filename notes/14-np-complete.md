---
title: "NP Completeness"
author: "Alyssa Lytle"
date: "November 20, 2025"
---

<!-- pandoc -t slidy -s notes/14-np-complete.md -o slides/14-np-complete.html --webtex -->

# NP Completeness

## Last Class

For the guest lecture, you covered the following topics:


* You reviewed how to show if problem set $A$ is in P and how to show if it is in NP.
* You reviewed the general open question of P vs. NP.
* You did an example of reducing a problem $A$ to $B$ in polynomial time ($A \leq_\textrm{P} B$) to show that $B$ is in $NP$


For this lesson, we're going to explicitly layout the reasoning and process of *polynomial time reduction* (the final bullet point).

## Polynomial Time Reducibility

When discussing decidability, we introduced the concept of reducing one problem to another. 

If we can reduce problem $A$ to problem $B$, we can use a solution for $B$ to solve $A$. 

We also showed how this can be done via a computable function using mapping reduction. 

The idea of *polynomial time mapping reducibility* extends this line of thinking, considering the time (or number of computations) it would take to do this reduction.

## Polynomial Time Computability

This definition is very similar to that of mapping reducibility, but the mapping function must be computed in polynomial time.


A function $f: \Sigma^* \to \Sigma^*$ is a *polynomial time computable function* if some polynomial time Turing machine M exists that halts with just $f(w)$ on its tape, when started on any input $w$. 


Language $A$ is *polynomial time mapping reducible*, or *polynomial time reducible*, to language $B$, written $A \leq_\textrm{P}$ if polynomial time computable function $f: \Sigma^* \to \Sigma^*$ exists, where for every $w$,

$$w \in A \iff f(w) \in B$$

The function $f$ is called the *polynomial time reduction* of $A$ to $B$.


## Reducibility and Membership in P

Also similar to previous lessons, we use this reducibility to show whether something is in $P$.

If $A \leq_\textrm{P} B$ and $B \in P$, then $A \in P$.


## Reducibility and Membership in P

Also similar to previous lessons, we use this reducibility to show whether something is in $P$.

If $A \leq_\textrm{P} B$ and $B \in P$, then $A \in P$.

Proof?

<!-- The reasoning behind this proof is quite straightforward. If $B \in P$, then there exists a polynomial time algorithm $M$ that decides $B$. And if $A \leq_\textrm{P} B$ then there is a polynomial time function $f$ mapping every input to $A$ to an input for $B$. So, you just compute $f(w)$ on every $w$ input into $A$, and then input $f(w)$ into $M$. -->



## NP-Completeness

Previously, we've discussed what the process of proving whether or not P $=$ NP would look like. 

The heart of this lies in the set of *NP-complete* problems. 

If we can show one of these problems is solvable in polynomial time, then all problems in NP would be solvable in polynomial time.


A language $B$ is *NP-Complete* if it satisfies two conditions:

1. $B$ is in NP
2. every $A$ in NP is polynomial time reducible to $B$

## NP-Completeness

Previously, we've discussed what the process of proving whether or not P $=$ NP would look like. 

The heart of this lies in the set of *NP-complete* problems. 

If we can show one of these problems is solvable in polynomial time, then all problems in NP would be solvable in polynomial time.


A language $B$ is *NP-Complete* if it satisfies two conditions:

1. $B$ is in NP
2. every $A$ in NP is polynomial time reducible to $B$


Q: What does it mean if $B$ is NP-Complete AND $B \in P$? 

## Proving NP-Completeness


If $B$ is NP-complete and $B \leq_\textrm{P} C$ for $C$ in NP, then $C$ is NP-complete.

## Proving NP-Completeness


If $B$ is NP-complete and $B \leq_\textrm{P} C$ for $C$ in NP, then $C$ is NP-complete.

Proof?

<!-- This proof is pretty straightforward as well. If $B$ is NP-complete, every $A$ in NP is polynomial time reducible to $B$ ($A \leq_\textrm{P} B$). If $B \leq_\textrm{P} C$, then $B$ is polynomial time reducible to $C$. You can compose polynomial time reductions. E.g. if $A \leq_\textrm{P} B$ and $B \leq_\textrm{P} C$, then $A \leq_\textrm{P} C$. -->

## Common NP-Complete Problems


A common NP-Complete Problem is the satisfiability problem (SAT).

A boolean expression $\phi$ is *satisfiable* if there is an assignment of \texttt{True} and \texttt{False} values such that the expression evaluates to \texttt{True}.

$SAT = \{ \langle \phi \rangle \mid \phi$ is a satisfiable boolean formula $\}$.

The proof that $SAT$ is NP-Complete is a very famous one, written by Stephen Cook and Leonid Levin the the early 1970s.

## Common NP-Complete Problems

A subset of $SAT$ that will prove to be useful is $3SAT$, defined the following way:

$3SAT = \{ \langle \phi \rangle \mid \phi$ is a satisfiable 3cnf-formula $\}$.

Conjunctive normal form is defined as clauses connected by conjunctions $\land$. 

A clause is several literals combined by $\lor$'s. 

A 3cnf-formula has clauses of length 3.

$3SAT$ is also NP-Complete.

## Example


Now, we will show $CLIQUE$ is NP-Complete by showing $3SAT \leq_\textrm{P} CLIQUE$. 

$CLIQUE = \{\langle G, k \rangle \mid G$ is an undirected graph with a $k$-clique $\}$
    
$3SAT = \{ \langle \phi \rangle \mid \phi$ is a satisfiable 3cnf-formula $\}$.


