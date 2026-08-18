---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Regular Expressions
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

# Regular Expressions

---

# Patterns


* Let $\Sigma$ be a finite alphabet. A *pattern* is a string of symbols representing a set of strings in $\Sigma^*$


* A string *matches* a pattern $\iff$ it's accepted by that pattern's language. $L(\alpha) = \{x \in \Sigma^* | x$ matches $\alpha\}$


* The UNIX commmands `grep`, `fgrep`, and `egrep` are basic pattern-matching utilities that use DFA/NFA hybrids in their implementation! 

---

# Atomic Patterns


<v-clicks>

*  $a$, for each $a \in \Sigma$; $L(a) = \{a\}$
*  $\boldsymbol{\epsilon}$; $L(\boldsymbol{\epsilon}) = \{\epsilon\}$
*  $\boldsymbol{\emptyset}$; $L(\boldsymbol{\emptyset}) = \emptyset$.
*  $\#$ (any symbol in $\Sigma$); $L(\#)=\Sigma$
*  $@$ (any string in $\Sigma^*$); $L(@) = \Sigma^*$
</v-clicks>

---

# Compound Patterns

<v-clicks>

* $L(\alpha \cup \beta)$ (or $L(\alpha + \beta)$) $= L (\alpha) \cup L(\beta)$ 
*  $L(\alpha \cap \beta) =  L (\alpha) \cap L(\beta)$
*  $L(\alpha \circ \beta) = L(\alpha) \circ L(\beta) = \{yz \mid y \in L(\alpha)$ and $z \in L(\beta) \}$
* $L(\sim \alpha) =  \sim L(\alpha) = \Sigma^* - L(\alpha)$
* $L(\alpha^*) = \{x_1 x_2 \ldots x_n \mid n \geq 0$ and $x_i \in L(\alpha), 1 \leq i \leq n = L(\alpha)^*\}$
</v-clicks>

---

# Redundant Operators

* $\#$ 
* $@$
* $\cap$
* $\sim$

---

# Inductive Definition of Patterns



*  $a \in \Sigma$
*  $\boldsymbol{\epsilon}$
*  $\boldsymbol{\emptyset}$
*  $\beta \cup \gamma$
*  $\beta \circ \gamma$
*  $\beta^*$ 


---

# Inductive Definition of Regular Expressions


Regular expressions are patterns used to represent *languages*.

$R$ is a regular expression if $R$ is 

*  $a \in \Sigma$
*  $\boldsymbol{\epsilon}$
*  $\boldsymbol{\emptyset}$
*  $R_1\cup R_2$ where $R_1$ and $R_2$ are regular expressions
*  $R_1 \circ R_2$ where $R_1$ and $R_2$ are regular expressions
*  $R_1^*$ where $R_1$ is a regular expression


---

# Examples

| Regular Expression | Language |
| --- | --- |
| <span v-click="1"> $ab \cup ba$ </span>| <span v-click="1"> $\{ab,ba\}$ </span> |
| <span v-click="2"> $a\circ b$ </span>| <span v-click="2"> $\{ab\}$ </span> |
| <span v-click="3"> $a^*$ </span>| <span v-click="3"> $\{\epsilon, a, aa, aaa, \ldots\}$ </span> |
| <span v-click="4"> $(ab)^*$ </span>| <span v-click="4"> $\{\epsilon, ab, abab, ababab, \ldots\}$ </span> |
| <span v-click="5"> $a^* b^*$ </span>| <span v-click="5"> Any string of all $a$s followed by all $b$s </span> |
| <span v-click="6"> $(a \cup b)^*$ </span>| <span v-click="6"> Every string over $\{a,b\} (so, $\Sigma^*$) </span> |
| <span v-click="7"> $a^* \cup b^*$ </span>| <span v-click="7"> Every string of either all $a$s or all $b$s </span> |
| <span v-click="8"> $(ab \cup ba)^*$ </span>| <span v-click="8"> Every combination of $ab$s and $ba$s, $\{\epsilon, ab, abab, abba, baab, \ldots\}$ </span> |




---

# Regular Expressions and Languages

<v-clicks>

Let $A \subseteq \Sigma^*$. 

$A$ is a regular language
$\iff$
$A = L(\alpha)$ for some regular expression $\alpha$

Main conclusion: equally as "powerful" as DFAs + NFAs!
</v-clicks>


