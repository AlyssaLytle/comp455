---
theme: default
title: Mathematical Foundations for Theory of Computation
canvasWidth: 1920
colorSchema: dark
---

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<img src="./unc-logo.png" alt="UNC logo" style="width:150px;height:auto;border-radius:8px;margin-bottom:56px;" />
  <div style="font-size:24px;letter-spacing:4px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:28px;">COMP 455 &middot; Theory of Computation</div>
  <h1 style="font-size:84px;font-weight:700;color:#EDF2F7;margin:0 0 24px 0;line-height:1.05;">Mathematical Foundations</h1>
  <div style="font-size:36px;color:#93A5BD;font-weight:400;">Sets, functions, logic, and proof &mdash; the vocabulary this course is built on</div>
</div>

<!--
Welcome. Today's material is background: the set notation, functions, logic, and proof techniques we'll rely on constantly once we start defining automata and languages formally.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Today</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 48px 0;">Agenda</h2>
  <div style="display:flex;flex-direction:column;">
    <div style="display:flex;align-items:baseline;gap:36px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-size:28px;font-weight:700;color:#6CB6EA;width:64px;">01</div><div style="font-size:28px;font-weight:600;color:#EDF2F7;width:420px;">Sets: The Basics</div><div style="font-size:24px;color:#93A5BD;">Notation, membership, and the sets we'll use constantly</div></div>
    <div style="display:flex;align-items:baseline;gap:36px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-size:28px;font-weight:700;color:#6CB6EA;width:64px;">02</div><div style="font-size:28px;font-weight:600;color:#EDF2F7;width:420px;">Set Operations</div><div style="font-size:24px;color:#93A5BD;">Union, intersection, difference, product, and cardinality</div></div>
    <div style="display:flex;align-items:baseline;gap:36px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-size:28px;font-weight:700;color:#6CB6EA;width:64px;">03</div><div style="font-size:28px;font-weight:600;color:#EDF2F7;width:420px;">Functions &amp; Relations</div><div style="font-size:24px;color:#93A5BD;">Domain, range, and the three properties that matter most</div></div>
    <div style="display:flex;align-items:baseline;gap:36px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-size:28px;font-weight:700;color:#6CB6EA;width:64px;">04</div><div style="font-size:28px;font-weight:600;color:#EDF2F7;width:420px;">Predicate Logic</div><div style="font-size:24px;color:#93A5BD;">Connectives, truth tables, and quantifiers</div></div>
    <div style="display:flex;align-items:baseline;gap:36px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-size:28px;font-weight:700;color:#6CB6EA;width:64px;">05</div><div style="font-size:28px;font-weight:600;color:#EDF2F7;width:420px;">Proof Techniques</div><div style="font-size:24px;color:#93A5BD;">Direct proof, contradiction, induction, and pigeonhole</div></div>
    <div style="display:flex;align-items:baseline;gap:36px;padding:18px 0;"><div style="font-size:28px;font-weight:700;color:#6CB6EA;width:64px;">06</div><div style="font-size:28px;font-weight:600;color:#EDF2F7;width:420px;">Bringing It Together</div><div style="font-size:24px;color:#93A5BD;">Why this is exactly the language automata theory speaks</div></div>
  </div>
</div>

<!--
Preview the six parts: sets, set operations, functions and relations, predicate logic, proof techniques, and why it all matters once we get to automata.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:220px;font-weight:700;color:#182740;line-height:1;margin-bottom:8px;">01</div>
  <h2 style="font-size:76px;font-weight:700;color:#EDF2F7;margin:0;">Sets: The Basics</h2>
</div>

<!--
Section break.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Sets: The Basics</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 44px 0;">What Is a Set?</h2>
  <div style="font-size:30px;color:#DCE3EC;line-height:1.5;max-width:1200px;margin-bottom:44px;">A <b style="color:#EDF2F7;">set</b> is an unordered collection of distinct objects, called its <b style="color:#EDF2F7;">elements</b> or <b style="color:#EDF2F7;">members</b>.</div>
  <div style="display:flex;gap:36px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:30px 36px;flex:1;">
      <div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#EDF2F7;margin-bottom:12px;">A = {1, 2, 3}</div>
      <div style="font-size:24px;color:#93A5BD;">order doesn't matter: {1,2,3} = {3,1,2}</div>
    </div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:30px 36px;flex:1;">
      <div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#EDF2F7;margin-bottom:12px;">{1, 1, 2} = {1, 2}</div>
      <div style="font-size:24px;color:#93A5BD;">duplicates don't count twice</div>
    </div>
  </div>
</div>

<!--
Define a set informally: an unordered collection of distinct objects. Emphasize unordered and no duplicates -- both surprise students at first.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Sets: The Basics</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 52px 0;">Notation &amp; Membership</h2>
  <div style="display:flex;flex-direction:column;">
    <div style="display:flex;align-items:baseline;gap:32px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;width:130px;">x &isin; A</div><div style="font-size:26px;color:#DCE3EC;">x is an <b style="color:#EDF2F7;">element of</b> A</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;width:130px;">x &notin; A</div><div style="font-size:26px;color:#DCE3EC;">x is <b style="color:#EDF2F7;">not</b> an element of A</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;width:130px;">|A|</div><div style="font-size:26px;color:#DCE3EC;">the <b style="color:#EDF2F7;">cardinality</b> of A &mdash; how many elements it has</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:18px 0;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;width:130px;">&empty;</div><div style="font-size:26px;color:#DCE3EC;">the <b style="color:#EDF2F7;">empty set</b>, the unique set with |&empty;| = 0</div></div>
  </div>
</div>

<!--
Introduce membership notation and the empty set. This is the vocabulary students will see every time we write a formal definition.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Sets: The Basics</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 16px 0;">Set-Builder Notation</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:44px;">Instead of listing elements, describe the <b style="color:#DCE3EC;">rule</b> that qualifies them.</div>
  <div style="font-family:'Roboto Mono',monospace;font-size:36px;color:#EDF2F7;background:#1B3350;border:1px solid #3A6C96;border-radius:12px;padding:26px 38px;display:inline-block;width:fit-content;margin-bottom:20px;">{ x | P(x) }</div>
  <div style="font-size:24px;color:#93A5BD;margin-bottom:44px;">read as: "the set of all x such that P(x) is true"</div>
  <div style="display:flex;gap:36px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px 32px;flex:1;">
      <div style="font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;margin-bottom:10px;">{ x &isin; &Nopf; | x is even }</div>
      <div style="font-size:24px;color:#93A5BD;">= {0, 2, 4, 6, &hellip;}</div>
    </div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px 32px;flex:1;">
      <div style="font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;margin-bottom:10px;">{ w &isin; &Sigma;* | w starts with a }</div>
      <div style="font-size:24px;color:#93A5BD;">exactly how we'll define languages soon</div>
    </div>
  </div>
</div>

<!--
Introduce set-builder notation as a way to describe sets by a property rather than listing every element. This shows up everywhere once we define L(M).
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Sets: The Basics</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 48px 0;">Common Sets You'll See by Name</h2>
  <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:22px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">&Nopf;</div><div style="font-size:24px;color:#DCE3EC;">natural numbers, {0,1,2,&hellip;}</div></div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">&Zopf;</div><div style="font-size:24px;color:#DCE3EC;">integers, {&hellip;,-1,0,1,&hellip;}</div></div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">&Qopf;, &Ropf;</div><div style="font-size:24px;color:#DCE3EC;">rationals, reals</div></div>
    <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;margin-bottom:8px;">&Sigma;</div><div style="font-size:24px;color:#DCE3EC;">an <b>alphabet</b> &mdash; a finite set of symbols</div></div>
    <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;margin-bottom:8px;">&Sigma;*</div><div style="font-size:24px;color:#DCE3EC;">the set of <b>all finite strings</b> over &Sigma;, including &epsilon;</div></div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:26px;"><div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#6CB6EA;margin-bottom:8px;">&empty;</div><div style="font-size:24px;color:#DCE3EC;">the empty set &mdash; not the same as {&empty;}</div></div>
  </div>
</div>

<!--
List the standard named sets students will see referenced by symbol throughout the course, including Sigma-star which is new to them.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Sets: The Basics</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Subsets</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:44px;">A is a <b style="color:#DCE3EC;">subset</b> of B if every element of A is also in B.</div>
  <div style="display:flex;gap:72px;align-items:center;flex:1;">
    <svg viewBox="0 0 460 400" style="width:380px;height:330px;flex-shrink:0;">
      <circle cx="230" cy="200" r="180" fill="#111B2C" stroke="#93A5BD" stroke-width="4"/>
      <circle cx="230" cy="230" r="90" fill="#1B3350" stroke="#6CB6EA" stroke-width="4"/>
      <text x="230" y="55" text-anchor="middle" font-size="26" font-weight="700" fill="#EDF2F7">B</text>
      <text x="230" y="235" text-anchor="middle" font-size="26" font-weight="700" fill="#EDF2F7">A</text>
    </svg>
    <div style="display:flex;flex-direction:column;gap:26px;">
      <div style="display:flex;align-items:baseline;gap:22px;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:96px;">A &sube; B</div><div style="font-size:24px;color:#DCE3EC;">A is a subset of B (A could equal B)</div></div>
      <div style="display:flex;align-items:baseline;gap:22px;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:96px;">A &sub; B</div><div style="font-size:24px;color:#DCE3EC;">A is a <b style="color:#EDF2F7;">proper</b> subset &mdash; A &ne; B</div></div>
      <div style="font-family:'Roboto Mono',monospace;font-size:24px;color:#93A5BD;margin-top:10px;">example: {strings ending in 01} &sub; {0,1}*</div>
    </div>
  </div>
</div>

<!--
Define subset and proper subset. Give the concrete example with binary strings so it connects to automata immediately.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Sets: The Basics</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">The Power Set</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">The set of <b style="color:#DCE3EC;">all subsets</b> of A, written &Popf;(A).</div>
  <div style="display:flex;gap:64px;align-items:center;flex:1;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:32px 40px;">
      <div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#DCE3EC;margin-bottom:16px;">A = {a, b}</div>
      <div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#6CB6EA;">&Popf;(A) = { &empty;, {a}, {b}, {a,b} }</div>
    </div>
    <div style="display:flex;flex-direction:column;gap:22px;max-width:520px;">
      <div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#EDF2F7;">|&Popf;(A)| = 2^|A|</div>
      <div style="font-size:24px;color:#DCE3EC;line-height:1.5;">Every element is independently in-or-out, so a set of size n has 2<sup>n</sup> subsets.</div>
      <div style="font-size:24px;color:#93A5BD;line-height:1.5;">This is exactly the idea behind the <b style="color:#DCE3EC;">subset construction</b> that converts an NFA into a DFA.</div>
    </div>
  </div>
</div>

<!--
Introduce the power set. This is genuinely new for most students -- flag that it comes up directly when we build the subset construction converting NFAs to DFAs.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:220px;font-weight:700;color:#182740;line-height:1;margin-bottom:8px;">02</div>
  <h2 style="font-size:76px;font-weight:700;color:#EDF2F7;margin:0;">Set Operations</h2>
</div>

<!--
Section break.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Set Operations</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 44px 0;">Union &amp; Intersection</h2>
  <div style="display:flex;gap:80px;justify-content:center;flex:1;align-items:center;">
    <div style="display:flex;flex-direction:column;align-items:center;gap:18px;">
      <svg viewBox="0 0 400 260" style="width:320px;height:208px;">
        <circle cx="150" cy="130" r="100" fill="#6CB6EA" opacity="0.4"/>
        <circle cx="250" cy="130" r="100" fill="#6CB6EA" opacity="0.4"/>
        <circle cx="150" cy="130" r="100" fill="none" stroke="#93A5BD" stroke-width="3"/>
        <circle cx="250" cy="130" r="100" fill="none" stroke="#93A5BD" stroke-width="3"/>
        <text x="110" y="135" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">A</text>
        <text x="290" y="135" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">B</text>
      </svg>
      <div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;">A &cup; B</div>
      <div style="font-size:24px;color:#93A5BD;text-align:center;">in A, or B, or both</div>
    </div>
    <div style="display:flex;flex-direction:column;align-items:center;gap:18px;">
      <svg viewBox="0 0 400 260" style="width:320px;height:208px;">
        <defs><clipPath id="isect"><circle cx="150" cy="130" r="100"/></clipPath></defs>
        <circle cx="150" cy="130" r="100" fill="none" stroke="#93A5BD" stroke-width="3"/>
        <circle cx="250" cy="130" r="100" fill="none" stroke="#93A5BD" stroke-width="3"/>
        <circle cx="250" cy="130" r="100" fill="#6CB6EA" opacity="0.55" clip-path="url(#isect)"/>
        <text x="110" y="135" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">A</text>
        <text x="290" y="135" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">B</text>
      </svg>
      <div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;">A &cap; B</div>
      <div style="font-size:24px;color:#93A5BD;text-align:center;">in both A and B</div>
    </div>
  </div>
</div>

<!--
Union and intersection with Venn diagrams. These are the two operations we'll prove regular languages are closed under.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Set Operations</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 44px 0;">Difference &amp; Complement</h2>
  <div style="display:flex;gap:80px;justify-content:center;flex:1;align-items:center;">
    <div style="display:flex;flex-direction:column;align-items:center;gap:18px;">
      <svg viewBox="0 0 400 260" style="width:320px;height:208px;">
        <circle cx="150" cy="130" r="100" fill="#6CB6EA" opacity="0.4"/>
        <circle cx="250" cy="130" r="100" fill="#111B2C"/>
        <circle cx="150" cy="130" r="100" fill="none" stroke="#93A5BD" stroke-width="3"/>
        <circle cx="250" cy="130" r="100" fill="none" stroke="#93A5BD" stroke-width="3"/>
        <text x="110" y="135" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">A</text>
        <text x="290" y="135" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">B</text>
      </svg>
      <div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;">A &minus; B</div>
      <div style="font-size:24px;color:#93A5BD;text-align:center;">in A, but not in B</div>
    </div>
    <div style="display:flex;flex-direction:column;align-items:center;gap:18px;">
      <svg viewBox="0 0 400 260" style="width:320px;height:208px;">
        <rect x="10" y="10" width="380" height="240" fill="#6CB6EA" opacity="0.28" stroke="#93A5BD" stroke-width="3"/>
        <circle cx="200" cy="130" r="90" fill="#111B2C" stroke="#93A5BD" stroke-width="3"/>
        <text x="200" y="138" text-anchor="middle" font-size="24" font-weight="700" fill="#EDF2F7">A</text>
        <text x="45" y="35" text-anchor="middle" font-size="24" fill="#EDF2F7">&Sigma;*</text>
      </svg>
      <div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;">&Sigma;* &minus; A (or A&#772;)</div>
      <div style="font-size:24px;color:#93A5BD;text-align:center;">everything <b>not</b> in A, relative to the universe</div>
    </div>
  </div>
</div>

<!--
Difference and complement -- complement is what we use to prove regular languages closed under complement, so tie it back explicitly.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Set Operations</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Cartesian Product</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">A &times; B is the set of all ordered pairs (a, b) with a &isin; A, b &isin; B.</div>
  <div style="display:flex;gap:64px;align-items:center;flex:1;">
    <div style="display:flex;flex-direction:column;gap:14px;">
      <div style="font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;">A = {1, 2}&nbsp;&nbsp;&nbsp;B = {x, y}</div>
      <div style="display:grid;grid-template-columns:repeat(2,110px);gap:14px;margin-top:8px;">
        <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:8px;padding:14px;text-align:center;font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;">(1,x)</div>
        <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:8px;padding:14px;text-align:center;font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;">(1,y)</div>
        <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:8px;padding:14px;text-align:center;font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;">(2,x)</div>
        <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:8px;padding:14px;text-align:center;font-family:'Roboto Mono',monospace;font-size:24px;color:#EDF2F7;">(2,y)</div>
      </div>
    </div>
    <div style="display:flex;flex-direction:column;gap:22px;max-width:600px;font-size:26px;color:#DCE3EC;line-height:1.5;">
      <div>Order matters here: (1,x) &ne; (x,1).</div>
      <div style="color:#93A5BD;">This is exactly why a DFA's transition function has signature &delta;: Q &times; &Sigma; &rarr; Q &mdash; it takes an (state, symbol) pair.</div>
    </div>
  </div>
</div>

<!--
Cartesian product -- foreshadow that this is exactly how we'll define the transition function's domain, and the product construction for closure proofs.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Set Operations</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 44px 0;">Infinite Sets: A Quick Preview</h2>
  <div style="display:flex;gap:64px;align-items:center;flex:1;">
    <div style="display:flex;flex-direction:column;gap:26px;max-width:900px;">
      <div style="font-size:28px;color:#DCE3EC;line-height:1.5;">&Sigma;* is infinite &mdash; there's no longest string. But it's <b style="color:#EDF2F7;">countably</b> infinite: we can list every string in some order (by length, then alphabetically).</div>
      <div style="font-size:28px;color:#DCE3EC;line-height:1.5;">That matters because a <b style="color:#EDF2F7;">language</b> is just a subset of &Sigma;* &mdash; and some languages turn out not to be describable by any finite machine.</div>
    </div>
    <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:16px;padding:40px;width:360px;flex-shrink:0;">
      <div style="font-size:24px;color:#6CB6EA;font-weight:700;text-transform:uppercase;letter-spacing:2px;margin-bottom:14px;">Looking ahead</div>
      <div style="font-size:24px;color:#EDF2F7;line-height:1.5;">Countability is why we can even ask "how many languages are there?" &mdash; more later in the course.</div>
    </div>
  </div>
</div>

<!--
Brief teaser on countability -- not a full proof, just enough that students aren't surprised later. Keep light.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:220px;font-weight:700;color:#182740;line-height:1;margin-bottom:8px;">03</div>
  <h2 style="font-size:76px;font-weight:700;color:#EDF2F7;margin:0;">Functions &amp; Relations</h2>
</div>

<!--
Section break.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Functions &amp; Relations</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">What Is a Function?</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:40px;">A <b style="color:#DCE3EC;">relation</b> from A to B is any subset of A &times; B. A <b style="color:#DCE3EC;">function</b> f: A &rarr; B is a relation that assigns <b style="color:#DCE3EC;">exactly one</b> output in B to every input in A.</div>
  <div style="display:flex;gap:64px;align-items:center;flex:1;">
    <svg viewBox="0 0 500 320" style="width:440px;height:282px;">
      <ellipse cx="130" cy="160" rx="100" ry="140" fill="#1A2740" stroke="#93A5BD" stroke-width="3"/>
      <ellipse cx="370" cy="160" rx="100" ry="140" fill="#1A2740" stroke="#93A5BD" stroke-width="3"/>
      <circle cx="130" cy="90" r="8" fill="#6CB6EA"/><circle cx="130" cy="160" r="8" fill="#6CB6EA"/><circle cx="130" cy="230" r="8" fill="#6CB6EA"/>
      <circle cx="370" cy="70" r="8" fill="#93A5BD"/><circle cx="370" cy="140" r="8" fill="#93A5BD"/><circle cx="370" cy="210" r="8" fill="#93A5BD"/><circle cx="370" cy="260" r="8" fill="#93A5BD"/>
      <line x1="130" y1="90" x2="370" y2="140" stroke="#6CB6EA" stroke-width="2"/>
      <line x1="130" y1="160" x2="370" y2="140" stroke="#6CB6EA" stroke-width="2"/>
      <line x1="130" y1="230" x2="370" y2="210" stroke="#6CB6EA" stroke-width="2"/>
      <text x="130" y="30" text-anchor="middle" font-size="24" fill="#EDF2F7" font-weight="700">A</text>
      <text x="370" y="30" text-anchor="middle" font-size="24" fill="#EDF2F7" font-weight="700">B</text>
    </svg>
    <div style="display:flex;flex-direction:column;gap:20px;font-size:26px;color:#DCE3EC;line-height:1.5;max-width:560px;">
      <div>Every dot in A has exactly one arrow out. Multiple dots in A can share a target.</div>
      <div style="color:#93A5BD;">This is precisely why &delta;: Q &times; &Sigma; &rarr; Q must be <b>total</b> and <b>single-valued</b> &mdash; that's what "deterministic" means.</div>
    </div>
  </div>
</div>

<!--
Define function formally: a relation from A to B assigning exactly one output to each input. Contrast with delta being a function specifically.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Functions &amp; Relations</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 44px 0;">Injective, Surjective, Bijective</h2>
  <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:28px;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:28px;">
      <div style="font-size:26px;font-weight:700;color:#EDF2F7;margin-bottom:10px;">Injective</div>
      <div style="font-size:24px;color:#93A5BD;margin-bottom:14px;">one-to-one: no two inputs share an output</div>
      <svg viewBox="0 0 200 140" style="width:150px;"><circle cx="45" cy="35" r="6" fill="#6CB6EA"/><circle cx="45" cy="70" r="6" fill="#6CB6EA"/><circle cx="45" cy="105" r="6" fill="#6CB6EA"/><circle cx="155" cy="20" r="6" fill="#93A5BD"/><circle cx="155" cy="55" r="6" fill="#93A5BD"/><circle cx="155" cy="90" r="6" fill="#93A5BD"/><circle cx="155" cy="120" r="6" fill="#93A5BD"/><line x1="45" y1="35" x2="155" y2="20" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="70" x2="155" y2="55" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="105" x2="155" y2="90" stroke="#6CB6EA" stroke-width="2"/></svg>
    </div>
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:28px;">
      <div style="font-size:26px;font-weight:700;color:#EDF2F7;margin-bottom:10px;">Surjective</div>
      <div style="font-size:24px;color:#93A5BD;margin-bottom:14px;">onto: every output is hit by something</div>
      <svg viewBox="0 0 200 140" style="width:150px;"><circle cx="45" cy="20" r="6" fill="#6CB6EA"/><circle cx="45" cy="55" r="6" fill="#6CB6EA"/><circle cx="45" cy="90" r="6" fill="#6CB6EA"/><circle cx="45" cy="120" r="6" fill="#6CB6EA"/><circle cx="155" cy="35" r="6" fill="#93A5BD"/><circle cx="155" cy="70" r="6" fill="#93A5BD"/><circle cx="155" cy="105" r="6" fill="#93A5BD"/><line x1="45" y1="20" x2="155" y2="35" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="55" x2="155" y2="35" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="90" x2="155" y2="70" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="120" x2="155" y2="105" stroke="#6CB6EA" stroke-width="2"/></svg>
    </div>
    <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:12px;padding:28px;">
      <div style="font-size:26px;font-weight:700;color:#EDF2F7;margin-bottom:10px;">Bijective</div>
      <div style="font-size:24px;color:#DCE3EC;margin-bottom:14px;">both: a perfect pairing, |A| = |B|</div>
      <svg viewBox="0 0 200 140" style="width:150px;"><circle cx="45" cy="30" r="6" fill="#6CB6EA"/><circle cx="45" cy="70" r="6" fill="#6CB6EA"/><circle cx="45" cy="110" r="6" fill="#6CB6EA"/><circle cx="155" cy="30" r="6" fill="#6CB6EA"/><circle cx="155" cy="70" r="6" fill="#6CB6EA"/><circle cx="155" cy="110" r="6" fill="#6CB6EA"/><line x1="45" y1="30" x2="155" y2="30" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="70" x2="155" y2="70" stroke="#6CB6EA" stroke-width="2"/><line x1="45" y1="110" x2="155" y2="110" stroke="#6CB6EA" stroke-width="2"/></svg>
    </div>
  </div>
</div>

<!--
Introduce the three key properties of functions. Bijections come up when proving two sets have the same size, which shows up in cardinality/pumping lemma arguments.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:24px;">Functions &amp; Relations</div>
  <h2 style="font-size:56px;font-weight:700;color:#EDF2F7;margin:0 0 40px 0;max-width:1400px;">This Is the Vocabulary a DFA Is Written In</h2>
  <div style="font-size:30px;color:#93A5BD;line-height:1.6;max-width:1300px;">A DFA's transition function, its extension &delta;&#770;, and later the equivalence relations behind minimizing automata are <b style="color:#EDF2F7;">all</b> just functions and relations on sets. Nothing new happens conceptually &mdash; only the objects (states, strings) change.</div>
</div>

<!--
Tie functions and relations directly to what's coming: delta as a function, delta-hat as its extension, equivalence relations for the Myhill-Nerode theorem later.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:220px;font-weight:700;color:#182740;line-height:1;margin-bottom:8px;">04</div>
  <h2 style="font-size:76px;font-weight:700;color:#EDF2F7;margin:0;">Predicate Logic</h2>
</div>

<!--
Section break.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Predicate Logic</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Propositions &amp; Connectives</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">A <b style="color:#DCE3EC;">proposition</b> is a statement that is either true or false. We combine them with connectives.</div>
  <div style="display:flex;flex-direction:column;">
    <div style="display:flex;align-items:baseline;gap:32px;padding:14px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:104px;">&not;p</div><div style="font-size:24px;color:#DCE3EC;">not &mdash; true when p is false</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:14px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:104px;">p &and; q</div><div style="font-size:24px;color:#DCE3EC;">and &mdash; true only when both are true</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:14px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:104px;">p &or; q</div><div style="font-size:24px;color:#DCE3EC;">or &mdash; true when at least one is true</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:14px 0;border-bottom:1px solid #2C3E56;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:104px;">p &rarr; q</div><div style="font-size:24px;color:#DCE3EC;">implies &mdash; false only when p is true and q is false</div></div>
    <div style="display:flex;align-items:baseline;gap:32px;padding:14px 0;"><div style="font-family:'Roboto Mono',monospace;font-size:28px;color:#6CB6EA;width:104px;">p &harr; q</div><div style="font-size:24px;color:#DCE3EC;">iff &mdash; true when p and q match</div></div>
  </div>
</div>

<!--
Define propositions and the five connectives students need. This is the toolkit for writing precise definitions and proofs.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Predicate Logic</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Truth Tables</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">Implication surprises people &mdash; it's false in exactly <b style="color:#DCE3EC;">one</b> of the four rows.</div>
  <div style="display:flex;gap:64px;align-items:center;flex:1;">
    <table style="border-collapse:collapse;font-family:'Roboto Mono',monospace;font-size:26px;">
      <tr style="background:#1B3350;color:#EDF2F7;"><th style="padding:14px 30px;">p</th><th style="padding:14px 30px;">q</th><th style="padding:14px 30px;">p &rarr; q</th></tr>
      <tr style="border-bottom:1px solid #2C3E56;background:#1A2740;"><td style="padding:12px 30px;color:#DCE3EC;">T</td><td style="padding:12px 30px;color:#DCE3EC;">T</td><td style="padding:12px 30px;color:#6CB6EA;font-weight:700;">T</td></tr>
      <tr style="border-bottom:1px solid #2C3E56;background:#241626;"><td style="padding:12px 30px;color:#DCE3EC;">T</td><td style="padding:12px 30px;color:#DCE3EC;">F</td><td style="padding:12px 30px;color:#E88A8A;font-weight:700;">F</td></tr>
      <tr style="border-bottom:1px solid #2C3E56;background:#1A2740;"><td style="padding:12px 30px;color:#DCE3EC;">F</td><td style="padding:12px 30px;color:#DCE3EC;">T</td><td style="padding:12px 30px;color:#6CB6EA;font-weight:700;">T</td></tr>
      <tr style="background:#1A2740;"><td style="padding:12px 30px;color:#DCE3EC;">F</td><td style="padding:12px 30px;color:#DCE3EC;">F</td><td style="padding:12px 30px;color:#6CB6EA;font-weight:700;">T</td></tr>
    </table>
    <div style="display:flex;flex-direction:column;gap:22px;max-width:540px;font-size:26px;color:#DCE3EC;line-height:1.5;">
      <div>"If p, then q" is only broken when p happens and q doesn't.</div>
      <div style="color:#93A5BD;">If p is false, p &rarr; q is <b style="color:#DCE3EC;">vacuously true</b> &mdash; the exact pattern behind proving &empty; &sube; A for any set A.</div>
    </div>
  </div>
</div>

<!--
Show a real truth table, especially calling out that implication is only false in one row -- this trips students up constantly.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Predicate Logic</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Predicates &amp; Quantifiers</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">A <b style="color:#DCE3EC;">predicate</b> P(x) is a statement whose truth depends on x. Quantifiers say how many x make it true.</div>
  <div style="display:flex;gap:48px;flex:1;align-items:center;">
    <div style="display:flex;flex-direction:column;align-items:center;gap:14px;">
      <svg viewBox="0 0 260 220" style="width:190px;height:161px;">
        <circle cx="130" cy="110" r="100" fill="#111B2C" stroke="#93A5BD" stroke-width="4"/>
        <circle cx="80" cy="80" r="10" fill="#6CB6EA"/><circle cx="130" cy="60" r="10" fill="#6CB6EA"/><circle cx="180" cy="85" r="10" fill="#6CB6EA"/>
        <circle cx="90" cy="140" r="10" fill="#6CB6EA"/><circle cx="150" cy="150" r="10" fill="#6CB6EA"/><circle cx="190" cy="130" r="10" fill="#6CB6EA"/>
      </svg>
      <div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;">&forall;x P(x)</div>
      <div style="font-size:24px;color:#93A5BD;text-align:center;">"for all" &mdash; every dot must satisfy P</div>
    </div>
    <div style="display:flex;flex-direction:column;align-items:center;gap:14px;">
      <svg viewBox="0 0 260 220" style="width:190px;height:161px;">
        <circle cx="130" cy="110" r="100" fill="#111B2C" stroke="#93A5BD" stroke-width="4"/>
        <circle cx="80" cy="80" r="10" fill="#3A4A5F"/><circle cx="130" cy="60" r="10" fill="#6CB6EA"/><circle cx="180" cy="85" r="10" fill="#3A4A5F"/>
        <circle cx="90" cy="140" r="10" fill="#3A4A5F"/><circle cx="150" cy="150" r="10" fill="#3A4A5F"/><circle cx="190" cy="130" r="10" fill="#3A4A5F"/>
      </svg>
      <div style="font-family:'Roboto Mono',monospace;font-size:30px;color:#EDF2F7;">&exist;x P(x)</div>
      <div style="font-size:24px;color:#93A5BD;text-align:center;">"there exists" &mdash; at least one dot suffices</div>
    </div>
    <div style="max-width:460px;font-size:24px;color:#DCE3EC;line-height:1.5;">Example: <span style="font-family:'Roboto Mono',monospace;color:#6CB6EA;">&forall;n &isin; &Nopf;, n &ge; 0</span> is true.<br/><span style="font-family:'Roboto Mono',monospace;color:#6CB6EA;">&exist;n &isin; &Nopf;, n &gt; 100</span> is also true.</div>
  </div>
</div>

<!--
Introduce predicates as functions returning true/false, then the two quantifiers. Central to reading formal definitions like L(M).
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Predicate Logic</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Negating Quantifiers</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">To negate a quantified statement, flip the quantifier and negate what's inside.</div>
  <div style="display:flex;flex-direction:column;gap:20px;">
    <div style="display:flex;align-items:center;gap:24px;background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:22px 30px;">
      <div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#EDF2F7;white-space:nowrap;">&not;(&forall;x P(x))&nbsp;&equiv;&nbsp;&exist;x &not;P(x)</div>
      <div style="font-size:24px;color:#93A5BD;">"not everyone" means "someone doesn't"</div>
    </div>
    <div style="display:flex;align-items:center;gap:24px;background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:22px 30px;">
      <div style="font-family:'Roboto Mono',monospace;font-size:26px;color:#EDF2F7;white-space:nowrap;">&not;(&exist;x P(x))&nbsp;&equiv;&nbsp;&forall;x &not;P(x)</div>
      <div style="font-size:24px;color:#93A5BD;">"no one" means "everyone doesn't"</div>
    </div>
  </div>
  <div style="margin-top:32px;font-size:24px;color:#DCE3EC;line-height:1.5;max-width:1300px;">This is exactly how we'll show a language is <b style="color:#EDF2F7;">not</b> regular: negate "&exist; a DFA that recognizes L" into "&forall; DFAs, some string is misclassified" &mdash; the pumping lemma's whole strategy.</div>
</div>

<!--
This is the slide students most need: negating a quantified statement, and order of nested quantifiers mattering. Directly needed to state what it means for a language to NOT be regular.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:220px;font-weight:700;color:#182740;line-height:1;margin-bottom:8px;">05</div>
  <h2 style="font-size:76px;font-weight:700;color:#EDF2F7;margin:0;">Proof Techniques</h2>
</div>

<!--
Section break.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Proof Techniques</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Direct Proof</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:40px;">Assume the hypothesis is true, then chain logical steps to the conclusion.</div>
  <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:32px 40px;max-width:1300px;">
    <div style="font-size:24px;color:#6CB6EA;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:16px;">Claim: if n is even, n&sup2; is even</div>
    <div style="font-family:'Roboto Mono',monospace;font-size:24px;color:#DCE3EC;line-height:2;">
      n is even &rArr; n = 2k for some k &isin; &Zopf;<br/>
      &rArr; n&sup2; = (2k)&sup2; = 4k&sup2; = 2(2k&sup2;)<br/>
      &rArr; n&sup2; is 2 &times; (an integer) &rArr; n&sup2; is even &#9633;
    </div>
  </div>
</div>

<!--
Direct proof: assume the hypothesis, chain implications to the conclusion. Give a tiny concrete example.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Proof Techniques</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Proof by Contradiction</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:40px;">Assume the <b style="color:#DCE3EC;">opposite</b> of what you want, then derive something impossible.</div>
  <div style="display:flex;gap:56px;align-items:center;">
    <div style="background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:32px 40px;flex:1;">
      <div style="font-size:24px;color:#6CB6EA;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:16px;">Classic example</div>
      <div style="font-size:24px;color:#DCE3EC;line-height:1.7;">Suppose &radic;2 is rational: &radic;2 = a/b in lowest terms.<br/>Then 2b&sup2; = a&sup2;, so a is even &mdash; write a=2c.<br/>Then b is even too. But then a/b wasn't in lowest terms. <b style="color:#EDF2F7;">Contradiction.</b></div>
    </div>
    <div style="background:#1B3350;border:1px solid #3A6C96;border-radius:16px;padding:36px;width:340px;flex-shrink:0;">
      <div style="font-size:24px;color:#6CB6EA;font-weight:700;text-transform:uppercase;letter-spacing:2px;margin-bottom:14px;">Coming up</div>
      <div style="font-size:24px;color:#EDF2F7;line-height:1.5;">The pumping lemma proves a language isn't regular by assuming it IS, then contradicting the lemma.</div>
    </div>
  </div>
</div>

<!--
Proof by contradiction: assume the negation, derive an absurdity. This is the exact shape of pumping lemma proofs coming up.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Proof Techniques</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 8px 0;">Proof by Induction</h2>
  <div style="font-size:28px;color:#93A5BD;margin-bottom:36px;">Prove a statement for <b style="color:#DCE3EC;">every</b> natural number by proving it for 0, and that each case implies the next.</div>
  <div style="display:flex;flex-direction:column;gap:18px;">
    <div style="display:flex;align-items:center;gap:24px;background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:20px 30px;">
      <div style="font-size:24px;font-weight:700;color:#6CB6EA;width:180px;">Base case</div>
      <div style="font-size:24px;color:#DCE3EC;">show the statement holds for n = 0</div>
    </div>
    <div style="display:flex;align-items:center;gap:24px;background:#1A2740;border:1px solid #2C3E56;border-radius:12px;padding:20px 30px;">
      <div style="font-size:24px;font-weight:700;color:#6CB6EA;width:180px;">Inductive step</div>
      <div style="font-size:24px;color:#DCE3EC;">assume it holds for n (the "IH"), prove it for n+1</div>
    </div>
  </div>
  <div style="margin-top:28px;font-size:24px;color:#93A5BD;line-height:1.5;max-width:1300px;">Sound familiar? This is exactly the shape of &delta;&#770;'s definition: a base case (&epsilon;) and a step (wa) &mdash; induction on string length is how we prove things about it.</div>
</div>

<!--
Induction: base case plus inductive step. This is used constantly to prove facts about delta-hat and about all strings of a language.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:24px;">Proof Techniques</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 40px 0;">The Pigeonhole Principle</h2>
  <div style="display:flex;gap:64px;align-items:center;">
    <div style="display:flex;flex-direction:column;gap:24px;max-width:820px;">
      <div style="font-size:30px;color:#DCE3EC;line-height:1.55;">If you put more than n items into n boxes, <b style="color:#EDF2F7;">some box gets at least two</b>.</div>
      <div style="font-size:26px;color:#93A5BD;line-height:1.55;">Obvious, but powerful: it's the entire engine behind the <b style="color:#DCE3EC;">pumping lemma</b>. Run a DFA with n states on a string longer than n symbols, and by pigeonhole some state must repeat.</div>
    </div>
    <svg viewBox="0 0 320 200" style="width:280px;flex-shrink:0;">
      <rect x="10" y="60" width="80" height="80" rx="8" fill="#1A2740" stroke="#93A5BD" stroke-width="3"/>
      <rect x="120" y="60" width="80" height="80" rx="8" fill="#1A2740" stroke="#93A5BD" stroke-width="3"/>
      <rect x="230" y="60" width="80" height="80" rx="8" fill="#1B3350" stroke="#6CB6EA" stroke-width="3"/>
      <circle cx="35" cy="100" r="10" fill="#6CB6EA"/>
      <circle cx="145" cy="100" r="10" fill="#6CB6EA"/>
      <circle cx="255" cy="85" r="10" fill="#6CB6EA"/><circle cx="285" cy="115" r="10" fill="#6CB6EA"/>
    </svg>
  </div>
</div>

<!--
Pigeonhole principle: directly foreshadows the pumping lemma, where more strings than states forces a repeated state.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:220px;font-weight:700;color:#182740;line-height:1;margin-bottom:8px;">06</div>
  <h2 style="font-size:76px;font-weight:700;color:#EDF2F7;margin:0;">Bringing It Together</h2>
</div>

<!--
Section break.
-->

---
class: p-0
---

<div style="background:#111B2C;display:flex;flex-direction:column;padding:100px 140px 80px 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<div style="font-size:24px;letter-spacing:3px;color:#6CB6EA;font-weight:700;text-transform:uppercase;margin-bottom:20px;">Bringing It Together</div>
  <h2 style="font-size:52px;font-weight:700;color:#EDF2F7;margin:0 0 48px 0;">Key Takeaways</h2>
  <div style="display:flex;flex-direction:column;">
    <div style="display:flex;align-items:baseline;gap:28px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="width:14px;height:14px;border-radius:50%;background:#6CB6EA;flex-shrink:0;"></div><div style="font-size:26px;color:#DCE3EC;">Sets and set-builder notation are how we'll define alphabets, languages, and L(M).</div></div>
    <div style="display:flex;align-items:baseline;gap:28px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="width:14px;height:14px;border-radius:50%;background:#6CB6EA;flex-shrink:0;"></div><div style="font-size:26px;color:#DCE3EC;">Functions (and the power set) explain why &delta; is deterministic, and how NFA-to-DFA works.</div></div>
    <div style="display:flex;align-items:baseline;gap:28px;padding:18px 0;border-bottom:1px solid #2C3E56;"><div style="width:14px;height:14px;border-radius:50%;background:#6CB6EA;flex-shrink:0;"></div><div style="font-size:26px;color:#DCE3EC;">Quantifiers and their negations are how we state and disprove "L is regular."</div></div>
    <div style="display:flex;align-items:baseline;gap:28px;padding:18px 0;"><div style="width:14px;height:14px;border-radius:50%;background:#6CB6EA;flex-shrink:0;"></div><div style="font-size:26px;color:#DCE3EC;">Induction, contradiction, and pigeonhole are the three proof techniques you'll reuse most.</div></div>
  </div>
</div>

<!--
Recap all core ideas before wrapping up, explicitly mapping each concept to where it will resurface in the course.
-->

---
class: p-0
---

<div style="background:#0A1220;display:flex;flex-direction:column;justify-content:center;align-items:flex-start;padding:0 140px;font-family:-apple-system,'Helvetica Neue',Arial,sans-serif;height:100%;box-sizing:border-box;">
<img src="./unc-logo.png" alt="UNC logo" style="width:120px;height:auto;border-radius:8px;margin-bottom:56px;" />
  <h1 style="font-size:88px;font-weight:700;color:#EDF2F7;margin:0 0 28px 0;">Questions?</h1>
  <div style="font-size:32px;color:#93A5BD;">Next lecture: deterministic finite automata, built on exactly this vocabulary.</div>
</div>

<!--
Open the floor for questions. Remind students that the next lecture starts formal DFA definitions.
-->

