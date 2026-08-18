---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Nonregular Languages
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


# Nonregular Languages

---

<v-clicks>

We've talked a lot about Regular Languages and how to *prove* they are regular. 

However, what if they're not regular? Can we prove that?

The answer is yes! And that is what we will be talking about!

Specifically, we will use a lemma called The Pumping Lemma, so let's give a motivation for the basic reasoning behind it.

</v-clicks>

---

# An Example

We're going to demonstrate a property that all regular languages have. 

Let's start with the example of the automaton $M$ 

where $L(M) = \{w \in \{0,1\}^* ~|~ w$ starts with $1$ and has odd length $\}$

<img src="/public/pumping-lemma/nfa-start1-odd.png" width="500"/>

---

# Testing an Input

Let's test on input 1

1

<img src="/public/pumping-lemma/nfa-start1-odd.png" width="500"/>

---

# Testing an Input

Let's test on input 1

<span class="text-blue-500">1</span>

<img src="/public/pumping-lemma/nfa-q0-q1.png" width="500"/>

<v-clicks>

Accepted!

</v-clicks>

---

# Testing an Input

Let's test on input 101

101

<img src="/public/pumping-lemma/nfa-start1-odd.png" width="500"/>

---

# Testing an Input

Let's test on input 101

<span class="text-blue-500">1</span>01

<img src="/public/pumping-lemma/nfa-q0-q1.png" width="500"/>

---

# Testing an Input

Let's test on input 101

1<span class="text-blue-500">0</span>1

<img src="/public/pumping-lemma/nfa-q1-q2.png" width="500"/>

---

# Testing an Input

Let's test on input 101

10<span class="text-blue-500">1</span>

<img src="/public/pumping-lemma/nfa-q2-q1.png" width="500"/>


<v-clicks>

Accepted!

</v-clicks>

---

# Testing an Input

Let's test on input 10101

10101

<img src="/public/pumping-lemma/nfa-start1-odd.png" width="500"/>

---

# Testing an Input

Let's test on input 10101

<span class="text-blue-500">1</span>0101

<img src="/public/pumping-lemma/nfa-q0-q1.png" width="500"/>

---

# Testing an Input

Let's test on input 10101

1<span class="text-blue-500">0</span>101

<img src="/public/pumping-lemma/nfa-q1-q2.png" width="500"/>

---

# Testing an Input

Let's test on input 10101

10<span class="text-blue-500">1</span>01

<img src="/public/pumping-lemma/nfa-q2-q1.png" width="500"/>

---


# Testing an Input

Let's test on input 10101

101<span class="text-blue-500">0</span>1

<img src="/public/pumping-lemma/nfa-q1-q2.png" width="500"/>

---

# Testing an Input

Let's test on input 10101

1010<span class="text-blue-500">1</span>

<img src="/public/pumping-lemma/nfa-q2-q1.png" width="500"/>


<v-clicks>

Accepted!

</v-clicks>


---

# Testing an Input

Let's test on input 1010101

1010101

<img src="/public/pumping-lemma/nfa-start1-odd.png" width="500"/>

---

# Testing an Input

Let's test on input 1010101

<span class="text-blue-500">1</span>010101

<img src="/public/pumping-lemma/nfa-q0-q1.png" width="500"/>

---

# Testing an Input

Let's test on input 1010101

1<span class="text-blue-500">0</span>10101

<img src="/public/pumping-lemma/nfa-q1-q2.png" width="500"/>

---

# Testing an Input

Let's test on input 1010101

10<span class="text-blue-500">1</span>0101

<img src="/public/pumping-lemma/nfa-q2-q1.png" width="500"/>

---


# Testing an Input

Let's test on input 1010101

101<span class="text-blue-500">0</span>101

<img src="/public/pumping-lemma/nfa-q1-q2.png" width="500"/>

---

# Testing an Input

Let's test on input 10101

1010<span class="text-blue-500">1</span>01

<img src="/public/pumping-lemma/nfa-q2-q1.png" width="500"/>

---


# Testing an Input

Let's test on input 1010101

10101<span class="text-blue-500">0</span>1

<img src="/public/pumping-lemma/nfa-q1-q2.png" width="500"/>

---

# Testing an Input

Let's test on input 1010101

101010<span class="text-blue-500">1</span>

<img src="/public/pumping-lemma/nfa-q2-q1.png" width="500"/>


<v-clicks>

Accepted!

</v-clicks>

---

# Testing an Input

What can we conclude?

$1(01)^i$ will be accepted for any $i \geq 0$!

<img src="/public/pumping-lemma/nfa.png" width="500"/>

---
layout: two-cols

---

# Cycles

Note that this "cycle" appears.

<img src="/public/pumping-lemma/nfa-cycle.png" width="300"/>

::right::

<v-clicks>

This is the basic idea for the pumping lemma.

$L(M)$ can contain arbitrarily long strings, 

but $M$ has only $3$ states, 

so if the length of an accepted string is $>3$, some states are going to have to be visited twice!

Therefore, this type of "cycle" will appear for any infinite regular language!

*(So, if it doesn't appear, the language isn't regular!)*

</v-clicks>

---

# The Pumping Lemma

The idea of being able to repeat/"pump" (or even delete) a subsection of the input string and still get an accepted string: 

<v-clicks>

If $A$ is a regular language, then there is a number $p$ (the pumping length) where if $s$ is any string in $A$ of length at least $p$, then $s$ may be divided into three pieces, $s = xyz$, satisfying the following conditions: 
    
* for each $i \geq 0$, $xy^iz \in A$

* $|y| > 0$

* $|xy| \leq p$

</v-clicks>

---
layout: two-cols

---

# Back to Our Example

<img src="/public/pumping-lemma/nfa.png" width="300"/>

We chose $s = xyz = 101$, 

with $x = 1$, 

$y =$ <span class="text-blue-500">$01$</span>, and 

$z = \epsilon$. 

::right::

<v-clicks>

* $xyz = 1$ <span class="text-blue-500">$01$</span> 

* $xy^2z = 1$ <span class="text-blue-500">$0101$</span>  ("pump" once)

* $xy^3z = 1$ <span class="text-blue-500">$010101$</span> ("pump" twice)

* $xy^iz = 1$ <span class="text-blue-500">$(01)^i$</span>  ("pump" $i-1$ times)

* $xy^0z = 1$ (delete or "pump" 0 times)

</v-clicks>

<v-clicks>

According to The Pumping Lemma, this should work for *every string* of a certain length accepted by this automaton, so let's try another one.

</v-clicks>

---
layout: two-cols

---

<img src="/public/pumping-lemma/nfa.png" width="300"/>

We chose $s = xyz = 11011$, 

with $x = 11$, 

$y =$ <span class="text-blue-500">$01$</span>, and 

$z = 1$. 

::right::

<v-clicks>

* $xyz = 11$ <span class="text-blue-500">$01$</span> $1$ 

* $xy^2z = 11$ <span class="text-blue-500">$0101$</span> $1$  ("pump" once)

* $xy^3z = 11$ <span class="text-blue-500">$010101$</span> $1$ ("pump" twice)

* $xy^iz = 11$ <span class="text-blue-500">$(01)^i$</span> $1$ ("pump" $i-1$ times)

* $xy^0z = 111$ (delete or "pump" 0 times)

</v-clicks>

---

# Nonregular Languages

Now we can prove a language is *not* regular!

The basic strategy for prove a language is nonregular is to first assume that it *is* regular and then show that it violates the pumping lemma -- a proof by contradiction!

Let's think about this approach from a high level. Say we want to prove a language $A$ is nonregular, we would:

<v-clicks>

1. Assume the language $A$ *is* regular.

2. Choose an input string $s$ that would be accepted  by this language. (Pro tip: Usually it's helpful to make it a string whose length is a multiple of pumping length $p$.)

3. Apply the pumping lemma to $s$ and display where it causes a contradiction ($xy^iz \notin A$).

</v-clicks>

<v-clicks>

Note: You have to show there is *no way* to assign $x$ $y$ and $z$ that satisfies the pumping lemma. <br>
You pick one assignment for $s$, but you must consider all possible ways to break $s$ into $x$ $y$ and $z$! 
</v-clicks>

---

# A Classic Nonregular Language

Let $B = \{a^nb^n \mid n \geq 0 \}$

In other words, it would be the set of strings with a number of $a$s followed by *the same number* of $b$s. 

<v-clicks>

The challenge of this is that is has to *remember* how many $a$s it has seen by the center point and then confirm that it has the same number of $b$s. It has to be able to do this for an *arbitrarily large* string!

(Try building a DFA/NFA to recognize this to convince yourself it's not possible!)

</v-clicks>

---


# Proving $a^nb^n$ is Nonregular

We can express this as a two column proof by contradiction:

| Proof Step | Reasoning |
| --- | --- |
| <span v-click="1"> 1. $B = \{a^nb^n \mid n \geq 0 \}$ is a regular language</span>| <span v-click="1"> Assumption  </span> |
| <span v-click="2"> 2. $\exists s = a^pb^p \in B$ </span>| <span v-click="2"> Definition of $B$ </span> |
| <span v-click="3"> 3. $s$ can be split into $s = xyz$, where for any $i \geq 0$ the string $xy^iz$ is in $B$ </span>| <span v-click="3"> Pumping Lemma </span> |
| <span v-click="4"> 4. It's impossible to split $s$ into $s = xyz$, where $\forall i \geq 0$, $xy^iz$ is in $B$ </span>| <span v-click="4"> Shown Next...</span> |
| <span v-click="5"> $\rightarrow \leftarrow$ </span>| <span v-click="5">Lines 3 and 4 contradict.</span> |

---

# Proving Line 4

Want to prove: it is impossible to split $s$ into $s = xyz$, where for any $i \geq 0$ the string $xy^iz$ is in $B$.

This will be a *proof by cases*.

There are three possible situations we must consider for the assignment of string $y$ in $s=xyz$, and we can see why for each of them $xy^iz \notin B$.

<v-clicks>



Case 1: The string $y$ consists only of $a$s, so $y = a^t = aaa \ldots a$ <br>
 $y$ can't be "deleted" because then there will be more $b$s than $a$s, and "pumping" $y$ (e.g. the string $xy^2z$) would result in more $a$s than $b$s and so is not a member of $B$. 


Case 2: The string $y$ consists only of $b$s, so $y = b^t = bbb \ldots b$ <br>
 This can be shown with the same reasoning as Case 1. 


Case 3: The string $y$ consists of both $a$s and $b$s, so $y = aaaa\ldots bbbb$ <br>
In this case, pumping $y$ (e.g. the string $xy^2z$) may have the same number of $a$s and $b$s, but they will be out of order with some $b$s before $a$s. Hence it is not a member of $B$.

$\square$

</v-clicks>