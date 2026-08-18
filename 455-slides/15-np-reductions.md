---
# try also 'default' to start simple
theme: seriph
title: NP Completeness
info: |
  ## Slides for 455
# 455 Class Slides
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
# duration of the presentation
duration: 35min

---

# NP Completeness

---

# NP-Hard

<v-clicks>

Last class, we talked about NP, and how it represents a seemingly large set of problems, including those in P. 

Our goal is to say something about the *harder* problems--the ones we haven't been able to prove are in P. 

These problems are put in a class called **NP-Hard**. Essentially, these problems are considered the "most difficult" problems, and every problem in NP is *polynomial time reducible* to an NP-Hard problem.

$B$ is ***NP-Hard*** if and only if every $A$ in NP is polynomial time reducible to $B$.


</v-clicks>

---

# Polynomial Time Reducibility

<v-clicks>

When discussing decidability, we introduced the concept of reducing one problem to another. 

If we can reduce problem $A$ to problem $B$, we can use a solution for $B$ to solve $A$. 

We also showed how this can be done via a computable function using mapping reduction. 

The idea of *polynomial time mapping reducibility* extends this line of thinking, considering the time (or number of computations) it would take to do this reduction.

</v-clicks>

---

# Polynomial Time Computability

<v-clicks>

This definition is very similar to that of mapping reducibility, but the mapping function must be computed in polynomial time.


A function $f: \Sigma^* \to \Sigma^*$ is a *polynomial time computable function* if some polynomial time Turing machine M exists that halts with just $f(w)$ on its tape, when started on any input $w$. 


Language $A$ is *polynomial time mapping reducible*, or *polynomial time reducible*, to language $B$, written $A \leq_\textrm{P}$ if polynomial time computable function $f: \Sigma^* \to \Sigma^*$ exists, where for every $w$,

$$w \in A \iff f(w) \in B$$

The function $f$ is called the *polynomial time reduction* of $A$ to $B$.

</v-clicks>



---

# Reducibility and Membership in P

<v-clicks>

Also similar to previous lessons, we use this reducibility to show whether something is in $P$.

If $A \leq_\textrm{P} B$ and $B \in P$, then $A \in P$.

Proof?

The reasoning behind this proof is quite straightforward... 

If $B \in P$, then there exists a polynomial time algorithm $M$ that decides $B$.

And if $A \leq_\textrm{P} B$ then there is a polynomial time function $f$ mapping every input to $A$ to an input for $B$.

So, you just compute $f(w)$ on every $w$ input into $A$, and then input $f(w)$ into $M$. 

</v-clicks>


---

# NP-Completeness

--

<v-clicks>

Previously, we've discussed what the process of proving whether or not P $=$ NP would look like. 

The heart of this lies in the set of *NP-complete* problems. 

If we can show one of these problems is solvable in polynomial time, then all problems in NP would be solvable in polynomial time.


A language $B$ is *NP-Complete* if it satisfies two conditions:

1. $B$ is in NP (verifiable in polynomial time)
2. $B$ is NP-Hard (every $A$ in NP is polynomial time reducible to $B$)

</v-clicks>



<!-- 
Q: What does it mean if $B$ is NP-Complete AND $B \in P$?  -->

---


# Proving NP-Completeness

--

<v-clicks>

If $B$ is NP-complete and $B \leq_\textrm{P} C$ for $C$ in NP, then $C$ is NP-complete.

Proof?

This proof is pretty straightforward as well. 

If $B$ is NP-complete, every $A$ in NP is polynomial time reducible to $B$ ($A \leq_\textrm{P} B$). 

If $B \leq_\textrm{P} C$, then $B$ is polynomial time reducible to $C$. 

You can compose polynomial time reductions. E.g. if $A \leq_\textrm{P} B$ and $B \leq_\textrm{P} C$, then $A \leq_\textrm{P} C$.

</v-clicks>

---

# Common NP-Complete Problems

--

<v-clicks>


A common NP-Complete Problem is the satisfiability problem (SAT).

A boolean expression $\phi$ is *satisfiable* if there is an assignment of $\texttt{True}$ and $\texttt{False}$ values such that the expression evaluates to $\texttt{True}$.

$SAT = \{ \langle \phi \rangle \mid \phi$ is a satisfiable boolean formula $\}$.

The proof that $SAT$ is NP-Complete is a very famous one, written by Stephen Cook and Leonid Levin the the early 1970s.

</v-clicks>

---

# Common NP-Complete Problems

<v-clicks>

A subset of $SAT$ that will prove to be useful is $3SAT$, defined the following way:

$3SAT = \{ \langle \phi \rangle \mid \phi$ is a satisfiable 3cnf-formula $\}$.

Conjunctive normal form is defined as clauses connected by conjunctions $\land$. 

A clause is several literals combined by $\lor$'s. 

$$(x_1 \lor x_2 \lor \neg x_3) \land (x_3 \lor x_5) \land (\neg x_1 \lor x_2)$$

A 3cnf-formula has clauses of length 3.

$$(x_1 \lor x_2 \lor \neg x_3) \land (x_3 \lor x_5 \lor x_6) \land (\neg x_1 \lor x_2 \lor x_4)$$

$3SAT$ is also NP-Complete.

</v-clicks>

---

# Example

We will prove $\mathit{CLIQUE}$ is NP-Complete.

<v-clicks>

We already showed that $\mathit{CLIQUE} \in \textrm{NP}$, so we just need to show that it is also NP-Hard. 

We will do this  by showing $3SAT \leq_\textrm{P} CLIQUE$. 

$CLIQUE = \{\langle G, k \rangle \mid G$ is an undirected graph with a $k$-clique $\}$
    
$3SAT = \{ \langle \phi \rangle \mid \phi$ is a satisfiable 3cnf-formula $\}$.

The main idea is that, in polynomial time, we will convert a 3cnf-formula $\phi$ into a graph. 


Remember that the main goal is, on input $\langle \phi \rangle$, produce an output $f(\langle \phi \rangle) = \langle G, k \rangle$ such that

$\langle \phi \rangle \in 3SAT \iff \langle G, k \rangle \in CLIQUE$.


</v-clicks>

---

# Example Continued

<v-clicks>

Let's generalize $\phi$ to

$$\phi = (a_1 \lor b_1 \lor c_1) \land (a_2 \lor b_2 \lor c_2) \land \ldots \land (a_k \lor b_k \lor c_k)$$

Every literal in $\phi$ will be a node on the graph.

We need at least one literal to be $\texttt{True}$ in each clause.

Draw an edge between every literal/node except for ones in the same clause and ones that conflict.

For $k$ clauses, we need to know there is a non-conflicting assignment of at least one element from each clause, which would be a k-clique! All nodes in the k-clique could be assigned $\texttt{True}$ and it would result in $\phi$ evaluating to $\texttt{True}$. So, that would mean that $\phi$ is satisfiable!

</v-clicks>

---

# As an Algorithm

--

<v-clicks>

On input $\langle \phi \rangle$,
1. Create a graph $G$ by making every literal in $\phi$ a node.
2. For every literal in $\phi$, add an edge between every literal/node except for ones in the same clause or ones that conflict. 
3. Output $\langle G, k \rangle$ where $k$ is the number of clauses in $\phi$

In terms of runtime, we could argue that this is polynomial in the length of $\phi = n$, 
then step 1 takes $n$ operations, step 2 takes less than $n^2$ operations and step 3 is just one operation, so overall our algorithm would be in $n^2 + n + 1  = O(n^2)$ time.

</v-clicks>