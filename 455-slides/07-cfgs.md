

---
# try also 'default' to start simple
theme: seriph
title: Context-Free Grammars + Languages
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

# Context-Free Grammars + Languages

---

# CFGs and CFLs

* Just as regular expressions describe regular languages, **context-free grammars describe context-free languages.** 

* The "class" of Context-Free Languages *contains* the set of Regular Languages.

* CFLs are good for describing infinite sets of  strings in a finite way. They are commonly used for describing the syntax of programming languages.

---

# CFG Example


<img src="/public/pl-cfg.png" width="700"/>

---

# Context Free Grammar Definition

A context-free grammar (CFG) is a quadruple

$$G = (N, \Sigma, P, S)$$



where 


* $N$ is a finite set (the *nonterminal* symbols or *variables*)
* $\Sigma$ is a finite set (the *terminal* symbols) dijoint from $N$
* $P$ is a finite subset of $N \times (N \cup \Sigma)^*$ (the *productions* or *rules*), and
* $S \in N$ (the *start symbol*) 



---

# Back to Our Example


<img src="/public/pl-cfg.png" width="400"/>


<v-clicks>

$N$, the nonterminals, would be $\{\texttt{<stmt>}, \texttt{<if-stmt>}   \ldots \texttt{<var>} \}$

$\Sigma$, the terminals, would be  $\{ \textbf{if}, \textbf{then}, <, >, +, \ldots \}$

$P$ is all of the rules defined above.

$S$, the start symbol would be $\texttt{<stmt>}$.

</v-clicks>


---

# Common Conventions

Typically, 

* nonterminals are denoted with capital letters (e.g. $A, B, \ldots$)

* terminals are denoted with lowercase letters (e.g. $a,b, \ldots$) 

* strings in $(N \cup \Sigma)^*$ are denoted using greek letters (e.g. $\alpha, \beta, \gamma, \ldots$)

---

# Common Conventions

Typically, 

* nonterminals are denoted with capital letters (e.g. $A, B, \ldots$)

* terminals are denoted with lowercase letters (e.g. $a,b, \ldots$) 

* strings in $(N \cup \Sigma)^*$ are denoted using greek letters (e.g. $\alpha, \beta, \gamma, \ldots$)

Think of productions/rules kind of like transitions. Instead of a tuple representation like $(A, \alpha)$, they often have an arrow representation $A \rightarrow \alpha$. 

To denote a set of productions with the same left-hand side, instead of listing them 

$A \rightarrow \alpha_1$, $A \rightarrow \alpha_2$, $A \rightarrow \alpha_3$

You use the abbreviation

$A \rightarrow \alpha_1  \mid  \alpha_2  \mid  \alpha_3$


---

# $a^nb^n$

The nonregular set $\{a^nb^n  \mid n \geq 0 \}$ can be represented  as a CFL 

$S \rightarrow aSb  \mid \epsilon$


More specifically, in quadruple form: 
$G = (N, \Sigma, P, S)$, where

    
* $N = \{S\}$
* $\Sigma = \{a,b\}$
* $P = \{S \rightarrow aSb, S \rightarrow \epsilon \}$
    
---

# $a^nb^n$

$S \rightarrow aSb ~|~ \epsilon$

Here's how you would derive the string $a^3b^3$ or $aaabbb$:

| String | Rule Applied |
| --- | --- |
| <span v-click="1"> $S$ </span>| <span v-click="1"> Start Symbol  </span> |
| <span v-click="2"> $aSb$ </span>| <span v-click="2"> Apply $S \to aSb$ </span> |
| <span v-click="3"> $aaSbb$ </span>| <span v-click="3"> Apply $S \to aSb$ </span> |
| <span v-click="4"> $aaaSbbb$ </span>| <span v-click="4"> Apply $S \to aSb$ </span> |
| <span v-click="5"> $aaabbb$ </span>| <span v-click="5"> Apply $S \to \epsilon$ </span> |


---

# $a^nb^n$

$S \rightarrow aSb ~|~ \epsilon$

Here's how you would derive the string $a^3b^3$ or $aaabbb$:

<v-clicks>

The more common way to write this is:


$S \xrightarrow[G]{1} aSb \xrightarrow[G]{1} aaSbb \xrightarrow[G]{1} aaaSbbb \xrightarrow[G]{1} aaabbb$

    
Or
    
$S \xrightarrow[G]{4} aaabbb$
    

In English you'd say "This string is derivable from the start symbol in 4 steps."

</v-clicks>


---

# Sentential Form + Sentence

A string in $(N \cup \Sigma)^*$ derivable from the start symbol $S$ is called a *sentential form*. 

A sentential form is called a *sentence* if it consists only of terminal symbols.  

(In other words, a sentence would be in $\Sigma^*$.)



---

# Derivable Strings

As we showed in the example, 

<v-clicks>

* $\alpha \xrightarrow[G]{1} \beta$ if $\beta$ can be derived from $\alpha$ over one step in the grammar $G$.

<div style="height: 10px;" />

* $\alpha \xrightarrow[G]{n} \beta$ if $\beta$ can be derived from $\alpha$ over $n$ steps in the grammar $G$.


</v-clicks>

Moreover

<v-clicks>

* $\alpha \xrightarrow[G]{*} \beta$ if $\alpha \xrightarrow[G]{n} \beta$ for some $n \geq 0$
</v-clicks>

---

# The Language of a Grammar

This allows us to define the *language* of a grammar in the following way:


The *language of the grammar* $G$ is $\{w \in \Sigma^*  \mid S \xrightarrow[G]{*}w\}$

---
layout: center


---

# How do CFLs Compare to Regular Languages?


<img src="/public/cfls-rls.png" width="700"/>

---

# Converting a DFA into a CFG

There is an easy step-by-step way to convert a DFA $M=(Q,\Sigma,\delta,s,F)$ into a CFG:

<v-clicks>

* For each $q_i \in Q$, make a nonterminal $R_i$
* For all transitions $\delta(q_i, x) = q_j$, add the rule $R_i \rightarrow xR_j$
* If $q_i$ is an accept state, add the rule $R_i \rightarrow \epsilon$
* If $q_0$ is the start state of the machine, make $R_0$ the start variable.

</v-clicks>

---

# Designing CFGs

Now that we understand how to read and interpret the definitions of CFGs to determine what CFL they generate, let's practice generating a CFG given a CFL!

---

# First Design a DFA

If the language you are trying to design a CFG for is also regular, you can first define a DFA that recognizes it and convert that DFA to a CFG!

## Example in Lesson

---

# Union Two Simpler CFGs

## Example

<v-clicks>

Define a CFG that generates $\{a^nb^n \mid n \geq 0\} \cup \{b^na^n \mid n \geq 0\}$

We can define a CFG for $\{a^nb^n \mid n \geq 0\}$:

$$
    \begin{align*}
        S_1 \to aS_1b | \varepsilon
    \end{align*}
$$

and for $\{b^na^n \mid n \geq 0\}$:

$$
\begin{align*}
        S_2 \to bS_2a | \varepsilon
\end{align*}
$$

And then union them:

$$
\begin{align*}
    S &\to S_1 | S_2 \\
    S_1 &\to aS_1b | \varepsilon\\
    S_2 &\to bS_2a | \varepsilon
\end{align*}
$$

</v-clicks>

---


# Make Use of Underlying Patterns + Structures

This tip is a little more general, but just as you saw that certain regular languages present themselves with specific properties in their respective DFAs/NFAs, you'll find some patterns in CFLs!

## Example: Balance Using Middle Variable

$L = \{w \in \{a,b\}^*| w$ is a palindrome $\}$

another way you can say this is

$L = \{w \in \{a,b\}^*| w = w^{\mathcal{R}}\}$

Again, to maintain balance, we want to define our rules off of a middle symbol.

$$
\begin{align*}
    S \to aSa ~|~ bSb ~|~ a ~|~ b ~|~ \varepsilon 
\end{align*}
$$

---


# Make Use of Underlying Patterns + Structures

## Another Example: Underlying Recursion

<v-clicks>

The string $a^ib^{2i}$ can be defined as a recursive function in such a way, with the \verb|+| symbol denoting concatenation:

* Base Case: `f(0) = ""` (empty string)

* Recursive Rule: `f(i) = "a" + f(i-1) + "bb"`
   

This could translate to the following CFG:

$$S  \to aSbb ~|~ \varepsilon$$

</v-clicks>

---

# Make Use of Underlying Patterns + Structures

## Another Example: Counting Characters

<v-clicks>

 $L = \{ w~|~w$ contains at least three  b's $\}$

(You could design a DFA that recognizes this language and convert it to a CFG, and you'd get the grammar below.)

This structure emerges. It lies from the idea that "you must encounter this symbol to advance towards a terminal"

$$
\begin{align*}
    S &\to aS | bT\\
    T &\to aT | bU \\
    U &\to aU | bV \\
    V &\to aV | bV| \varepsilon
\end{align*}
$$

To get to non-terminal $V$, you must encounter exactly three $b$'s. You can also encounter as many $a$'s as you like. Additionally, $V$ allows us to append as many $a$'s and $b$'s as desired, so it can generate any string of that form.


</v-clicks>
---

