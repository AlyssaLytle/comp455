---
# try also 'default' to start simple
theme: seriph
title: Time Complexity
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

<!-- pandoc -t slidy -s notes/12-time-complexity-intro.md -o slides/12-time-complexity-intro.html --webtex -->

# Time Complexity

---

# Complexity Theory

<v-clicks>

* We've talked about problems being computationally solvable *in principle*, but what about in practice?
* *Complexity Theory* is the investigation of the time, memory, + other resources required to solve computational problems.
* We will focus on *time complexity*.

</v-clicks>

---

# Importance of Time Complexity

<v-clicks>

* Measures how *long* an algorithm will take to compute. 

* Can consider average case, best case, or worst case scenarios.

* Why is this important?

    * Security: Modern crypto relies on the fact that private keys take too long to compute.

    * User Experience: People want fast interfaces.

    * Safety: Critical systems need to make fast decisions.

</v-clicks>

---

# Some Questions You Can Answer With Time Complexity

<v-clicks>

* Is this problem solvable on a modern computer in a reasonable amount of time?

* Does this problem take as long to solve as this other problem? 

* Is this algorithm faster than this other algorithm?


For this lesson, we will work on formalizing the idea of time complexity to answer these questions directly.
</v-clicks>

<!-- ---

# Big-O Notation

What do you know about Big-O notation + runtime? -->

---

# Time Complexity

<v-clicks>

The main approach to talking about the time complexity to solve a problem is to consider a specific algorithm used to solve it.

"I have a turing machine $M$ that decides problem $A$. How much time does the algorithm for $M$ take to decide $A$?"

Reasoned about as a number of "steps" taken to complete the algorithm. 

Consider the steps taken based on the size of the input.

"How long will it take $M$ to decide if $w$ is in $A$?" will be determined by and expressed in terms of the size of $w$. 

Typically, we use $n = |w|$.

</v-clicks>


---

# Running Time

--

<v-clicks>

Let $M$ be a Turing machine that halts on all inputs. 

The *running time* or *time complexity* of $M$ is the function $f: \mathbb{N} \to \mathbb{N}$, where $f(n)$ is the maximum number of steps that $M$ uses on any input of length $n$. 

If $f(n)$ is the running time of $M$ we say that 

"$M$ runs in time $f(n)$" and that 

"$M$ is an $f(n)$ time Turing machine" 

</v-clicks>

---

# Big-O Notation

<v-clicks>


We typically talk about $f(n)$ in terms of its bounds. 

Can consider average case, best case, or worst case *inputs*. 

"What $w$, with $|w| = n$, will cause $M$ to make the most steps to decide if $w \in A$? How many steps will that be?"

For this lesson, we will focus on worst case runtime, or the upper bound of $f(n)$. 

This is expressed using the *big-O notation* for $f(n)$.

</v-clicks>


---

# Big-O Notation

--

<v-clicks>

Let $f$ and $g$ be functions, $f,g: \mathbb{N} \to \mathbb{R}^+$. Say that $f(n) = O(g(n))$ if positive integers $c$ and $n_0$ exist such that for every integer $n \geq n_0$,

$$f(n) \leq c g(n).$$ 

$g(n)$ is an "upper bound" for $f(n)$.

Essentially, this means $f(n)$ is less than or equal to $g(n)$ for a high enough $n$ if we ignore constants.

</v-clicks>

---

# Determining g



Generally, $g$ is determined by choosing the highest order term and suppressing its constant.

Example: 

<v-clicks>

* $f(n) = 5n^3 + 2n^2 + 22n + 6$
* choose highest order term $5n^3$ 
* supressing the constant $5$. 
* So, $g(n) = n^3$ and $f(n) = O(g(n)) = O(n^3)$. 

</v-clicks>


---

# Example

--

<v-clicks>

For any $f(n) = O(\log_x n)$ we can write $f(n) = O(\log n)$. In other words we can suppress the log base. Why?

We can use the fact that $\log_b n = \frac{\log_x n}{\log_x b}$. 

Therefore, $\log_x n = (\log_b n)(\log_x b)$. 

Since $\log_x b$ is a constant, $\log_x n = O(\log_b n)$ 
</v-clicks>

<!-- 
---

# Example: Selection Sort

    def selection_sort(items: list[int]) -> list[int]:
    """Repeatedly pull out the minimum."""
    # Outer loop keeps track of how far we've sorted
    outer_idx: int = 0
    while outer_idx < len(items):
        # Inner loop repeatedly finds the minimum
        inner_idx: int = outer_idx
        min_index: int = outer_idx
        while inner_idx < len(items):
            # Finding the minimum
            if items[inner_idx] < items[min_index]:
                min = items[inner_idx]
                min_index = inner_idx
            inner_idx += 1
        # Swap the minimum with the first unsorted element
        min = items[min_index]
        items[min_index] = items[outer_idx] 
        items[outer_idx] = min 
        outer_idx += 1
    return items -->

---

# Small-o Notation

--

<v-clicks>

Another definition that may be useful is small-o notation, or $o(n)$. This essentially lets you express that $f(n)$ is strictly smaller than $g(n)$.


et $f$ and $g$ be functions, $f,g: \mathbb{N} \to \mathbb{R}^+$. Say that $f(n) = o(g(n))$ if

$$\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0.$$ 


In other words, $f(n) = o(g(n))$ if positive integers $c$ and $n_0$ exist such that for every integer $n \geq n_0, f(n) < c g(n).$ 

</v-clicks>

---

# Common Runtimes


<img src="/public/big-o-runtimes.png" width="500"/>




---

# Time Complexity Classes

--

<v-clicks>

Let $t: \mathbb{N} \to \mathbb{R}^+$ be a function. Define the *time complexity class*, $\textrm{TIME}(t(n))$, to be the collection of all languages that are decidable by an $O(t(n))$ time Turing Machine. 

Example: 

* $\textrm{TIME}(n^2)$ contains all languages that can be decided in $O(n^2)$ time.
* So, if there exists a machine $M$ that decides $A$ in time $O(n^2)$, we say $A \in \textrm{TIME}(n^2)$

</v-clicks>


---

# Time Complexity Class P

--

<v-clicks>

Now, we will introduce the class of languages decidable in polynomial time, P.


P is the class of languages that are decidable in polynomial time on a deterministic single-tape Turing machine. 

In other words, 

$$P = \bigcup_k \textrm{TIME}(n^k).$$ 


P is important because it describes the class of problems that are realistically solvable on a computer.

</v-clicks>

---

# Problems in P

<v-clicks>

Now we can talk about some examples of problems that are in P and show how we can prove this. 

We prove a problem is in P by presenting an algorithm to solve it in polynomial time. 

Essentially for our proof we should:


1. Express our problem as a language $A$
2. Present a Turing machine computable algorithm $M$ that decides $A$
3. Argue the runtime of $M$

</v-clicks>


---

# Example

--

<v-clicks>

Say we have a directed graph $G$ that contains nodes $s$ and $t$. The problem we want to solve is whether or not there exists a direct path from $s$ to $t$ in $G$.

So, first let's express this as a language:

$$PATH = \{\langle G, s, t \rangle | G \textrm{ is a directed graph that has a directed path from $s$ to $t$} \}$$

Now, let's define an algorithm $M$ to decide this. 

</v-clicks>

---

# PATH Algorithm




$${1|1-2|1-5|1-6}
\begin{align*}
M = & \textrm{``On input $\langle G, s, t \rangle$,}\\
& 1. \textrm{ Place a mark on node $s$}\\
& 2. \textrm{ Repeat until no additional nodes are marked:} \\
& 3. \hspace{10pt} \textrm{Scan all edges of $G$. If an edge $(a,b)$ is found going from a marked node $a$} \\
& \hspace{20pt} \textrm{to an unmarked node $b$, mark node $b$.} \\
& 4. \textrm{ If $t$ is marked, \emph{accept}. Otherwise, \emph{reject}.''}
\end{align*}$$

Finally, we have to argue that $M$ is in P by reasoning about its runtime.

<v-clicks>

Steps 1 and 4 are only computed once. Step 3 is potentially repeated once for every node in $G$, so $m$ for $m$ nodes in $G$.
Therefore the total runtime is <span v-mark="{color: 'orange', type: 'underline' }">$1 + 1 + m$</span>. 

Let $n$ be the length of $\langle G, s, t \rangle$. Since $m$ is the number of nodes in $G$, $n$ is directly dependent on $m$,<br> so $1 + 1 + m  = O(n)$. 

Note if we did this by brute force, the number of potential paths over each node is $m^m$ so that's a lot of searching... and not in $P$! 
</v-clicks>


---

# Relatively Prime Numbers

--

<v-clicks>

Say our problem is: I want to know if two integers $x$ and $y$ are relatively prime.
    
We can define our language as $\textit{RELPRIME} = \{\langle x,y \rangle ~|~ x$ and $y$ are relatively prime $\}$.

Recall Euclidean Algorithm: $(x,y) \to (y, x \bmod y)$

$${1|1-2|1-3|1-4|1-5}
\begin{align*}
       R = &\textrm{ ``On input $\langle x,y \rangle$, }\\
       &1. \textrm{ Repeat until $y=0$:}\\
        &2. \hspace{10pt} \textrm{ Assign $x \leftarrow x \bmod y$}\\
        &3. \hspace{10pt} \textrm{ Swap $x$ and $y$}\\
        &4. \textrm{ If $x$ is $1$, \emph{accept}. Otherwise, \emph{reject}.''}
\end{align*}$$
        
Runtime: If we assume the $\bmod$ operation is constant time, then the runtime is bounded by the minimum of $x$ and $y$.

Let $n$ be the length of $\langle x, y \rangle$. This algorithm is in $O(n)$.

</v-clicks>