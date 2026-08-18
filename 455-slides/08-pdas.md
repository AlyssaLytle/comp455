---
# try also 'default' to start simple
theme: seriph
title: Pushdown Automata
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
# Pushdown Automata

---

# Pushdown Automata

DFAs/NFAs are computational models that recognize regular languages. 

Similarly *pushdown automata* are computational models that recognize context-free languages.


<img src="/public/reg-cf-table.png" width="700"/>



---

# Thinking of Finite Automata Differently

First, let's think about DFAs/NFAs a little differently using this representation:

<img src="/public/fa-tape.png" width="300"/>


 
* The control represents the states and transition function, 
* the tape contains the input string, 
* and the arrow represents the input head, pointing at the next input symbol to be read. 

---

# Pushdown Automata

A pushdown automaton is similar in its design, but it includes a *stack* where the automaton can write symbols to read back later. 

Every time a new symbol is written to the stack, the other symbols are *pushed down*.


<img src="/public/pda-tape.png" width="300"/>

(Recall that adding an element to a stack is called *pushing* an element and removing one is called *popping*!)

This design allows us to track things! You can recall that this was a limitation for finite automata, and was the reason they couldn't be used to represent sets such as $\{a^nb^n | n \geq 0\}$.

---

# Using a PDA to Recognize $a^nb^n$ - Example

Abstractly, we can think of a strategy to use the stack to "track" that we have the same amount of $a$s and $b$s.

<v-clicks>

We can use the state structure to maintain the structure of $a$s followed by $b$s.

Every time an $a$ is encountered, push an $A$ counter onto the stack. For every $b$ input encountered, pop an $A$ counter off the stack. At the end of the input string, the stack should be empty.

</v-clicks>



---

# Testing for an Empty Stack

<v-clicks>


We need a way to tell whether or not the stack is empty.

(For this example, that tells us we've seen the same amount of $a$s and $b$s.) 


To know when the stack is empty, we can push a $\$$ in the stack at the beginning. Since a stack is "last in first out", we know that when we see the $\$$ again, we have removed every other item from the stack.

We use an $\varepsilon$-transition from our start state $q_1$ to $q_2$ to allow us to initalize that $\$$ element in the stack. 

</v-clicks>


<!-- Another common convention is to *not* use $\varepsilon$-transitions but instead to just add a ``starting stack symbol'' to the tuple definition, making it a 7-tuple. For this class, let's stick the the former convention of always starting with an empty stack.  -->

---

# Note: Testing for the End of The Input

The way we've discussed acceptance of an input hasn't required knowing where the *end* of an input is. 

We will stick with the assumption that our "machine" recognizes the end of input for now, but it's something to think about...

---


# Using a PDA to Recognize $a^nb^n$ 


<img src="/public/anbn-pda/s1.png" width="400"/>



---


# Using a PDA to Recognize $a^nb^n$ 


<img src="/public/anbn-pda/s2.png" width="400"/>



---


# Using a PDA to Recognize $a^nb^n$ 


<img src="/public/anbn-pda/s3.png" width="400"/>


---


# Using a PDA to Recognize $a^nb^n$ 


<img src="/public/anbn-pda/s4.png" width="400"/>



---


# Using a PDA to Recognize $a^nb^n$ 


<img src="/public/anbn-pda/fn.png" width="400"/>






---

# Pushdown Automaton

    
A *pushdown automaton* is a 6-tuple $(Q, \Sigma, \Gamma, \delta, s, F)$ where

    
* $Q$ is the set of states
* $\Sigma$ is the the input alphabet
* $\Gamma$ is the stack alphabet
* $\delta: Q \times \Sigma_\varepsilon \times \Gamma_\varepsilon \to \mathcal{P}(Q \times \Gamma_\varepsilon)$
* $s \in Q$ is the start state
* $F \subseteq Q$ is the set of accept states
    

<v-clicks>

Where $\Sigma \cup \{\varepsilon\}$ be denoted as $\Sigma_\varepsilon$ and $\Gamma \cup \{\varepsilon\}$ be denoted as $\Gamma_\varepsilon$

and $\mathcal{P}(Q \times \Gamma_\varepsilon)$ is the powerset of $\mathcal{P}(Q \times \Gamma_\varepsilon)$ (aka all possible subsets of $Q \times \Gamma_\varepsilon$).

</v-clicks>





---

# Using a PDA to Recognize $a^nb^n$ (continued)

Define our PDA as $(Q, \Sigma, \Gamma, \delta, s, F)$ where: 

<v-clicks>

* $Q = \{q_1, q_2, q_3, q_4\}$
* $\Sigma = \{a,b\}$ 
* $\Gamma = \{A, \$ \}$ 
* $s = q_1$
* $F = \{q_1, q_4\}$ 

</v-clicks>


---

# Acceptance to a PDA

A PDA $M=(Q, \Sigma, \Gamma, \delta, s, F)$ *accepts* input $w = w_1w_2\ldots w_m$, $w_i \in \Sigma_\varepsilon$ 
if sequences of states 
$r_0,r_1,\ldots,r_m \in Q$ and strings $s_0,s_1,\ldots,s_m \in \Gamma^*$ exist that satisfy the following three conditions:


<v-clicks>

* $r_0 = s$ and $s_0 = \varepsilon$ ($M$ starts out in the start state with an empty stack.)
* For $i = 0, \ldots, m-1$, <br>
    $(r_{i+1}, b) \in \delta(r_i, w_{i+1}, a)$,
    $s_i= at$, and <br>
     $s_{i+1} = bt$ for $a, b \in \Gamma_\varepsilon$ $t \in \Gamma^*$. <br>
     (Given this input string, $M$ moves as expected over both the states and the stack.)
* $r_m \in F$ ($M$ ends in an accept state.)
</v-clicks>


---

# Theorem 

A language is context free if and only if some pushdown automaton recognizes it. 



<img src="/public/cfls-rls.png" width="600"/>


---

# Converting a CFG to a PDA

From a high level:



<v-clicks>

- We can use the idea of *substitution* used by CFGs. In other words, CFGs use variables essentially as intermediate symbols and substitute them using the rules of the grammar until we get to a string of only terminal symbols.

- The PDA will use this same idea. It can push the start symbol on the stack and then:
    - If the top element of the stack is a nonterminal, pop it and push a substitution
    - If the top element of the stack is a terminal, pop it and check if it matches the input string 

</v-clicks>


---

# Converting a CFG to a PDA

1. Place the marker symbol \$ and the start variable on the stack.
2. Repeat the following steps:

<v-clicks>

  a. If the top element in the stack is a nonterminal symbol (e.g. $A$), nondeterministically select one of the rules for $A$ and substitute $A$ by applying this rule. Push that new substution onto the stack.

  b. If the top element in the stack is a terminal symbol (e.g. $a$), read the next symbol from the input to see if it matches $a$. If they match, continue. Otherwise, consider this a reject and try another "branch" of nondeterminism. (Apply a different rule in the previous step.)

  c. If the top of the stack is \$, this means the stack is empty, so transition to the accept state. If the input has all be read, that means that the string is accepted.

</v-clicks>

---

# Converting a CFG to a PDA

$$
\begin{align*}
    S &\to aTb ~|~ b \\
    T & \to Ta ~|~ \varepsilon
\end{align*}$$

<img src="/public/cfg-conversion/s1.png" width="400"/>

---

# Converting a CFG to a PDA

$$
\begin{align*}
    S &\to aTb ~|~ b \\
    T & \to Ta ~|~ \varepsilon
\end{align*}$$

<img src="/public/cfg-conversion/s2.png" width="400"/>

---

# Converting a CFG to a PDA

$$
\begin{align*}
    S &\to aTb ~|~ b \\
    T & \to Ta ~|~ \varepsilon
\end{align*}$$

<img src="/public/cfg-conversion/s3.png" width="400"/>

---

# Converting a CFG to a PDA

$$
\begin{align*}
    S &\to aTb ~|~ b \\
    T & \to Ta ~|~ \varepsilon
\end{align*}$$

<img src="/public/cfg-conversion/s4.png" width="400"/>

---

# Converting a CFG to a PDA

$$
\begin{align*}
    S &\to aTb ~|~ b \\
    T & \to Ta ~|~ \varepsilon
\end{align*}$$

<img src="/public/cfg-conversion/s5.png" width="400"/>

---

# Converting a CFG to a PDA

$$
\begin{align*}
    S &\to aTb ~|~ b \\
    T & \to Ta ~|~ \varepsilon
\end{align*}$$

<img src="/public/cfg-conversion/final.png" width="400"/>