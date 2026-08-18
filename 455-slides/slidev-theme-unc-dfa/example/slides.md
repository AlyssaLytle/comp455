---
theme: ./slidev-theme-unc-dfa
title: Deterministic Finite Automata
logo: ./unc-logo.png
kicker: COMP 455 · Theory of Computation
layout: cover
---

# Deterministic Finite Automata

An introduction to the simplest machines that compute

<!--
Welcome. Introduce the course and today's topic: deterministic finite automata, the simplest model of computation we'll study.
-->

---
kicker: Today
layout: default
---

## Agenda

<div style="display:flex;flex-direction:column;">
  <div style="display:flex;align-items:baseline;gap:40px;padding:26px 0;border-bottom:1px solid #DCE3EC;">
    <div style="font-size:32px;font-weight:700;color:#1B6FA8;width:70px;">01</div>
    <div style="font-size:34px;font-weight:600;color:#13294B;width:420px;">Foundations</div>
    <div style="font-size:24px;color:#51607A;">Why automata theory, and what counts as a machine</div>
  </div>
  <div style="display:flex;align-items:baseline;gap:40px;padding:26px 0;border-bottom:1px solid #DCE3EC;">
    <div style="font-size:32px;font-weight:700;color:#1B6FA8;width:70px;">02</div>
    <div style="font-size:34px;font-weight:600;color:#13294B;width:420px;">The Formal Definition</div>
    <div style="font-size:24px;color:#51607A;">The five-tuple, state diagrams, and the language of a DFA</div>
  </div>
  <div style="display:flex;align-items:baseline;gap:40px;padding:26px 0;border-bottom:1px solid #DCE3EC;">
    <div style="font-size:32px;font-weight:700;color:#1B6FA8;width:70px;">03</div>
    <div style="font-size:34px;font-weight:600;color:#13294B;width:420px;">Examples &amp; Practice</div>
    <div style="font-size:24px;color:#51607A;">Tracing DFAs by hand, then designing our own</div>
  </div>
  <div style="display:flex;align-items:baseline;gap:40px;padding:26px 0;border-bottom:1px solid #DCE3EC;">
    <div style="font-size:32px;font-weight:700;color:#1B6FA8;width:70px;">04</div>
    <div style="font-size:34px;font-weight:600;color:#13294B;width:420px;">Beyond DFAs</div>
    <div style="font-size:24px;color:#51607A;">A first look at nondeterminism</div>
  </div>
  <div style="display:flex;align-items:baseline;gap:40px;padding:26px 0;">
    <div style="font-size:32px;font-weight:700;color:#1B6FA8;width:70px;">05</div>
    <div style="font-size:34px;font-weight:600;color:#13294B;width:420px;">Regular Languages</div>
    <div style="font-size:24px;color:#51607A;">What DFAs recognize, and how those languages combine</div>
  </div>
</div>

<!-- Walk through the five parts of today's lecture at a high level. -->

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

<div style="display:flex;gap:60px;align-items:center;">
  <div style="display:flex;flex-direction:column;gap:24px;max-width:700px;">
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">Every time a text editor highlights a search match, or a compiler tokenizes your code, a finite automaton is running underneath.</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">Regular expressions — the ones you use in <span style="font-family:'Roboto Mono',monospace;">grep</span> or Python — compile down to exactly this kind of machine.</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">It's the simplest model of computation we study — no tape, no stack, just a handful of states.</div>
  </div>
  <div style="background:#13294B;border-radius:16px;padding:36px;width:320px;flex-shrink:0;">
    <div style="font-size:16px;color:#8FC1E8;font-weight:700;text-transform:uppercase;letter-spacing:2px;margin-bottom:16px;">Relief</div>
    <div style="font-size:22px;color:#FFFFFF;line-height:1.5;">No Turing machines yet. Today, every question we ask has a definite answer.</div>
  </div>
</div>

<!-- Motivate the topic: automata underlie text search, compilers, and regex engines. Keep it light. -->

---
kicker: Foundations
layout: default
---

## Computation as a Machine

<div style="font-size:24px;color:#1A1F27;line-height:1.5;max-width:1000px;margin-bottom:32px;">A finite automaton reads an input string one symbol at a time, changes its internal state as it goes, and at the end reports a single yes-or-no answer.</div>

<div style="display:flex;align-items:center;justify-content:center;gap:0;">
  <div style="display:flex;flex-direction:column;align-items:center;gap:12px;">
    <div style="display:flex;gap:6px;">
      <div style="width:44px;height:44px;border:2px solid #13294B;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:22px;font-family:'Roboto Mono',monospace;color:#13294B;">0</div>
      <div style="width:44px;height:44px;border:2px solid #13294B;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:22px;font-family:'Roboto Mono',monospace;color:#13294B;">1</div>
      <div style="width:44px;height:44px;border:2px solid #13294B;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:22px;font-family:'Roboto Mono',monospace;color:#13294B;">1</div>
      <div style="width:44px;height:44px;border:2px solid #13294B;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:22px;font-family:'Roboto Mono',monospace;color:#13294B;">0</div>
    </div>
    <div style="font-size:18px;color:#51607A;">input string</div>
  </div>
  <div style="width:70px;height:3px;background:#1B6FA8;margin:0 20px;"></div>
  <div style="display:flex;flex-direction:column;align-items:center;gap:12px;">
    <div style="width:170px;height:100px;background:#13294B;border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:22px;font-weight:700;color:#FFFFFF;">Machine</div>
    <div style="font-size:18px;color:#51607A;">one state at a time</div>
  </div>
  <div style="width:70px;height:3px;background:#1B6FA8;margin:0 20px;"></div>
  <div style="display:flex;flex-direction:column;align-items:center;gap:12px;">
    <div style="width:170px;height:100px;background:#DCEBF7;border:3px solid #1B6FA8;border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:22px;font-weight:700;color:#13294B;">Accept / Reject</div>
    <div style="font-size:18px;color:#51607A;">a single verdict</div>
  </div>
</div>

<!-- Introduce the black-box view: a machine reads input and reports accept or reject. -->

---
kicker: Foundations
layout: default
---

## Intuition: A Turnstile

<div style="font-size:22px;color:#51607A;margin-bottom:16px;">A turnstile has two conditions, and two things that can happen to it.</div>

<div style="display:flex;justify-content:center;">
<svg viewBox="0 0 900 420" style="width:700px;height:327px;">
  <defs><marker id="t-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M20,210 L110,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#t-arrow)"/>
  <path d="M225,150 C300,60 500,60 575,150" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#t-arrow)"/>
  <text x="400" y="90" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">coin</text>
  <path d="M575,270 C500,360 300,360 225,270" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#t-arrow)"/>
  <text x="400" y="345" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">push</text>
  <path d="M150,145 C110,100 150,55 175,95" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#t-arrow)"/>
  <text x="95" y="90" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">push</text>
  <path d="M650,95 C675,55 715,100 675,145" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#t-arrow)"/>
  <text x="705" y="90" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">coin</text>
  <circle cx="170" cy="210" r="70" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="170" y="220" text-anchor="middle" font-size="30" font-weight="700" fill="#13294B">Locked</text>
  <circle cx="630" cy="210" r="70" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <text x="630" y="220" text-anchor="middle" font-size="30" font-weight="700" fill="#13294B">Unlocked</text>
</svg>
</div>

<!-- Use the subway turnstile as a warm, concrete example of a state machine before any formalism. -->

---
kicker: Foundations
layout: two-cols
---

## From Analogy to Automaton

::title::

<div style="font-size:22px;color:#51607A;margin-bottom:8px;">Relabel it, and it's already everything we need: states, an alphabet, transitions, a start state.</div>

::left::

<svg viewBox="0 0 700 420" style="width:100%;max-width:480px;">
  <defs><marker id="f-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M20,210 L110,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#f-arrow)"/>
  <path d="M225,150 C300,60 400,60 475,150" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#f-arrow)"/>
  <text x="350" y="90" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">coin</text>
  <path d="M475,270 C400,360 300,360 225,270" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#f-arrow)"/>
  <text x="350" y="345" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">push</text>
  <circle cx="170" cy="210" r="70" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="170" y="220" text-anchor="middle" font-size="30" font-weight="700" fill="#13294B">q0</text>
  <circle cx="530" cy="210" r="70" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <text x="530" y="220" text-anchor="middle" font-size="30" font-weight="700" fill="#13294B">q1</text>
</svg>

::right::

<div style="display:flex;flex-direction:column;gap:20px;font-family:'Roboto Mono',monospace;">
  <div style="display:flex;gap:16px;"><div style="color:#1B6FA8;width:34px;">Q</div><div style="font-size:20px;color:#1A1F27;">two states, {q0, q1}</div></div>
  <div style="display:flex;gap:16px;"><div style="color:#1B6FA8;width:34px;">Σ</div><div style="font-size:20px;color:#1A1F27;">two symbols, {coin, push}</div></div>
  <div style="display:flex;gap:16px;"><div style="color:#1B6FA8;width:34px;">δ</div><div style="font-size:20px;color:#1A1F27;">the four arrows above</div></div>
  <div style="display:flex;gap:16px;"><div style="color:#1B6FA8;width:34px;">q0</div><div style="font-size:20px;color:#1A1F27;">start locked</div></div>
</div>

<!-- Relabel the turnstile with formal state names: it already has all the ingredients of a DFA. -->

---
layout: section
index: "02"
---

# The Formal Definition

---
kicker: The Formal Definition
layout: default
---

## A DFA Is a 5-Tuple

<div style="font-family:'Roboto Mono',monospace;font-size:32px;color:#13294B;background:#DCEBF7;border-radius:12px;padding:16px 28px;display:inline-block;margin-bottom:28px;">M = (Q, Σ, δ, q0, F)</div>

<div style="display:flex;flex-direction:column;">
  <div style="display:flex;align-items:baseline;gap:30px;padding:14px 0;border-bottom:1px solid #DCE3EC;"><div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#1B6FA8;width:60px;">Q</div><div style="font-size:22px;color:#1A1F27;">a finite set of <b>states</b></div></div>
  <div style="display:flex;align-items:baseline;gap:30px;padding:14px 0;border-bottom:1px solid #DCE3EC;"><div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#1B6FA8;width:60px;">Σ</div><div style="font-size:22px;color:#1A1F27;">a finite <b>alphabet</b> of input symbols</div></div>
  <div style="display:flex;align-items:baseline;gap:30px;padding:14px 0;border-bottom:1px solid #DCE3EC;"><div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#1B6FA8;width:60px;">δ</div><div style="font-size:22px;color:#1A1F27;">a <b>transition function</b>, δ: Q × Σ → Q</div></div>
  <div style="display:flex;align-items:baseline;gap:30px;padding:14px 0;border-bottom:1px solid #DCE3EC;"><div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#1B6FA8;width:60px;">q0</div><div style="font-size:22px;color:#1A1F27;">the <b>start state</b>, q0 ∈ Q</div></div>
  <div style="display:flex;align-items:baseline;gap:30px;padding:14px 0;"><div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#1B6FA8;width:60px;">F</div><div style="font-size:22px;color:#1A1F27;">the set of <b>accepting states</b>, F ⊆ Q</div></div>
</div>

<!-- Present the 5-tuple, component by component. -->

---
kicker: The Formal Definition
layout: two-cols
---

## A Concrete Example

::title::

<div style="font-size:20px;color:#51607A;">M1: strings over {0,1} that end in <code>01</code></div>

::left::

<svg viewBox="0 0 760 420" style="width:100%;max-width:480px;">
  <defs><marker id="m1-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M10,210 L90,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <path d="M155,155 C130,90 95,90 90,150" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <text x="95" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <path d="M225,210 L385,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <text x="305" y="195" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">0</text>
  <path d="M450,155 C425,90 390,90 385,150" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <text x="390" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">0</text>
  <path d="M520,210 L680,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <text x="600" y="195" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <path d="M660,275 C500,370 250,370 155,275" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <text x="405" y="360" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">0</text>
  <path d="M690,155 C620,60 260,60 230,150" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#m1-arrow)"/>
  <text x="460" y="55" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">1</text>
  <circle cx="150" cy="210" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="150" y="220" text-anchor="middle" font-size="28" font-weight="700" fill="#13294B">q0</text>
  <circle cx="445" cy="210" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="445" y="220" text-anchor="middle" font-size="28" font-weight="700" fill="#13294B">q1</text>
  <circle cx="695" cy="210" r="65" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <circle cx="695" cy="210" r="52" fill="none" stroke="#13294B" stroke-width="3"/>
  <text x="695" y="220" text-anchor="middle" font-size="28" font-weight="700" fill="#13294B">q2</text>
</svg>

::right::

<div style="display:flex;flex-direction:column;gap:14px;font-family:'Roboto Mono',monospace;font-size:20px;color:#1A1F27;">
  <div>Q = {q0, q1, q2}</div>
  <div>Σ = {0, 1}</div>
  <div>q0 = q0</div>
  <div>F = {q2}</div>
  <div style="color:#51607A;">q1 means "last symbol was 0"<br/>q2 means "last two were 01"</div>
</div>

<!-- Introduce the running example: strings over {0,1} ending in 01. -->

---
kicker: The Formal Definition
layout: default
---

## Reading a State Diagram

<div style="display:grid;grid-template-columns:1fr 1fr;gap:36px;">
  <div style="display:flex;align-items:center;gap:28px;">
    <svg viewBox="0 0 140 140" style="width:80px;height:80px;flex-shrink:0;"><circle cx="70" cy="70" r="60" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/></svg>
    <div style="font-size:22px;color:#1A1F27;">A circle is a <b>state</b></div>
  </div>
  <div style="display:flex;align-items:center;gap:28px;">
    <svg viewBox="0 0 140 140" style="width:80px;height:80px;flex-shrink:0;"><circle cx="70" cy="70" r="60" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/><circle cx="70" cy="70" r="48" fill="none" stroke="#13294B" stroke-width="3"/></svg>
    <div style="font-size:22px;color:#1A1F27;">A double circle is an <b>accepting state</b></div>
  </div>
  <div style="display:flex;align-items:center;gap:28px;">
    <svg viewBox="0 0 200 140" style="width:120px;height:84px;flex-shrink:0;">
      <defs><marker id="leg-a1" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
      <path d="M10,70 L70,70" stroke="#13294B" stroke-width="3" marker-end="url(#leg-a1)"/>
      <circle cx="130" cy="70" r="60" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    </svg>
    <div style="font-size:22px;color:#1A1F27;">An unattached arrow marks the <b>start state</b></div>
  </div>
  <div style="display:flex;align-items:center;gap:28px;">
    <svg viewBox="0 0 220 140" style="width:130px;height:83px;flex-shrink:0;">
      <defs><marker id="leg-a2" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#1B6FA8"/></marker></defs>
      <circle cx="55" cy="70" r="50" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
      <path d="M105,70 L155,70" stroke="#1B6FA8" stroke-width="3" marker-end="url(#leg-a2)"/>
      <text x="130" y="55" text-anchor="middle" font-size="22" fill="#1B6FA8" font-family="Roboto Mono,monospace">a</text>
      <circle cx="200" cy="70" r="50" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    </svg>
    <div style="font-size:22px;color:#1A1F27;">A labeled arrow is a <b>transition</b> on that symbol</div>
  </div>
</div>

<!-- Give students the legend for reading any state diagram from here on. -->

---
kicker: The Formal Definition
layout: default
---

## Extending δ to Strings

<div style="font-size:20px;color:#51607A;margin-bottom:28px;">δ only knows how to read one symbol. We build δ̂ to read a whole string, one symbol at a time.</div>

<div style="display:flex;flex-direction:column;gap:20px;">
  <div style="display:flex;align-items:center;gap:24px;background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:20px 28px;">
    <div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#13294B;white-space:nowrap;">δ̂(q, ε) = q</div>
    <div style="font-size:18px;color:#51607A;">reading nothing leaves you where you started</div>
  </div>
  <div style="display:flex;align-items:center;gap:24px;background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:20px 28px;">
    <div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#13294B;white-space:nowrap;">δ̂(q, wa) = δ(δ̂(q, w), a)</div>
    <div style="font-size:18px;color:#51607A;">process the string so far, then read one more symbol</div>
  </div>
</div>

<div style="margin-top:28px;font-size:22px;color:#1A1F27;line-height:1.5;">In practice, tracing a DFA is just following the arrows — δ̂ makes "follow the arrows" precise.</div>

<!-- Introduce delta-hat: extending the one-symbol transition function to whole strings. -->

---
kicker: The Formal Definition
layout: default
---

## The Language of a DFA

<div style="display:flex;align-items:center;gap:48px;margin-bottom:28px;">
  <div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#13294B;background:#DCEBF7;border-radius:12px;padding:24px 32px;">L(M) = { w ∈ Σ* | δ̂(q0, w) ∈ F }</div>
  <div style="font-size:22px;color:#1A1F27;line-height:1.5;max-width:480px;">A DFA doesn't just accept or reject one string — it partitions <i>every possible string</i> into two piles.</div>
</div>
<div style="font-size:22px;color:#1A1F27;">L(M) is that pile of accepted strings: the language the machine recognizes.</div>

<!-- Define L(M): a DFA defines the whole set of strings it accepts. -->

---
layout: section
index: "03"
---

# Examples &amp; Practice

---
kicker: Examples & Practice
layout: two-cols
---

## Trace: Ends in 01

::title::

<div style="font-size:20px;color:#51607A;">Input: <code>1001</code> on M1</div>

::left::

<svg viewBox="0 0 760 420" style="width:100%;max-width:440px;">
  <defs><marker id="m1b-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M10,210 L90,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <path d="M155,155 C130,90 95,90 90,150" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <text x="95" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <path d="M225,210 L385,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <text x="305" y="195" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">0</text>
  <path d="M450,155 C425,90 390,90 385,150" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <text x="390" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">0</text>
  <path d="M520,210 L680,210" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <text x="600" y="195" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <path d="M660,275 C500,370 250,370 155,275" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <text x="405" y="360" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">0</text>
  <path d="M690,155 C620,60 260,60 230,150" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#m1b-arrow)"/>
  <text x="460" y="55" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">1</text>
  <circle cx="150" cy="210" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="150" y="220" text-anchor="middle" font-size="28" font-weight="700" fill="#13294B">q0</text>
  <circle cx="445" cy="210" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="445" y="220" text-anchor="middle" font-size="28" font-weight="700" fill="#13294B">q1</text>
  <circle cx="695" cy="210" r="65" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <circle cx="695" cy="210" r="52" fill="none" stroke="#13294B" stroke-width="3"/>
  <text x="695" y="220" text-anchor="middle" font-size="28" font-weight="700" fill="#13294B">q2</text>
</svg>

::right::

<div style="display:flex;flex-direction:column;gap:10px;">
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div><div>— 1 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div><div>— 0 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q1</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q1</div><div>— 0 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q1</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q1</div><div>— 1 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q2</div></div>
  <div style="margin-top:12px;display:inline-flex;align-items:center;gap:12px;background:#DCEBF7;border-radius:10px;padding:12px 20px;width:fit-content;">
    <div style="font-size:20px;font-weight:700;color:#13294B;">q2 ∈ F → Accepted</div>
  </div>
</div>

<!-- Trace 1001 through M1 step by step on the board. -->

---
kicker: Examples & Practice
layout: two-cols
---

## Trace: An Even Number of 0s

::title::

<div style="font-size:20px;color:#51607A;">Input: <code>1010</code> — two states: even so far, or odd so far</div>

::left::

<svg viewBox="0 0 700 380" style="width:100%;max-width:400px;">
  <defs><marker id="ev-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M10,190 L90,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#ev-arrow)"/>
  <path d="M215,140 C350,60 400,60 490,135" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#ev-arrow)"/>
  <text x="350" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">0</text>
  <path d="M500,245 C400,340 250,340 220,255" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#ev-arrow)"/>
  <text x="360" y="335" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">0</text>
  <path d="M100,130 C60,80 130,35 170,90" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#ev-arrow)"/>
  <text x="55" y="75" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">1</text>
  <path d="M545,130 C585,80 515,35 475,90" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#ev-arrow)"/>
  <text x="600" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <circle cx="155" cy="190" r="70" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <circle cx="155" cy="190" r="57" fill="none" stroke="#13294B" stroke-width="3"/>
  <text x="155" y="200" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q_even</text>
  <circle cx="545" cy="190" r="70" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="545" y="200" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q_odd</text>
</svg>

::right::

<div style="display:flex;flex-direction:column;gap:10px;">
  <div style="display:flex;align-items:center;gap:12px;font-size:20px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:90px;color:#1B6FA8;font-weight:700;">q_even</div><div>— 1 →</div><div style="width:90px;color:#1B6FA8;font-weight:700;">q_even</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:20px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:90px;color:#1B6FA8;font-weight:700;">q_even</div><div>— 0 →</div><div style="width:90px;color:#1B6FA8;font-weight:700;">q_odd</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:20px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:90px;color:#1B6FA8;font-weight:700;">q_odd</div><div>— 1 →</div><div style="width:90px;color:#1B6FA8;font-weight:700;">q_odd</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:20px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:90px;color:#1B6FA8;font-weight:700;">q_odd</div><div>— 0 →</div><div style="width:90px;color:#1B6FA8;font-weight:700;">q_even</div></div>
  <div style="margin-top:12px;display:inline-flex;align-items:center;gap:12px;background:#DCEBF7;border-radius:10px;padding:12px 20px;width:fit-content;">
    <div style="font-size:20px;font-weight:700;color:#13294B;">two 0s, ends at q_even → Accepted</div>
  </div>
</div>

<!-- Second worked example: a two-state DFA tracking parity of zero count. -->

---
kicker: Examples & Practice
layout: two-cols
---

## Trace: Divisible by 3

::title::

<div style="font-size:20px;color:#51607A;">Each state tracks the remainder mod 3. Input: <code>110</code> (six)</div>

::left::

<svg viewBox="0 0 700 460" style="width:100%;max-width:380px;">
  <defs><marker id="d3-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M10,150 L90,140" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <path d="M240,190 C260,270 300,300 330,340" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <text x="215" y="270" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <path d="M470,340 C500,300 540,265 555,195" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <text x="555" y="270" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <path d="M380,395 C420,410 460,410 470,395" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <path d="M470,375 C440,360 405,360 380,375" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <text x="425" y="440" text-anchor="middle" font-size="22" fill="#1B6FA8" font-family="Roboto Mono,monospace">0</text>
  <path d="M120,90 C160,60 210,60 235,95" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <text x="175" y="55" text-anchor="middle" font-size="22" fill="#1B6FA8" font-family="Roboto Mono,monospace">0</text>
  <path d="M540,105 C580,70 605,105 570,140" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#d3-arrow)"/>
  <text x="620" y="90" text-anchor="middle" font-size="22" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <circle cx="175" cy="120" r="65" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <circle cx="175" cy="120" r="52" fill="none" stroke="#13294B" stroke-width="3"/>
  <text x="175" y="130" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q0</text>
  <circle cx="290" cy="395" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="290" y="405" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q1</text>
  <circle cx="530" cy="120" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="530" y="130" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q2</text>
</svg>

::right::

<div style="display:flex;flex-direction:column;gap:10px;">
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div><div>— 1 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q1</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q1</div><div>— 1 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div></div>
  <div style="display:flex;align-items:center;gap:12px;font-size:22px;font-family:'Roboto Mono',monospace;color:#1A1F27;"><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div><div>— 0 →</div><div style="width:54px;color:#1B6FA8;font-weight:700;">q0</div></div>
  <div style="margin-top:12px;display:inline-flex;align-items:center;gap:12px;background:#DCEBF7;border-radius:10px;padding:12px 20px;width:fit-content;">
    <div style="font-size:20px;font-weight:700;color:#13294B;">110₂ = 6, remainder 0 → Accepted</div>
  </div>
</div>

<!-- Third example: binary numbers divisible by 3, tracking remainder mod 3. -->

---
kicker: Examples & Practice
layout: two-cols
---

## Your Turn: Trace This

::title::

<div style="font-size:20px;color:#51607A;">Same "even number of 0s" machine. Input: <code>0110</code> — accept or reject?</div>

::left::

<svg viewBox="0 0 700 380" style="width:100%;max-width:400px;">
  <defs><marker id="yt-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
  <path d="M10,190 L90,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#yt-arrow)"/>
  <path d="M215,140 C350,60 400,60 490,135" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#yt-arrow)"/>
  <text x="350" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">0</text>
  <path d="M500,245 C400,340 250,340 220,255" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#yt-arrow)"/>
  <text x="360" y="335" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">0</text>
  <path d="M100,130 C60,80 130,35 170,90" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#yt-arrow)"/>
  <text x="55" y="75" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">1</text>
  <path d="M545,130 C585,80 515,35 475,90" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#yt-arrow)"/>
  <text x="600" y="75" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">1</text>
  <circle cx="155" cy="190" r="70" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
  <circle cx="155" cy="190" r="57" fill="none" stroke="#13294B" stroke-width="3"/>
  <text x="155" y="200" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q_even</text>
  <circle cx="545" cy="190" r="70" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
  <text x="545" y="200" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">q_odd</text>
</svg>

::right::

<div style="font-size:22px;color:#1A1F27;line-height:1.5;margin-bottom:16px;">Work it out: follow each symbol of <code>0, 1, 1, 0</code> through the diagram.</div>

<v-click>
<div style="border-top:2px dashed #DCE3EC;padding-top:16px;">
  <div style="font-size:16px;letter-spacing:2px;color:#51607A;text-transform:uppercase;margin-bottom:8px;">Answer</div>
  <div style="font-size:20px;font-family:'Roboto Mono',monospace;color:#51607A;">q_even → q_odd → q_odd → q_odd → q_even — two 0s, <b style="color:#13294B;">accepted</b></div>
</div>
</v-click>

<!-- Give students a moment to trace this on their own before revealing the answer. -->

---
kicker: Examples & Practice
layout: default
---

## Designing a DFA: Think in States

<div style="display:flex;flex-direction:column;gap:24px;max-width:1000px;">
  <div style="display:flex;align-items:flex-start;gap:24px;">
    <div style="width:44px;height:44px;border-radius:50%;background:#13294B;color:#fff;font-size:22px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;">1</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">Ask: <b>what's the least I need to remember</b> about the input so far to decide what happens next?</div>
  </div>
  <div style="display:flex;align-items:flex-start;gap:24px;">
    <div style="width:44px;height:44px;border-radius:50%;background:#13294B;color:#fff;font-size:22px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;">2</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">Each distinct answer becomes <b>one state</b>. A DFA has no memory beyond "which state am I in."</div>
  </div>
  <div style="display:flex;align-items:flex-start;gap:24px;">
    <div style="width:44px;height:44px;border-radius:50%;background:#13294B;color:#fff;font-size:22px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;">3</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">For every state, decide where <b>each</b> symbol of Σ sends you — every state needs a complete set of exits.</div>
  </div>
</div>

<!-- Shift from tracing to designing: the key skill is figuring out what a state needs to remember. -->

---
kicker: Examples & Practice
layout: default
---

## Design Walkthrough: Contains "ab"

<div style="font-size:20px;color:#51607A;margin-bottom:20px;">Language: strings over {a, b} that contain <code>ab</code> somewhere</div>

<div style="display:flex;gap:40px;align-items:center;">
  <svg viewBox="0 0 1000 380" style="width:520px;flex-shrink:0;">
    <defs><marker id="ab-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
    <path d="M10,190 L90,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#ab-arrow)"/>
    <path d="M155,135 C110,80 190,35 220,90" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#ab-arrow)"/>
    <text x="105" y="70" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">b</text>
    <path d="M225,190 L385,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#ab-arrow)"/>
    <text x="305" y="175" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">a</text>
    <path d="M450,135 C405,80 485,35 515,90" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#ab-arrow)"/>
    <text x="400" y="70" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">a</text>
    <path d="M520,190 L680,190" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#ab-arrow)"/>
    <text x="600" y="175" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">b</text>
    <path d="M745,135 C700,80 850,35 880,90" stroke="#51607A" stroke-width="3" fill="none" marker-end="url(#ab-arrow)"/>
    <text x="800" y="70" text-anchor="middle" font-size="22" fill="#51607A" font-family="Roboto Mono,monospace">a, b</text>
    <circle cx="150" cy="190" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    <text x="150" y="200" text-anchor="middle" font-size="26" font-weight="700" fill="#13294B">q0</text>
    <circle cx="445" cy="190" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    <text x="445" y="200" text-anchor="middle" font-size="26" font-weight="700" fill="#13294B">q1</text>
    <circle cx="740" cy="190" r="65" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
    <circle cx="740" cy="190" r="52" fill="none" stroke="#13294B" stroke-width="3"/>
    <text x="740" y="200" text-anchor="middle" font-size="26" font-weight="700" fill="#13294B">q2</text>
  </svg>
  <div style="display:flex;flex-direction:column;gap:16px;font-size:22px;color:#1A1F27;line-height:1.5;">
    <div><b style="color:#1B6FA8;">q0</b> — haven't seen an "a" that could start "ab"</div>
    <div><b style="color:#1B6FA8;">q1</b> — just saw an "a"; a "b" now completes the match</div>
    <div><b style="color:#1B6FA8;">q2</b> — already saw "ab"; stay here forever, it's absorbing</div>
  </div>
</div>

<!-- Build a DFA for strings containing the substring ab, live, using the think-in-states framework. -->

---
kicker: Examples & Practice
layout: default
---

## Pitfall: Missing Transitions

<div style="display:flex;gap:56px;align-items:center;">
  <div style="display:flex;flex-direction:column;gap:20px;max-width:560px;">
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">A DFA's δ must be defined for <b>every</b> state and <b>every</b> symbol — that's what makes it deterministic and total.</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">Students often draw only the transitions that matter to the story, and quietly leave some pairs undefined.</div>
    <div style="font-size:24px;color:#1A1F27;line-height:1.5;">Fix: add an explicit <b>trap state</b> that catches every "otherwise" case and loops on itself forever.</div>
  </div>
  <div style="background:#13294B;border-radius:16px;padding:36px;width:360px;flex-shrink:0;">
    <div style="font-size:16px;color:#8FC1E8;font-weight:700;text-transform:uppercase;letter-spacing:2px;margin-bottom:16px;">Checklist</div>
    <div style="font-size:20px;color:#FFFFFF;line-height:1.7;">For each state, count the outgoing arrows.<br/>Does the count equal |Σ|?<br/>If not — route the rest to a trap state.</div>
  </div>
</div>

<!-- Common student mistake: forgetting a transition. Emphasize totality and the trap-state fix. -->

---
layout: section
index: "04"
---

# Beyond DFAs

---
kicker: Beyond DFAs
layout: default
---

## Enter Nondeterminism

<div style="font-size:20px;color:#51607A;margin-bottom:20px;">Same language, contains "ab" — but now the machine is allowed to guess.</div>

<div style="display:flex;gap:40px;align-items:center;">
  <svg viewBox="0 0 1000 380" style="width:520px;flex-shrink:0;">
    <defs><marker id="nfa-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
    <path d="M10,190 L90,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#nfa-arrow)"/>
    <path d="M155,135 C110,80 190,35 220,90" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#nfa-arrow)"/>
    <text x="105" y="70" text-anchor="middle" font-size="24" fill="#1B6FA8" font-family="Roboto Mono,monospace">a</text>
    <path d="M225,190 L385,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#nfa-arrow)"/>
    <text x="305" y="175" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">a</text>
    <path d="M520,190 L680,190" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#nfa-arrow)"/>
    <text x="600" y="175" text-anchor="middle" font-size="24" fill="#13294B" font-family="Roboto Mono,monospace">b</text>
    <circle cx="150" cy="190" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    <text x="150" y="200" text-anchor="middle" font-size="26" font-weight="700" fill="#13294B">q0</text>
    <circle cx="445" cy="190" r="65" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    <text x="445" y="200" text-anchor="middle" font-size="26" font-weight="700" fill="#13294B">q1</text>
    <circle cx="740" cy="190" r="65" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
    <circle cx="740" cy="190" r="52" fill="none" stroke="#13294B" stroke-width="3"/>
    <text x="740" y="200" text-anchor="middle" font-size="26" font-weight="700" fill="#13294B">q2</text>
  </svg>
  <div style="display:flex;flex-direction:column;gap:16px;font-size:22px;color:#1A1F27;line-height:1.5;">
    <div>From <b style="color:#1B6FA8;">q0</b>, an "a" can go to <b>two places at once</b> — stay at q0, or guess this is the "a" in "ab" and move to q1.</div>
    <div>q2 has no outgoing arrows at all — and that's allowed. NFAs don't need to be total.</div>
    <div style="color:#51607A;">Fewer states, easier to write down — the cost is "the" next state isn't always unique.</div>
  </div>
</div>

<!-- Introduce NFAs informally by contrast: multiple transitions on a symbol, missing transitions are fine. -->

---
kicker: Beyond DFAs
layout: statement
---

# NFAs and DFAs Recognize the Same Languages

Nondeterminism buys convenience, not additional power. Every NFA can be mechanically converted into an equivalent DFA — a construction called the **subset construction**.

*We'll build that construction next lecture.*

<!-- State the equivalence theorem as a teaser -- subset construction comes next lecture. -->

---
layout: section
index: "05"
---

# Regular Languages

---
kicker: Regular Languages
layout: default
---

## Regular Languages

<div style="font-size:20px;color:#51607A;margin-bottom:20px;">A language is <b>regular</b> exactly when some DFA recognizes it.</div>

<div style="display:flex;align-items:center;justify-content:center;gap:60px;">
  <svg viewBox="0 0 560 460" style="width:320px;">
    <circle cx="280" cy="230" r="220" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
    <circle cx="280" cy="260" r="120" fill="#DCEBF7" stroke="#1B6FA8" stroke-width="4"/>
    <text x="280" y="70" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">All languages over Σ*</text>
    <text x="280" y="265" text-anchor="middle" font-size="24" font-weight="700" fill="#13294B">Regular</text>
  </svg>
  <div style="display:flex;flex-direction:column;gap:20px;max-width:440px;font-size:22px;color:#1A1F27;line-height:1.5;">
    <div>Most languages you can describe are <b>not</b> regular — a DFA has finite memory, so it can never count without bound.</div>
    <div>Regular languages are the small, well-behaved slice that finite automata can handle exactly.</div>
  </div>
</div>

<!-- Define regular languages as exactly what DFAs recognize. -->

---
kicker: Regular Languages
layout: default
---

## Regular Languages Are Closed Under…

<div style="font-size:20px;color:#51607A;margin-bottom:32px;">Combine regular languages with these operations, and the result is still regular.</div>

<div style="display:grid;grid-template-columns:repeat(3,1fr);gap:20px;">
  <div style="background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:24px;"><div style="font-size:24px;font-weight:700;color:#13294B;margin-bottom:6px;">Union</div><div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#1B6FA8;">L1 ∪ L2</div></div>
  <div style="background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:24px;"><div style="font-size:24px;font-weight:700;color:#13294B;margin-bottom:6px;">Intersection</div><div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#1B6FA8;">L1 ∩ L2</div></div>
  <div style="background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:24px;"><div style="font-size:24px;font-weight:700;color:#13294B;margin-bottom:6px;">Complement</div><div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#1B6FA8;">Σ* − L</div></div>
  <div style="background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:24px;"><div style="font-size:24px;font-weight:700;color:#13294B;margin-bottom:6px;">Concatenation</div><div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#1B6FA8;">L1L2</div></div>
  <div style="background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:24px;"><div style="font-size:24px;font-weight:700;color:#13294B;margin-bottom:6px;">Kleene Star</div><div style="font-family:'Roboto Mono',monospace;font-size:20px;color:#1B6FA8;">L*</div></div>
  <div style="background:#DCEBF7;border:1px solid #1B6FA8;border-radius:12px;padding:24px;display:flex;align-items:center;"><div style="font-size:20px;font-weight:700;color:#13294B;">Two of these, next ↓</div></div>
</div>

<!-- List the closure properties before diving into the two we'll prove. -->

---
kicker: Regular Languages
layout: default
---

## Closure Under Complement

<div style="font-size:20px;color:#51607A;margin-bottom:24px;">Given a DFA for L, build one for Σ* − L: <b>swap</b> accepting and non-accepting states.</div>

<div style="display:flex;align-items:center;justify-content:center;gap:40px;">
  <div style="display:flex;flex-direction:column;align-items:center;gap:10px;">
    <svg viewBox="0 0 400 280" style="width:260px;">
      <defs><marker id="cc1-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
      <path d="M10,140 L60,140" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#cc1-arrow)"/>
      <path d="M130,110 C200,50 240,50 280,105" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#cc1-arrow)"/>
      <path d="M280,175 C240,230 200,230 130,170" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#cc1-arrow)"/>
      <circle cx="100" cy="140" r="55" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
      <circle cx="100" cy="140" r="43" fill="none" stroke="#13294B" stroke-width="3"/>
      <text x="100" y="149" text-anchor="middle" font-size="22" font-weight="700" fill="#13294B">q_even</text>
      <circle cx="310" cy="140" r="55" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
      <text x="310" y="149" text-anchor="middle" font-size="22" font-weight="700" fill="#13294B">q_odd</text>
    </svg>
    <div style="font-size:20px;font-weight:700;color:#13294B;">M — F = {q_even}</div>
  </div>
  <div style="font-size:40px;color:#1B6FA8;">→</div>
  <div style="display:flex;flex-direction:column;align-items:center;gap:10px;">
    <svg viewBox="0 0 400 280" style="width:260px;">
      <defs><marker id="cc2-arrow" markerWidth="10" markerHeight="10" refX="8" refY="3" orient="auto"><path d="M0,0 L8,3 L0,6 Z" fill="#13294B"/></marker></defs>
      <path d="M10,140 L60,140" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#cc2-arrow)"/>
      <path d="M130,110 C200,50 240,50 280,105" stroke="#13294B" stroke-width="3" fill="none" marker-end="url(#cc2-arrow)"/>
      <path d="M280,175 C240,230 200,230 130,170" stroke="#1B6FA8" stroke-width="3" fill="none" marker-end="url(#cc2-arrow)"/>
      <circle cx="100" cy="140" r="55" fill="#FAFAF7" stroke="#13294B" stroke-width="4"/>
      <text x="100" y="149" text-anchor="middle" font-size="22" font-weight="700" fill="#13294B">q_even</text>
      <circle cx="310" cy="140" r="55" fill="#DCEBF7" stroke="#13294B" stroke-width="4"/>
      <circle cx="310" cy="140" r="43" fill="none" stroke="#13294B" stroke-width="3"/>
      <text x="310" y="149" text-anchor="middle" font-size="22" font-weight="700" fill="#13294B">q_odd</text>
    </svg>
    <div style="font-size:20px;font-weight:700;color:#13294B;">M' — F' = {q_odd}</div>
  </div>
</div>
<div style="font-size:18px;color:#51607A;text-align:center;margin-top:12px;">This only works because every DFA is total — every string leads somewhere to swap.</div>

<!-- Prove complement closure by construction: swap accept and non-accept states. -->

---
kicker: Regular Languages
layout: default
---

## Closure Under Union

<div style="font-size:20px;color:#51607A;margin-bottom:28px;">Given DFAs M1 and M2, build a <b>product machine</b> whose states are pairs (p, q).</div>

<div style="display:flex;gap:48px;align-items:center;">
  <div style="display:grid;grid-template-columns:repeat(2,100px);grid-template-rows:repeat(2,100px);gap:16px;flex-shrink:0;">
    <div style="background:#DCEBF7;border:3px solid #1B6FA8;border-radius:12px;display:flex;align-items:center;justify-content:center;font-family:'Roboto Mono',monospace;font-size:20px;color:#13294B;">p0,q0</div>
    <div style="background:#FFFFFF;border:2px solid #DCE3EC;border-radius:12px;display:flex;align-items:center;justify-content:center;font-family:'Roboto Mono',monospace;font-size:20px;color:#13294B;">p0,q1</div>
    <div style="background:#FFFFFF;border:2px solid #DCE3EC;border-radius:12px;display:flex;align-items:center;justify-content:center;font-family:'Roboto Mono',monospace;font-size:20px;color:#13294B;">p1,q0</div>
    <div style="background:#DCEBF7;border:3px solid #1B6FA8;border-radius:12px;display:flex;align-items:center;justify-content:center;font-family:'Roboto Mono',monospace;font-size:20px;color:#13294B;">p1,q1</div>
  </div>
  <div style="display:flex;flex-direction:column;gap:16px;font-size:22px;color:#1A1F27;line-height:1.5;">
    <div>Each state is a pair: one component tracks M1, the other tracks M2.</div>
    <div>New accepting states: any pair where <b>either</b> component is accepting (highlighted).</div>
    <div style="color:#51607A;">Swap "either" for "both" and the same construction gives intersection instead.</div>
  </div>
</div>

<!-- Explain the product construction: track both machines' states simultaneously. -->

---
kicker: Regular Languages
layout: default
---

## Practice Problems

<div style="display:flex;flex-direction:column;gap:20px;">
  <div style="display:flex;gap:24px;align-items:flex-start;background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:22px 28px;">
    <div style="font-size:24px;font-weight:700;color:#1B6FA8;">1</div>
    <div style="font-size:22px;color:#1A1F27;line-height:1.5;">Design a DFA over {0,1} that accepts strings whose length is a multiple of 3.</div>
  </div>
  <div style="display:flex;gap:24px;align-items:flex-start;background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:22px 28px;">
    <div style="font-size:24px;font-weight:700;color:#1B6FA8;">2</div>
    <div style="font-size:22px;color:#1A1F27;line-height:1.5;">Design a DFA over {0,1} that accepts strings that do <b>not</b> contain "11" anywhere.</div>
  </div>
  <div style="display:flex;gap:24px;align-items:flex-start;background:#FFFFFF;border:1px solid #DCE3EC;border-radius:12px;padding:22px 28px;">
    <div style="font-size:24px;font-weight:700;color:#1B6FA8;">3</div>
    <div style="font-size:22px;color:#1A1F27;line-height:1.5;">Trace the "divisible by 3" machine on <code>1011</code> (eleven). Accept or reject?</div>
  </div>
</div>

<!-- Give students problems to attempt before the next class or in small groups now. -->

---
kicker: Wrap-Up
layout: default
---

## Key Takeaways

<div style="display:flex;flex-direction:column;">
  <div style="display:flex;align-items:baseline;gap:24px;padding:16px 0;border-bottom:1px solid #DCE3EC;"><div style="width:14px;height:14px;border-radius:50%;background:#1B6FA8;flex-shrink:0;"></div><div style="font-size:24px;color:#1A1F27;">A DFA is five pieces: states, alphabet, transition function, start state, accept states.</div></div>
  <div style="display:flex;align-items:baseline;gap:24px;padding:16px 0;border-bottom:1px solid #DCE3EC;"><div style="width:14px;height:14px;border-radius:50%;background:#1B6FA8;flex-shrink:0;"></div><div style="font-size:24px;color:#1A1F27;">It reads input one symbol at a time, with no memory beyond its current state.</div></div>
  <div style="display:flex;align-items:baseline;gap:24px;padding:16px 0;border-bottom:1px solid #DCE3EC;"><div style="width:14px;height:14px;border-radius:50%;background:#1B6FA8;flex-shrink:0;"></div><div style="font-size:24px;color:#1A1F27;">L(M) is the full set of strings a DFA accepts — a language, not just an answer.</div></div>
  <div style="display:flex;align-items:baseline;gap:24px;padding:16px 0;border-bottom:1px solid #DCE3EC;"><div style="width:14px;height:14px;border-radius:50%;background:#1B6FA8;flex-shrink:0;"></div><div style="font-size:24px;color:#1A1F27;">Regular languages are exactly what DFAs (equivalently, NFAs) recognize.</div></div>
  <div style="display:flex;align-items:baseline;gap:24px;padding:16px 0;"><div style="width:14px;height:14px;border-radius:50%;background:#1B6FA8;flex-shrink:0;"></div><div style="font-size:24px;color:#1A1F27;">They're closed under union, intersection, complement, concatenation, and star.</div></div>
</div>

<!-- Recap the lecture's core ideas before wrapping up. -->

---
layout: end
---

# Questions?

Next lecture: the subset construction, turning any NFA into a DFA.

<!-- Open the floor for questions. Remind students the subset construction is next lecture. -->
