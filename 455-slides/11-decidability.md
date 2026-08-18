---
# try also 'default' to start simple
theme: seriph
title: Decidability
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

# Algorithms and Decidability

This lecture, we're going to talk more about the types of problems we're able to solve with these machines.

---

# Decidability

We have talked about languages + automata and what it means for a language to be *recognized* by an automaton. 

For a Turing Machine, we discuss this in terms of *decidability*.


<v-clicks>

For a language $L$ on machine $M$,

It is **Turing-recognizable** iff it

* Accepts if the input is in $L$
* Rejects *or* loops forever if the input is not in $L$

        
Is is **Turing-decidable** iff it

* Accepts if the input is in $L$
* Rejects if the input is not in $L$


</v-clicks>

---

# Algorithms

<v-clicks>

The main focus of today's lesson is going to be answering the question: how do I know if a *problem* is decidable?

To accomplish this, we do the following:

* Represent the problem we want to solve as a set or "language".
    
* Define a Turing machine that *decides* it. (You can do this by providing an "algorithm" that is essentially the design of your machine rather than designing the machine directly.)

</v-clicks>

---

# Example

<v-clicks>

Say my "problem", is that I want to know if a string is of the form $w\#w$, where $w \in \{0,1\}^*$.

1. We express this problem as a set:

$S_\texttt{double} = \{\langle w\#w \rangle \mid w \in \{0,1\}^*\}$.

(Why did we write $\langle w\#w \rangle$ instead of just $w\#w$? I'll explain soon!)

2. Then, we present a general algorithm design for a Turing Machine that "decides" membership in $S_\texttt{double}$. 
    
(We already did this in our last lecture!)

</v-clicks>

---

# Input Notation

<v-clicks>


Let $\langle A \rangle$ represent the *string representation* of input $A$. 

Since a Turing Machine takes string inputs, we must translate our input into a string representation.

For our previous example, $S_\texttt{double} = \{\langle w\#w \rangle \mid w \in \{0,1\}^*\}$, <br>
writing $\langle w\#w \rangle$ is a little redundant since we already know $w\#w$ is a string. 

But that's not always the case!

</v-clicks>

---
layout: two-cols-header

---

# Input Notation: Example

::left::

<v-clicks>

Say, for example, the problem we are trying to solve is 

"Is there a sequence of paths that touches all vertices in directed graph $G$?"

<img src="/public/DG.png" width="350"/>

To input $G$ in a Turing Machine, we have to represent it as a string.

</v-clicks>

::right::

<v-clicks>



For example, we could encode its vertices in a sequence followed by its edges in a sequence:

$\langle G \rangle = (1,2,3,4)((1,2),(2,3),(3,1),(1,4))$

</v-clicks>



<v-clicks>

So our "problem" could be described as language:

$L = \{ \langle G \rangle \mid$ there exists a path in $G$ that touches all vertices $\}$

Our Turing Machine *accepts* an input graph if such a path exists and *rejects* it otherwise.

</v-clicks>



---

# Decidable Problems + Regular Languages

<v-clicks>

We can prove problem is decidable by defining a TM that decides it!

Let's show that the problem of "whether a string is *accepted* by a DFA" is decidable. 

We do this by building a TM that decides it!

Let 

$A_{DFA} = \{ \langle B, w\rangle \mid B \textrm{ is a DFA that accepts input string } w \}$

For $B$'s string representation, assume we have a string representation of the tuple, $B = (Q, \Sigma, \delta, s, F)$.

</v-clicks>


---

# Decidable Problems + Regular Languages (cont.)

<v-clicks>


Let 

$A_{DFA} = \{ \langle B, w\rangle \mid B \textrm{ is a DFA that accepts input string } w \}$

High-level design of Turing Machine $M$:

1. Simulate $B$ on input $w$
    - Take as input the string representations for $B$ and $w$ and confirm they are in proper format (otherwise reject).
    - Write on the tape to keep track of the changing state of $B$ as we step through $w$. (*Read from the tape to find out the transitions defined in $\delta$.) Continue until we reach the end of $w$.
2. If the simulation ends in an accept state in $B$, *accept*! If it ends in a nonaccepting state in $B$, *reject*! (Determine if the state is in $F$ by reading $F$ from the tape.)

</v-clicks>


---

# Decidable Problems + Regular Languages, Lemmas

<v-clicks>


1. $A_{DFA} = \{ \langle B, w\rangle \mid B \textrm{ is a DFA that accepts input string } w \}$. <br> $A_{DFA}$ is a decidable language.
2. $A_{NFA} = \{ \langle B, w\rangle \mid B \textrm{ is an NFA that accepts input string } w \}$. <br> $A_{NFA}$ is a decidable language.
3. $A_{REX} = \{ \langle B, w\rangle \mid B \textrm{ is a regular expression that generates string } w \}$. <br> $A_{REX}$ is a decidable language.

</v-clicks>


---

# Decidable Problems + Regular Languages, General Acceptance

<v-clicks>

What if we want to check if a DFA accepts *anything*? Is this decidable?

*YES!*

$E_{DFA} = \{\langle A \rangle | A \textrm{ is a DFA and } L(A) \neq \emptyset \}$


* General idea: We can't test all possible strings $w$ because that could be infinite, so let's leverage the fact that the sets of states $Q$ and transitions $\delta$ *are* finite! 

* Starting with the start state, "mark" a state and follow all outgoing transitions. Mark every visited state. Repeat until either all states are marked or all transitions have been followed. If an accept state has been marked, *accept*. Otherwise, *reject*!

</v-clicks>


---

# Decidable Problems + CFLs

$E_{CFG} = \{\langle A \rangle | A \textrm{ is a CFG and } L(G) \neq \emptyset \}$

* General idea: 
    * Similar to the previous example, we can't test all possible strings $w$, but we know we have *finite* rules.
    * What does it mean to generate a string $w$. There has to be a mapping from a start variable to a string of all terminals. 
    * This algorithms works similarly to the previous one, but backwards in a way. Start on all *terminal symbols*, and "mark" them. Mark any variable that has a rule mapping to only marked symbols. Keep going until all variables or all rules have been marked. If the start state has been marked, *accept*. Otherwise, *reject*!

<!-- ---

# Undecidability


<img src="/public/sipser-lang-classes.png" width="550"/> -->


