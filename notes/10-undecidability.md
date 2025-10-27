---
title: "Undecidability"
author: "Alyssa Lytle"
date: "October 23, 2025"
---

<!-- pandoc -t slidy -s notes/10-undecidability.md -o slides/10-undecidability.html --webtex -->

# Undecidability

## Undecidability

How do we *prove* that a problem is undecidable? 

The main approach is to focus on one problem that we know to be undecidable which we will call $A_{TM}$, and if we want to prove any other problem is undecidable, we convert (or *reduce*) it to express it as an $A_{TM}$ problem.


## Input Acceptance on A Turing Machine

Previously, we talked about how we can check whether or not other automata accept a string, and how this is decidable. 

However, if we define:

$$A_{TM} = \{\langle M, w \rangle \mid M \textrm{ is a Turing Machine and accepts } w \}$$

$A_{TM}$ is *NOT* decidable. (It *is* Turing-recognizable, though!)

## Proof

## Theorem

A language is decidable iff it is Turing-recognizable *and* its complement is Turing recognizable.




## Reducibility

The primary method used to prove that problems are unsolvable is *reducibility*.

Given two problems $A$ and $B$,
a *reduction* is a way of converting problem $A$ to problem $B$ in such a way that a solution to $B$ can be used to solve $A$. 
If this is the case then you can say "$A$ is reducible to $B$"

## Ramifications of Reducibility

Reducibility has some powerful ramifications.

If $A$ is reducible to $B$ and $B$ is decidable, then that means $A$ is decidable! 

Similarly, if $A$ is reducible to $B$ and $A$ is undecidable, the $B$ is undecidable. 

(This second line of reasoning shows how we will prove the undecidability of other problems.)

## The Halting Problem

Another common question is: "Will the machine *halt* on this input or will it loop forever?"

This can be expressed as:
$$HALT_{TM} = \{\langle M, w \rangle \mid M \textrm{ is a Turing Machine and halts on input } w \}$$

$HALT_{TM}$ is also not Turing-decidable. Let's prove it using the idea of reducibility.

## Proof

## Undecidable Problems

Other common problems can be shown to be undecidable in a similar way.


The following problems are undecidable: 


* $HALT_{TM} = \{\langle M, w \rangle \mid M \textrm{ is a Turing Machine and halts on input } w \}$
* $E_{TM} =  \{\langle M \rangle \mid M \textrm{ is a Turing Machine and } L(M) \neq 0 \}$
* $REGULAR_{TM} = \{\langle M \rangle \mid M \textrm{ is a Turing Machine and } L(M) \textrm{is a regular language} \}$
* $EQ_{TM} = \{\langle M_1, M_2 \rangle \mid M_1 \textrm { and } M_2 \textrm{ are Turing Machines and } L(M_1) = L(M_2) \}$

    



## Reductions via Computation Histories

We've previously talked about *configurations* on Turing machines.

* The *configuration* of the Turing Machine is the current state, tape contents, and head location.

* It is represented as $u q v$ where $q$ is the current state and $uv$ are the current contents of the tape, with the first character of $v$ being the current head location.
    * The *start configuration* on input $w$ would be $sw$.
    * The *accepting configuration* is the configuration that contains the state  $q_{accept}$ 
    * and the *rejecting configuration* is the configuration that contains the state $q_{reject}$

* A Turing machine $M$ *accepts* input $w$ if there are a sequence of configurations that begin at the start configurations and finish in an accepting configuration.

## Computation History 

The computation history of a machine is defined in terms of these configurations.


Let $M$ be a Turing Machine and $w$ an input string.  

An *accepting computation history* for $M$ is a sequence of configurations $C_1, C_2, \ldots, C_l$, where 

* $C_1$ is the start configuration of $M$ on $w$,  
* $C_l$ is an accepting configuration of $M$, 
* and each $C_i$ legally follows from $C_{i-1}$ according to the rules of $M$.

A *rejecting computation history* for $M$ on $w$ is defined similarly, except that $C_l$ is a rejecting configuration. 



## Linear Bounded Automata

A *linear bounded automaton* (LBA) is a type of Turing Machine with a finite memory, determined by the size of the input tape.

The problem of whether or not a string is accepted by an LBA is actually decidable!

$$A_{LBA} = \{ \langle M , w \rangle \mid M \textrm{ is an LBA that accepts string } w\}$$

$A_{LBA}$ is decidable because, since our memory is now finite, there are a finite number of configurations possible over $M$. Therefore, we can bound our machine to stop after a certain number of configurations. 

## Linear Bounded Automata

A *linear bounded automaton* (LBA) is a type of Turing Machine with a finite memory, determined by the size of the input tape.

The problem of whether or not a string is accepted by an LBA is actually decidable!

$$A_{LBA} = \{ \langle M , w \rangle \mid M \textrm{ is an LBA that accepts string } w\}$$

$A_{LBA}$ is decidable because, since our memory is now finite, there are a finite number of configurations possible over $M$. Therefore, we can bound our machine to stop after a certain number of configurations. 

However, what about the question of whether or not an LBA accepts any strings?

$$E_{LBA} = \{ \langle M  \rangle \mid M \textrm{ is an LBA where } L(M) \neq 0 \}$$

This is, in fact, undecidable.

## Proof

