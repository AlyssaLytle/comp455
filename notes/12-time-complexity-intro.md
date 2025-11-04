---
title: "Introduction to Time Complexity"
author: "Alyssa Lytle"
date: "October 23, 2025"
---

<!-- pandoc -t slidy -s notes/12-time-complexity-intro.md -o slides/12-time-complexity-intro.html --webtex -->

# Time Complexity

## Complexity Theory

* We've talked about problems being computationally solvable *in principle*, but what about in practice?
* *Complexity Theory* is the investigation of the time, memory, + other resources required to solve computational problems.
* We will focus on *time complexity*.

## Importance of Time Complexity

* Measures how *long* an algorithm will take to compute. 

* Can consider average case, best case, or worst case scenarios.

* Why is this important?

    * Security: Modern crypto relies on the fact that private keys take too long to compute.

    * User Experience: People want fast interfaces.

    * Safety: Critical systems need to make fast decisions.

## Some Questions You Can Answer With Time Complexity

* Is this problem solvable on a modern computer in a reasonable amount of time?

* Does this problem take as long to solve as this other problem? 

* Is this algorithm faster than this other algorithm?


For this lesson, we will work on formalizing the idea of time complexity to answer these questions directly.


## Big-O Notation

What do you know about Big-O notation + runtime?

## Time Complexity

The main approach to talking about the time complexity to solve a problem is to consider a specific algorithm used to solve it.

"I have a turing machine $M$ that decides problem $A$. How much time does the algorithm for $M$ take to decide $A$?"

Reasoned about as a number of "steps" taken to complete the algorithm. 

Consider the steps taken based on the size of the input.

"How long will it take $M$ to decide if $w$ is in $A$?" will be determined by and expressed in terms of the size of $w$. 

Typically, we use $n = |w|$.


## Running Time

Let $M$ be a Turing machine that halts on all inputs. 

The *running time* or *time complexity* of $M$ is the function $f: \mathbb{N} \to \mathbb{N}$, where $f(n)$ is the maximum number of steps that $M$ uses on any input of length $n$. 

If $f(n)$ is the running time of $M$ we say that 

"$M$ runs in time $f(n)$" and that 

"$M$ is an $f(n)$ time Turing machine" 

## Big-O Notation


We typically talk about $f(n)$ in terms of its bounds. 

Can consider average case, best case, or worst case *inputs*. 

"What $w$, with $|w| = n$, will cause $M$ to make the most steps to decide if $w \in A$? How many steps will that be?"

For this lesson, we will focus on worst case runtime, or the upper bound of $f(n)$. 

This is expressed using the *big-O notation* for $f(n)$.


## Big-O Notation

Let $f$ and $g$ be functions, $f,g: \mathbb{N} \to \mathbb{R}^+$. Say that $f(n) = O(g(n))$ if positive integers $c$ and $n_0$ exist such that for every integer $n \geq n_0$,

$$f(n) \leq c g(n).$$ 

$g(n)$ is an "upper bound" for $f(n)$.

Essentially, this means $f(n)$ is less than or equal to $g(n)$ for a high enough $n$ if we ignore constants.

## Determining g

Generally, $g$ is determined by choosing the highest order term and suppressing its constant.

Example: 

* $f(n) = 5n^3 + 2n^2 + 22n + 6$
* choose highest order term $5n^3$ 
* supressing the constant $5$. 
* So, $g(n) = n^3$ and $f(n) = O(g(n)) = O(n^3)$. 


## Example

For any $f(n) = O(\log_x n)$ we can write $f(n) = O(\log n)$. In other words we can suppress the log base. Why?

<!-- ## Example

For any $f(n) = O(\log_x n)$ we can write $f(n) = O(\log n)$. In other words we can suppress the log base. Why?

    We can use the fact that $\log_b n = \frac{\log_x n}{\log_x b} $. Therefore, $\log_x n = (\log_b n)(\log_x b)$. Since $\log_x b$ is a constant, $\log_x n = O(\log_b n)$ -->

## Example: Selection Sort

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
    return items

## Small-o Notation

Another definition that may be useful is small-o notation, or $o(n)$. This essentially lets you express that $f(n)$ is strictly smaller than $g(n)$.


et $f$ and $g$ be functions, $f,g: \mathbb{N} \to \mathbb{R}^+$. Say that $f(n) = o(g(n))$ if

$$\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0.$$ 


In other words, $f(n) = o(g(n))$ if positive integers $c$ and $n_0$ exist such that for every integer $n \geq n_0, f(n) < c g(n).$ 

## Common Runtimes


![](../static/slide_figs/big-o-runtimes.png)


## Time Complexity Classes


Let $t: \mathbb{N} \to \mathbb{R}^+$ be a function. Define the *time complexity class*, $\textrm{TIME}(t(n))$, to be the collection of all languages that are decidable by an $O(t(n))$ time Turing Machine. 

Example: 

* $\textrm{TIME}(n^2)$ contains all languages that can be decided in $O(n^2)$ time.
* So, if there exists a machine $M$ that decides $A$ in time $O(n^2)$, we say $A \in \textrm{TIME}(n^2)$


## Time Complexity Class P

Now, we will introduce the class of languages decidable in polynomial time, P.


P is the class of languages that are decidable in polynomial time on a deterministic single-tape Turing machine. 

In other words, 

$$P = \bigcup_k \textrm{TIME}(n^k).$$ 


P is important because it describes the class of problems that are realistically solvable on a computer.

## Problems in P

Now we can talk about some examples of problems that are in P and show how we can prove this. We prove a problem is in P by presenting an algorithm to solve it in polynomial time. 

Essentially for our proof we should:


1. Express our problem as a language $A$
2. Present an Turing machine computable algorithm $M$ that decides $A$
3. Argue the runtime of $M$



## Example

Say we have a directed graph $G$ that contains nodes $s$ and $t$. The problem we want to solve is whether or not there exists a direct path from $s$ to $t$ in $G$.

    