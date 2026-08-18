---
# try also 'default' to start simple
theme: seriph
title: Non-CFLs
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

# Non-Context Free Languages + The Pumping Lemma

---
layout: two-cols-header

---
# Non-Context Free Languages 

We can use a modified version of the pumping lemma to prove a language is not context free:

If $A$ is a context-free language, then there is a number $p$ (the pumping length) where, if $s$ is any string in $A$ of length $\geq p$, then $s$ may be divided into $s = uvxyz$ satisfying these conditions:

::left::


<img src="/public/parse-tree-pumping-lemma.png" width="400"/>


::right::

<v-clicks>

* $|vy| > 0$ (at least one of $v$ or $y$ is not the empty string $\epsilon$)
* $|vxy| \leq p$
* for each $i \geq 0$, $uv^ixy^iz \in A$
</v-clicks>

---

# Example: $a^nb^nc^n$

The basic outline of the proof is the same as our previous pumping lemma proofs:

| Proof Step | Reasoning |
| --- | --- |
| <span v-click="1"> 1. $B = \{a^nb^nc^n \mid n \geq 0 \}$ is a context free language</span>| <span v-click="1"> Assumption  </span> |
| <span v-click="2"> 2. $\exists s = a^pb^pc^p \in B$ </span>| <span v-click="2"> Definition of $B$ </span> |
| <span v-click="3"> 3. $s$ can be split into $s = uvxyz$, where for any $i \geq 0$, $uv^ixy^iz$ is in $B$ </span>| <span v-click="3"> Pumping Lemma </span> |
| <span v-click="4"> 4. It's impossible to split $s$ into $s = uvxyz$, where $\forall i \geq 0$, $uv^ixy^iz \in B$ </span>| <span v-click="4"> Shown Next...</span> |
| <span v-click="5"> $\rightarrow \leftarrow$ </span>| <span v-click="5">Lines 3 and 4 contradict.</span> |


---

# Proving Line 4

We have to consider all ways to assign $u,v,x,y,z$. 

<v-clicks>

We can focus specifically at how we'd assign $v$ and $y$

There are two main cases we consider:

* Case 1: Either string ($v$ or $y$) could be a string of two characters (e.g. $a^j b^k$)

* Case 2: Either string ($v$ or $y$) could be a single repeating character (e.g. $a^j$)


Note: With cases involving "either" string, you still have to address what the *other* string could be assigned.

</v-clicks>

---

# Proving Line 4: Case 1

Case 1: Either string ($v$ or $y$) could be a string of two characters 


<v-clicks>


Say for example, $v=aa \ldots ab \ldots bb$.

If we "pump" $v$ once, we would get a string of the form 
$aa \ldots abb \ldots bb aa \ldots abb \ldots bb cc \ldots c$,  

so it would not be of the form $a^n b^n c^n$. $\checkmark$

In this case, it does not matter what the "other" string (in this example $y$) is assigned because the characters of the substring would be out of order regardless.

</v-clicks>

---

# Proving Line 4: Case 2

Case 2: Either string ($v$ or $y$) could be a single repeating character (e.g. $a^j$)


<v-clicks>


Say for example, $v=aa \ldots a$ and $y = \varepsilon$

If we "pump" $v$ and $y$ once, we get more $a$s than $b$s and $c$s, 

so the string would no longer be of the form $a^n b^n c^n$. $\checkmark$

But what if $y \neq \varepsilon$?

We know it wouldn't work if $y$ was a string of two characters (case 1), but we must consider when both $v$ and $y$ are single repeating characters...

</v-clicks>

---

# Proving Line 4: Case 2

<v-clicks>

Updated cases:

Case 1: Either string ($v$ or $y$) could be a string of two characters $\checkmark$

Case 2 (updated): Either string ($v$ or $y$) could be a single repeating character (e.g. $a^j$) *but not both* $\checkmark$

Case 3: Both strings ($v$ and $y$) are single repeating characters.

</v-clicks>

---

# Proving Line 4: Case 3

Case 3: Both strings ($v$ and $y$) are single repeating characters.

<v-clicks>

$v$ and $y$ could be the same repeating character or different repeating characters, so we must consider both cases.

Say for example, $v=aa \ldots a$ and $y = aa \ldots a$

If we "pump" $v$ and $y$ once, we get more $a$s than $b$s and $c$s, 

so the string would no longer be of the form $a^n b^n c^n$. $\checkmark$

If they were different characters, say $v=aa \ldots a$ and $y = bb \ldots b$

If we "pump" $v$ and $y$ once, we get more $a$s and $b$s than $c$s, 

so the string would no longer be of the form $a^n b^n c^n$. $\checkmark$

</v-clicks>

---

# Proving Line 4

Cases:

Case 1: Either string ($v$ or $y$) could be a string of two characters $\checkmark$

Case 2 (updated): Either string ($v$ or $y$) could be a single repeating character (e.g. $a^j$) *but not both* $\checkmark$

Case 3: Both strings ($v$ and $y$) are single repeating characters.$\checkmark$

---

# Another example: 

Prove $B = \{ww ~|~ w\in \{0,1\}^*\}$ is not context free.

| Proof Step | Reasoning |
| --- | --- |
| $B = \{ww ~\mid~ w\in \{0,1\}^*\}$ is a context free language | Assumption |
| Choose $s = 0^p1^p0^p1^p \in B$ | Definition of $B$ |
| $s$ can be split into $s = uvxyz$, where for any $i \geq 0$, $uv^ixy^iz$ is in $B$ | Pumping lemma |
| It's impossible to split $s$ into $s = uvxyz$, where $\forall i \geq 0$, $uv^ixy^iz \in B$ | Shown next... |
| $\rightarrow \leftarrow$| Lines 3 and 4 contradict.|

---

# Proving Line 4

Cases: 

<v-clicks>

* $v$ and/or $y$ are all $0$'s

* $v$ and/or $y$ are all $1$'s

* Either $v$ or $y$ is $0$'s followed by $1$'s.

* Either $v$ or $y$ is $1$'s followed by $0$'s


</v-clicks>

<v-clicks>

We do *not* need to consider the case where $v$ or $y$ contains more than two different characters <br> (e.g. $v = 00 \ldots 0 11 \ldots 1 00 \ldots 0$) <br>
because we have the requirement that $|vxy| \leq p$.

Use these cases for your CQ! 
</v-clicks>


