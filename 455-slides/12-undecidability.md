---
# try also 'default' to start simple
theme: seriph
title: Undecidability
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

# Undecidability


---

# Undecidability




How do we *prove* that a problem is *not* decidable, or **undecidable**? 

The main approach: Convert (or *reduce*) the problem to a known undecidable problem.

Today: 
<v-clicks>

- Prove $A_{TM}$ is undecidable, making it our first "known undecidable problem"

- Demonstrate how we can reduce $HALT_{TM}$ to this problem, showing $HALT_{TM}$ is also undecidable.

- Formally define the two types of reducibility.

- Do another reduction example.

- Rice's Theorem

</v-clicks>



---

# Input Acceptance on A Turing Machine

<v-clicks>

Previously, we talked about how we can check whether or not other automata accept a string, and how this is decidable. 

However, if we define:

$$A_{TM} = \{\langle M, w \rangle \mid M \textrm{ is a Turing Machine and accepts } w \}$$

$A_{TM}$ is *NOT* decidable. (It *is* Turing-recognizable, though!)

There are two common approaches to the proof of this idea, but they address this question: <br>
If $A_{TM}$ *is* decidable, then there must exist a Turing machine $H$ that takes $\langle M, w \rangle$ as input and decides it. <br> However, since $M$ is *any* Turing Machine, what happens if the machine takes *itself* as input?

</v-clicks>

---

# Proof

---

# Theorem

The type of reasoning used in this proof provides intuition for the following Theorem:

A language is decidable iff it is Turing-recognizable *and* its complement is Turing recognizable.




---

# Reducibility

<v-clicks>

The primary method used to prove that problems are unsolvable is *reducibility*.

Given two problems $A$ and $B$,
a *reduction* is a way of converting problem $A$ to problem $B$ in such a way that a solution to $B$ can be used to solve $A$. 
If this is the case then you can say "$A$ is reducible to $B$"


## Ramifications of Reducibility

Reducibility has some powerful ramifications.

If $A$ is reducible to $B$ and $B$ is decidable, then that means $A$ is decidable! 

<span v-mark="{color: 'orange', type: 'underline' }">Similarly, if $A$ is reducible to $B$ and $A$ is undecidable, then $B$ is undecidable. </span>

(This second line of reasoning shows how we will prove the undecidability of other problems.)

</v-clicks>

---

# Proof Approach

<v-clicks>

This will be a proof by contradiction. 

Say we know $A$ is undecidable. 

We are trying to prove the $B$ is undecidable. 

* Assume $B$ *is* decidable. (Assume we have a TM that decides $B$.)
* Demonstrate that $A$ is reducible to $B$.
* Therefore $A$ must be decidable. However, we already know $A$ is undecidable, so we reach a contradiction.

</v-clicks>

---

# Example: The Halting Problem

<v-clicks>

Another common question is: "Will a Turing machine *halt* on this input or will it loop forever?"

This can be expressed as:
$$HALT_{TM} = \{\langle M, w \rangle \mid M \textrm{ is a Turing Machine and halts on input } w \}$$

$HALT_{TM}$ is also not Turing-decidable. Let's prove it using the idea of reducibility.

</v-clicks>

---

# Proof



---

# Types of Reducibility


<v-clicks>

There are two main ways to demonstrate reducibility.

If we know $A$ is undecidable and we want to reduce $A$ to $B$ to show that $B$ is undecidable, we can use:

* Turing Reducibility: using a decider for $B$ to decide $A$

* Mapping Reducibility: showing that every possible input to $A$ can be converted to an input to $B$'s decider

</v-clicks>


---

# Computatability

<v-clicks>

* First let's define the *type* of function we will be talking about here. 


A function $f: \Sigma^* \to \Sigma^*$ is a *computable function* if some turing machine $M$, on every input $w$, halts with just $f(w)$ on its tape.


* E.g. We can show that $m + n$ is a computable function by designing a TM that takes $\langle m, n \rangle$ as input and outputs $m + n$.

* Note: A computable function can be a transformation of a machine description. In other words, a TM can take a string description of a turing machine $M$ as input and return a string description of another machine $M'$.

</v-clicks>

---
layout: two-cols-header

---

# Mapping Reducibility

::left::

<img src="/public/mapping-reducibility.png" width="350"/>

::right::

<v-clicks>

Language $A$ is ***mapping reducible*** to language $B$, denoted $A \leq_m B$, if there is a computable function<br> $f: \Sigma^* \to \Sigma^*$, where for every $w$,

$w \in A \iff f(w) \in B$

The function of $f$ is called the ***reduction*** from $A$ to $B$.

If $A$ is the solution set of one problem, and $B$ is the solution set to another problem, we can convert questions about membership in $A$ to questions about membership in $B$!

</v-clicks>

---


# Example

Let's again show $HALT_{TM}$ is undecidable by showing $A_{TM}$ can be reduced to $HALT_{TM}$.

Recall: 

$A_{TM} = \{\langle M, w \rangle | M$ is a Turing Machine and accepts $w \}$

$HALT_{TM} = \{\langle M, w \rangle | M$ is a Turing Machine and halts on input $w \}$

---

# Proof

---

# Example

Recall:
    
$E_{TM} =  \{\langle M \rangle | M$ is a Turing Machine and $L(M) = \emptyset \}$

and

$EQ_{TM} = \{\langle M_1, M_2 \rangle | M_1$ and $M_2$ are Turing Machines and $L(M_1) = L(M_2) \}$

Let's assume we know $E_{TM}$ is undecidable, and let's use that to show $EQ_{TM}$ is also undecidable.

---

# Proof


---


# Properties Over Turing Machines

<v-clicks>

You may sense that there is a pattern emerging with basic languages defined over Turing Machines. 

In fact, there are many languages that describe a property over Turing Machines that are undecidable, including:
 
* $A_\textrm{TM} = \{ \langle M, w \rangle ~\mid~ M$  is a TM and $M$ accepts $w$ $\}$
* $\textit{HALT}_\textrm{TM} = \{ \langle M, w \rangle ~|~ M$ is a TM and $M$ halts on input $w$} $\}$
* $\textit{NE}_\textrm{TM} = \{ \langle M \rangle ~|~ M$ is a TM and  $L(M) \neq \emptyset \}$
* $\textit{E}_\textrm{TM} = \{ \langle M \rangle ~|~ M$ is a TM and $L(M) = \emptyset \}$
*  $\textit{REGULAR}_\textrm{TM} = \{ \langle M \rangle ~|~$$M$ is a TM and $L(M)$ is a regular language.}\}$


Can we generalize this by essentially saying *all* of these problems and more are reducible to $A_{\textrm{TM}}$?

Yes!

</v-clicks>

---
layout: two-cols-header


---

# Reducing From $A_{TM}$

::left::

<v-clicks>

$L_P = \{\langle M\rangle \mid L(M) \in P\}$ ($P$ non-trivial + semantic)

$A_\textrm{TM} = \{ \langle M, w \rangle ~\mid~ M$  is a TM and $M$ accepts $w$ $\}$

The following TM must exist: $T_{y}$ with $L(T_{y}) \in P$


So we can map input $\langle M, w \rangle$ to the following TM $\langle F \rangle$:
 

$$
\begin{align*}
        F = &\textrm{ ``On input } \langle M \rangle:\\
        & 1. \textrm{ Run $M$ on $w$. } \\
        & 2. \textrm{ If $M$ accepts, run $T_{y}$ on $x$.}\\
        & 3. \textrm{ If $T_{y}$ accepts, \emph{accept}. Else (if $T_{y}$ rejects), \emph{reject}.''}
    \end{align*}
$$

</v-clicks>

::right::

<v-clicks>

Let's check!

$\langle M,w \rangle \in A_\textrm{TM}$ <br> $\iff$ <br> $f(\langle M,w \rangle ) = \langle F \rangle \in L_P$

If $M$ accepts $w$: $L(F) = L(T_{y}) \in P$, so $\langle F\rangle \in L_P$.


If $M$ doesn't accept $w$: $L(F) = \emptyset \notin P$, so $\langle F\rangle \notin L_P$.

</v-clicks>

---

# Rice's Theorem

--

<v-clicks>

Rice's theorem says: if $P$ is non-trivial (neither empty nor all strings) and semantic (depends only on $L(M)$, not on how $M$ is coded), then $L_P$ is undecidable.

## When This Doesn't Apply

* "Does $M$ have at least 5 states?" 
* "Does $M$ ever move its head left on input $w$?"
* "$\text{HALT}_{\text{TM}}$" itself — "does $M$ halt on $w$?" is not a property of the language $L(M)$

*Rice's theorem only applies when you're asking about what the machine computes, not how it computes it!*

</v-clicks>