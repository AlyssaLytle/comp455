---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: DFAs
info: |
  ## Slides for 455
# 455 Class Slides
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
# duration of the presentation
duration: 35min
---

<!-- NOTE: Add starting slides from NFA to this one! -->

<!-- pandoc -t slidy -s notes/01-fa.md -o slides/03-finite-automata.html --webtex -->
<!-- pandoc -s notes/01-fa.md -o pdfs/03-finite-automata.tex -->

# Finite Automata and Regular Languages

---

# Finite Automaton: An Example

Our example: an automatic door


<img src="/public/auto-door.png" width="400"/>

Front pad: detect person to walk through

Rear pad: Confirm person has passed through, don't hit other person standing there




---

# Rules of Operation

|        | Front | Rear | Both | Neither |
| --- | :---: | :---: | :---: | :---: |
| **Closed** | <span v-click="1">Open</span> | <span v-click="2">Closed</span>  | <span v-click="3">Closed</span>  | <span v-click="4">Closed</span>  |
| **Open** | <span v-click="5">Open</span>  | <span v-click="6">Open</span>  | <span v-click="7">Open</span>  | <span v-click="8">Closed</span>  |


<div v-click="9">

This is called a **state transition table**.

**Closed** and **Open** are states. 

They take Front, Rear, Both, and Neither as *inputs* to tell them what next-state to transition to.
</div>

---

<!-- # State Diagram

<!-- <img src="/public/auto-door.png" width="400"/> -->
![](/public/autodoor-informal.png)


This is called a state diagram.



--- -->

# Formal Definition



A finite automaton can be expressed as 5-tuple $(Q, \Sigma, \delta, s, F)$ where:

<v-clicks>

- $Q$: A finite set of states 
- $\Sigma$: A finite alphabet
- $\delta: Q \times \Sigma \to Q$: A transition function
- $s \in Q$: A start state
- $F \subseteq Q$: A set of accept states

</v-clicks>

---
layout: two-cols


---

# So If We're Being Technical About It...

(Which we are!)

- $Q: \{Open, Closed\}$ 
- $\Sigma: \{Front, Rear, Both, Neither\}$
- $\delta: Q \times \Sigma \to Q: \textrm{Our transition table}$
- $s \in Q: Closed$
- $F \subseteq Q: \{Open, Closed\}$

::right::


<div class="pt-20">
<v-clicks>

In the transition table, denote a start state with $\rightarrow$ and accept states with $*$.


|        | Front | Rear | Both | Neither |
| --- | :---: | :---: | :---: | :---: |
| $\rightarrow$ **Closed** $*$ | Open | Closed | Closed | Closed |
| **Open** $*$| Open | Open | Open | Closed |

</v-clicks>
</div>

---
layout: two-cols


---

# Getting More Comfortable with $\delta$...


- $\delta: Q \times \Sigma \to Q: \textrm{Our transition table}$





|        | Front | Rear | Both | Neither |
| --- | :---: | :---: | :---: | :---: |
| $\rightarrow$ **Closed** $*$ | Open | Closed | Closed | Closed |
| **Open** $*$| Open | Open | Open | Closed |

::right::


<div class="pt-20">
<v-clicks>

- $\delta$ maps from one state + input to a new state.
- $\delta(Closed, Rear) = Closed$ 
- $\delta(Open, Front) = Open$
- $\delta(Open, Neither) = Closed$

</v-clicks>
</div>

---

# State Diagrams

A state diagram can be used as an alternative to a transition table to represent a finite automaton.

![](/public/formal-door.png)

- $Q: \{Open, Closed\}$ 
- $\Sigma: \{Front, Rear, Both, Neither\}$
- $\delta: Q \times \Sigma \to Q: \textrm{Shown in state diagram}$
- $s \in Q: Closed$
- $F \subseteq Q: \{Open, Closed\}$

---

# The Language of the Machine

For our machine $M$,
The *language* of our machine $L(M)$ is the set of all string inputs that $M$ accepts... 


![](/public/formal-door.png)



E.g. $\{\epsilon, Front, FrontRear, FrontRearFront, RearBoth, ...\}$

$M$ accepts or *recognizes* a string if it terminates in an accept state.

(This isn't the best example because this door accepts all input strings, so let's try another one!)

---
layout: two-cols


---

# Another Example

Let $M$ be:

<img src="/public/fa.png" width="400"/>

::right::

What are $(Q, \Sigma, \delta,s, F)$?

<v-clicks>

- $Q: \{q_1, q_2\}$ 
- $\Sigma: \{0, 1\}$
- $\delta: Q \times \Sigma \to Q: \textrm{Shown in state diagram}$
- $s: q_1$
- $F: \{q_2\}$

</v-clicks>

---

---
layout: two-cols


---

# Finding the Language of $M$

Let $M$ be:

<img src="/public/fa.png" width="400"/>

::right::

What is $L(M)$?

Let's consider which possible input strings end in an accept state...

<v-clicks>

- $0$ - No
- $1$ - Yes
- $01$ - Yes
- $00$ - No
- $010$ - No
- $011$ - Yes
- $0111$ - Yes



</v-clicks>

<div v-click="8">

$L(M)$ is the set of all strings that end with $1$!
</div>

<div v-click="9">

$L(M) = \{w ~|~ w \textbf{ ends with } 1\}$ 
</div> 

---



# Formal Definition of Computation

Let $M = (Q, \Sigma, \delta,s, F)$ 

Let $w = w_1w_2\ldots w_n$ be a string where each $w_i$ is a member of the alphabet $\Sigma$

$M$ accepts $w$ if there exists a sequence of *states* $r_1, r_2, \ldots, r_n$ such that:

<v-clicks>

1. $r_0 = s$
2. $\delta(r_i,w_{i+1})= r_{i+1}$ for $i = 0,\ldots,n-1$, and
3. $r_n \in F$

</v-clicks>

---

# A Regular Language

A language is a *regular language* if there exists a finite automaton that recognizes it.

<v-clicks>
Example:

We now know $L(M) = \{w ~|~ w \textbf{ ends with } 1\}$ is a regular language!
</v-clicks>

---

# Language Operations

- Union: $A \cup B = \{x| x\in A \textrm{ or } x \in B\}$ 

- Concatenation: $A \circ B = \{xy| x \in A \textrm{ and } y \in B\}$

- Star: $A^* = \{x_1 x_2 \ldots x_k | k \geq 0 \textrm{ and each } x_i \in A \}$



---

# Language Operations Example

Let $\Sigma$ be the standard English alphabet

If $A = \{\textrm{good}, \textrm{bad}\}$
$B= \{\textrm{cat}, \textrm{dog}\}$


<v-clicks>

- $A \cup B = \{\textrm{good}, \textrm{bad}, \textrm{cat}, \textrm{dog}\}$

- $A \circ B = \{\textrm{goodcat}, \textrm{badcat}, \textrm{gooddog}, \textrm{baddog}\}$

- $A^* = \{"", \textrm{good}, \textrm{bad}, \textrm{goodgood}, \textrm{goodbad}, \ldots \}$


- Other * usage example:

  $L(M) = \{w  ~|~ w \textbf{ ends with } 1\}$  

  becomes

  $L(M) = \{w \in \{0,1\}^* ~|~ w \textbf{ ends with } 1\}$ 

</v-clicks>



---

# Practice [^hopcroft]

Let 

$$ L = \{w | w \textrm{ is of even length and begins with } 01 \}$$

Prove $L$ is a regular language.

---

# Practice

Let us design a DFA to accept the language:

$$ L = \{w | w \textrm{ is of even length and begins with } 01 \}$$

What we need to track:

* Whether it starts with 01
* Whether the input length is even

---

<!-- ---

# Gumball Machine Problem
    Design a DFA that represents a gumball machine with the following properties:

    * It takes nickels and dimes as inputs
    * If it receives 15 cents total, it dispenses a gumball
    * If it receives more than 15 cents, it dispenses a gumball and change


    Think of an "accept" state as one where a gumball is dispensed.

    (It's ok if your solution doesn't look quite like your neighbor's! There are multiple correct answers! We're going to compare!)

---

# Gumball Machine Solutions -->