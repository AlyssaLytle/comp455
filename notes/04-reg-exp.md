---
title: "Regular Expressions"
author: "Alyssa Lytle"
date: "September 16, 2025"
---

<!-- pandoc -t slidy -s notes/04-reg-exp.md -o slides/04-reg-exp.html --webtex -->

## Patterns


* Let $\Sigma$ be a finite alphabet. A \emph{pattern} is a string of symbols representing a set of strings in $\Sigma^*$


* A string \emph{matches} a pattern $\iff$ it's accepted by that pattern's language. $L(\alpha) = \{x \in \Sigma^* | x \mbox{ matches } \alpha\}$


* The UNIX commmands `grep`, `fgrep`, and `egrep` are basic pattern-matching utilities that use DFA/NFA hybrids in their implementation! \cite{kozen2007automata}

## Atomic Patterns


*  $a$, for each $a \in \Sigma$; $L(a) = \{a\}$
*  $\boldsymbol{\epsilon}$; $L(\boldsymbol{\epsilon}) = \{\epsilon\}$
*  $\boldsymbol{\emptyset}$; $L(\boldsymbol{\emptyset}) = \emptyset$.
*  $\#$ (any symbol in $\Sigma$); $L(\#)=\Sigma$
*  $@$ (any string in $\Sigma^*$); $L(@) = \Sigma^*$

## Compound Patterns

* $L(\alpha \cup \beta)$ (or $L(\alpha + \beta)$) $= L (\alpha) \cup L(\beta)$ 
*  $L(\alpha \cap \beta) =  L (\alpha) \cap L(\beta)$
*  $L(\alpha \circ \beta) = L(\alpha) \circ L(\beta) = \{yz \mid y \in L(\alpha)$ and $z \in L(\beta) \}$
* $L(\sim \alpha) =  \sim L(\alpha) = \Sigma^* - L(\alpha)$
* $L(\alpha^*) = \{x_1 x_2 \ldots x_n \mid n \geq 0$ and $x_i \in L(\alpha), 1 \leq i \leq n = L(\alpha)^*\}$

## Redundant Operators

* $\#$ 
* $\alpha$
* $\cap$
* $\sim$

## Inductive Definition of Patterns

*  $a \in \Sigma$
*  $\boldsymbol{\epsilon}$
*  $\boldsymbol{\emptyset}$
*  $\beta \cup \gamma$
*  $\beta \circ \gamma$
*  $\beta^*$ 

## Inductive Definition of Regular Expressions

Regular expressions are patterns used to represent *languages*.

$R$ is a regular expression if $R$ is 

*  $a \in \Sigma$
*  $\boldsymbol{\epsilon}$
*  $\boldsymbol{\emptyset}$
*  $R_1\cup R_2$ where $R_1$ and $R_2$ are regular expressions
*  $R_1 \circ R_2$ where $R_1$ and $R_2$ are regular expressions
*  $R_1^*$ where $R_1$ is a regular expression

## Regular Expressions and Languages

Let $A \subseteq \Sigma^*$. The following three statements are equivalent:

1.  $A$ is a regular language
2.  $A = L(\alpha)$ for some pattern $\alpha$
3.  $A = L(\alpha)$ for some regular expression $\alpha$

## Proving This...
