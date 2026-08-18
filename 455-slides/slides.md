---
theme: ../
title: Deterministic Finite Automata
logo: ./unc-logo.png
kicker: COMP 455 · Theory of Computation
layout: cover
---

# Deterministic Finite Automata

An introduction to the simplest machines that compute

---
layout: section
index: "01"
---

# Foundations

---
kicker: Foundations
layout: default
---

## Why Automata Theory?

- Every text editor search and compiler tokenizer runs a finite automaton underneath
- Regular expressions compile down to exactly this kind of machine
- It's the simplest model of computation — the one we can reason about completely

---
kicker: The Formal Definition
layout: two-cols
---

## A Concrete Example

::title::

<p>M1: strings over {0,1} that end in <code>01</code></p>

::left::

<div style="font-family:'Roboto Mono',monospace;font-size:1.5rem;line-height:2;">
Q = {q0, q1, q2}<br/>
&Sigma; = {0, 1}<br/>
q0 = q0<br/>
F = {q2}
</div>

::right::

<p>q1 means "last symbol was 0"<br/>q2 means "last two were 01"</p>

---
kicker: Beyond DFAs
layout: statement
---

# NFAs and DFAs Recognize the Same Languages

Nondeterminism buys convenience, not additional power — every NFA converts to an equivalent DFA via the subset construction.

---
layout: end
---

# Questions?

Next lecture: the subset construction, turning any NFA into a DFA.
