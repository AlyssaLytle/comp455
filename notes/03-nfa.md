---
title: "Nondeterministic Finite Automata"
author: "Alyssa Lytle"
date: "September 2, 2025"
---

<!-- pandoc -t slidy -s notes/03-nfa.md -o slides/03-nfas.html --webtex -->

# Nondeterministic Finite Automata

## Determinism

"When a machine is in a given state and reads the next input symbol, we know what the next state will be--it is *determined*." [^sipser]

## Nondeterminism

* "A state is not uniquely determined by its current state." - Kozen [^kozen]

* "...the power to be in several states at once." - Hopcroft et al.[^hopcroft]

* "...several  choices may exist for the next state at any point." - Sipser [^sipser]

## Why???

- Represents real-life situations where there's not enough/incomplete/unpredictable/unreliable information about external forces and how they impact the state.

- Can be a useful tool in computation. Some algorithms rely on nondeterminism for more efficient solutions.

- Nondeterministic definitions can be simpler/more concise.

## Nondeterministic Finite Automata

A Nondeterministic Finite Automaton (NFA) has a similar 5-tuple definition as the Deterministic Finite Automata (DFA) we've seen so far: $(Q, \Sigma, \delta, s, F)$, but one element in defined differently.

Thinking of our 5-tuple definition and the definition of nondeterminism, what element do you think is different?

## Nondeterministic Finite Automata

We still have:

- $Q$: A finite set of states 
- $\Sigma$: A finite alphabet
- $F \subseteq Q$: A set of accept states


But we can have a *set* of start states!

Also, $\delta$ is going to behave a little differently because now you can transition to a set of possible states! You also don't *have* to have a transition defined for every state, input combination! 

## Nondeterministic Finite Automata - Formal Definition

A *nondeterministic finite automaton* (NFA) is a five-tuple:

$$N = (Q, \Sigma, \Delta, S, F)$$ 

where

- $Q$: A finite set of states 
- $\Sigma$: A finite alphabet
- $\Delta$: a function $Q \times \Sigma \to 2^Q$
- $S \subseteq Q$: A *set* of start states
- $F \subseteq Q$: A set of accept states

Where $2^Q$ is the *power set* of $Q$. ($\{A \mid A \subseteq Q\}$)


## Example

Draw an NFA over the alphabet $\{0,1\}$ such that it accepts:

$$A = \{w \in \{0,1\}^* \mid \textrm{the second symbol from the right is one.} \} $$

E.g. it accepts $01010$ and $010$ but not $101$ or $11001$.

## What does "acceptance" mean?

<!-- - "An NFA accepts a string $w$ if it is possible to make any sequence of choices of next state, while reading the characters of $w$, and go from the start state to any accepting state." - Hopcroft et al. [^hopcroft] -->

A nondeterministic automaton is said to *accept* its input $w$ if there exists *at least* one computation path on input $w$ from a start state to an accept state.

## Some properties

* Every DFA can be expressed as an NFA. (Reasonable.)

* Every NFA can be expressed as a DFA. (A little more complicated to think about...)

## Every DFA can be expressed as an NFA

Let's take an example DFA from a previous class...

![](../static/slide_figs/fa.png)[^sipser]

## Every NFA can be expressed as an DFA

Let's use our earlier example...



# Sources

[^hopcroft]: - Hopcroft, John E., Rajeev Motwani, and Jeffrey D. Ullman. "Introduction to automata theory, languages, and computation." Acm Sigact News 32.1 (2001): 60-65.

[^kozen]: - Kozen, Dexter C. Automata and computability. Springer Science & Business Media, 2007.

[^sipser]: - Sipser, Michael. "Introduction to the Theory of Computation." ACM Sigact News 27.1 (1996): 27-29