---
# try also 'default' to start simple
theme: ./unc-cs
title: COMP 455 Syllabus
info: |
  ## Mathematical Foundations for Theory of Computation
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
kicker: COMP 455 · Models of Languages and Computation
layout: cover
---

# Mathematical Foundations: A Review

UNC-Chapel Hill, Fall 2026

---

# Sets - Definition

A ***set*** is an unordered collection of objects.

The following are sets:


<div style="display:flex;gap:36px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:30px 1px;flex:1;display: grid; place-items: center;">
      <div style="font-family:'Roboto Mono',monospace;font-size:18px;color:#EDF2F7;margin-bottom:12px;">{1, 2, 3}</div>
    </div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:30px 1px;flex:1;display: grid; place-items: center;">
      <div style="font-family:'Roboto Mono',monospace;font-size:18px;color:#EDF2F7;margin-bottom:12px;">"all multiples of 7"</div>
    </div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:30px 1px;flex:1;display: grid; place-items: center;">
      <div style="font-family:'Roboto Mono',monospace;font-size:18px;color:#EDF2F7;margin-bottom:12px;">{"apples", 7, True}</div>
    </div>
  </div>



---

# Properties of Sets

<v-clicks>

Sets don't inherently have an order.

> $\{1, 2, 3\} = \{3, 2, 1\}$

Sets don't count repeats.

> $\{1, 1, 2\} = \{1, 2\}$

</v-clicks>

---

# Sets - Notation


* $a \in A$ means $a$ is an element of $A$.

* $a \notin A$ means $a$ is *not* an element of $A$.

* $|A|$ is the cardinality, or number of elements, in $A$.

* $\emptyset$ is the empty set.

---

# Set-Builder Notation

  Instead of listing elements, describe the *rule* that qualifies them.

  <div style="font-family:'Roboto Mono',monospace;font-size:36px;color:#EDF2F7;background:#1B3350;border:1px solid #3A6C96;border-radius:12px;padding:26px 38px;display:inline-block;width:fit-content;margin-bottom:20px;">{ x | P(x) }</div>
  <div style="font-size:24px;color:#93A5BD;margin-bottom:44px;">read as: "the set of all x such that P(x) is true"</div>
  <div style="display:flex;gap:36px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px 32px;flex:1;">
      <div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#EDF2F7;margin-bottom:10px;">{ x &isin; &Nopf; | x is even }</div>
      <div style="font-size:24px;color:#93A5BD;">= {0, 2, 4, 6, &hellip;}</div>
    </div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px 32px;flex:1;">
      <div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#EDF2F7;margin-bottom:10px;">{ w &isin; &Sigma;* | w starts with a 1 }</div>
      <div style="font-size:24px;color:#93A5BD;">= {1, 10, 110, 101, &hellip;}</div>
    </div>
  </div>

---

# Common Sets

<div style="display:grid;grid-template-columns:repeat(2,1fr);gap:22px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-size:30px;color:#6CB6EA;margin-bottom:8px;">

$\mathbb{N} = \{0,1,\ldots \}$

</div>Natural Numbers</div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">

$\mathbb{Z} = \{ \ldots, -1, 0, 1, \ldots \}$

</div>Integers</div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">
    
   $\mathbb{Q} = \{ \frac{a}{b} | a,b \in \mathbb{Z} \}$
    
</div><div style="font-size:24px;color:#DCE3EC;">Rational Numbers</div></div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">
    
$\mathbb{R}$

</div><div style="font-size:24px;color:#DCE3EC;">Real Numbers</div></div>   
  </div>

---

# Sets You Will See

<div style="display:grid;grid-template-columns:repeat(2,1fr);gap:22px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">

$\Sigma$ (Alphabet)

</div>

A finite set of symbols

</div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">

$\Sigma^*$

</div>

The set of *all* finite strings over $\Sigma$ 

</div>

<div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">

$L$ (Language)

</div>

A set of strings over $\Sigma$ 

($L \subseteq \Sigma^*)$

</div>
  
  </div>


---
layout: two-cols
---

::title::

# Subset Operator

A is a *subset* of B if every element of A is also in B.

::left::



<svg viewBox="0 0 460 400" style="width:380px;height:330px;flex-shrink:0;">
      <circle cx="230" cy="180" r="175" fill="#111B2C" stroke="#93A5BD" stroke-width="4"/>
      <circle cx="230" cy="190" r="90" fill="#1B3350" stroke="#6CB6EA" stroke-width="4"/>
      <text x="230" y="90" text-anchor="middle" font-size="26" font-weight="700" fill="#EDF2F7">B</text>
      <text x="230" y="235" text-anchor="middle" font-size="26" font-weight="700" fill="#EDF2F7">A</text>
    </svg>

::right::
    
<v-clicks>

<div style="padding-top: 40px"></div>

* $A \subseteq B$: 
A is a subset of B 

($A$ could equal $B$)
    
* $A \subset B$: 
A is a *proper* subset

($A \neq B$)

* Example: 

$\{$ strings ending in $01 \} \subset \{0,1\}^*$

</v-clicks>