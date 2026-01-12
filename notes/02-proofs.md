% Proofs Review
% Alyssa Lytle
% January 13, 2026

<!-- pandoc -t slidy -s notes/02-proofs.md -o slides/02-proofs.html --webtex -->
<!-- pandoc notes/02-proofs.md -o pdfs/01-proofs.pdf --webtex  -->
<!-- pandoc notes/02-proofs.md -o pdfs/01-proofs.tex  -->







## Proofs

- Proofs are useful because they let you say something about the tools you're using and building! 
- In the real world, this is useful because it helps you explain your work and really convince people of your contribution.
- Proofs are also helpful because they force you to write down your thoughts. In writing down your thoughts, you might find out that your thinking is flawed or you're making assumptions where you shouldn't.  
- Examples of some things that you might prove:
   - This cryptography scheme is secure.
   - This new algorithm is the fastest out there.
   - This network will lose less than $.001 \%$ of the messages sent over it.
   - This new robot won't become sentient and kill you.



## What a proof looks like


- A good proof is like good code, clear and easy to follow! 
- Think of narrating your proof like commenting your code--you want the next person to read it to be able to follow your train of thought.
- I'm going to introduce a specific format for writing proofs. *You do not have to use this format for this course*, but it can be useful to make sure you are fully documenting and explaining your proofs. It also gives a linear structure to your argument.





## What a proof looks like


The two column format looks like this: 

$\begin{array}{l l l}
 & \textrm{Column 1} & \textrm{Column 2} \\
 \hline
    1. & \textrm{Your conclusion} & \textrm{How you came to that conclusion}  \\
     2. & \ldots\\
     3. & \ldots\\
     \vdots \\
      \square 
 \end{array}$
 



## Finding P and Q


### Example

- "If $x$ is even, $x^2$ is even." 
- $P:$ $x$ is even 
- $Q:$ $x^2$ is even
    



## Finding P and Q


### Example


- "There are infinitely many primes." 
- This can be restated as "For all $a \in \mathbb{Z}$, if $a$ is prime, then there exists a prime $b \in \mathbb{Z}$ such that $b>a$.''  
- $P:$ $a \in \mathbb{Z}$ is prime 
- $Q:$ There exists $b \in \mathbb{Z}$ such that $b>a$ 




## Finding P and Q


### Example
   
- "$x-1 < \left \lfloor{x}\right \rfloor$" 
- $P:$ Everything you know about math is true 
- $Q:$ $x-1 < \left \lfloor{x}\right \rfloor$
    




## Rewrites

Here are some common rewrites you might see when constructing your proofs:

- $n$ is an even integer converts to $n = 2t$ for some $t$
- $n$ is an odd integer converts to $n = 2t + 1$ for some $t$
- $n$ is a rational number converts to $n = \frac{a}{b}$ where $a$ and $b$ are integers
- $n$ divides $m$ converts to $m = nt$ for some integer $t$
- $n$ is a square converts to $n = t^2$ for some integer $t$.
- $n = a \bmod b$ converts to $n = bt + a$ for some integer $t$.


 
## Main Types of Proofs

The four typical ways we show $P \implies Q$ are the following:

- Direct Proof

- Proof By Contradiction

- Proof By Contrapositive

- Proof By Counterexample

- Proof By Induction


## Types of Proofs - Direct

 
 The first type of proof we will discuss is called a **direct proof**. Basically, we are trying to to prove $p  \rightarrow q$ by starting at $p$ and getting to $q$.
 
 For example, say we want to prove the following: "If $x$ is even, $x^2$ is even". 
 
 Then $p$ is "$x$ is even" and $q$ is "$x^2$ is even"
 
 
 




## Types of Proofs - Direct

 
 The first type of proof we will discuss is called a **direct proof**. Basically, we are trying to to prove $p  \rightarrow q$ by starting at $p$ and getting to $q$.
 
 For example, say we want to prove the following: "If $x$ is even, $x^2$ is even". 
 
 Then $p$ is "$x$ is even" and $q$ is "$x^2$ is even"
 
$\begin{array}{l l l}
      1. & x \textrm{ is even} & \textrm{Given (In other words, this is our } p \textrm{)}\\
      2. & x = 2k, {} k \in \mathbb{Z} & \textrm{Definition of Even Number}\\
      3. & x^2 = (2k)^2 & \textrm{Squared both sides of Line 2} \\
      4. & x^2 = 4k^2 & \textrm{Simplified Line 3} \\
      5. & x^2 = 2(2k^2) & \textrm{Rewrote Line 4} \\
      6. & x^2 \textrm{ is even} & \textrm{Definition of Even Number } \square
    \end{array}$
    
**Note that at every step you're basically saying, "Therefore..." this is where your implication $\rightarrow$ is coming in.**






<!-- ## Example Proof


We want to show $x-1 < \left \lfloor{x}\right \rfloor$






## Example Proof


We want to show $x-1 < \left \lfloor{x}\right \rfloor$

 $\begin{array}{l l l}
     1. & x = y + d, y \in \mathbb{Z}, d \in [0,1) & \textrm{Rewrite of x}  \\
     2. & d < 1 & \textrm{Defined in Line 1}\\
     3. & d - 1 < 0 & \textrm{Subtracted }1 \textrm{ from both sides of Line 2}\\
     4. & y + d - 1 < y & \textrm{Added } y \textrm{ to both sides}\\
     5. & x - 1 < y & \textrm{Plugged in Line 1 to Line 4.} \\
     6. & y = \left \lfloor{x}\right \rfloor & \textrm{Applied definition of floor to line 1.} \\
     7. & x - 1 < \left \lfloor{x}\right \rfloor & \textrm{Plugged line 6 into line 5. } \square 
 \end{array}$  
 
 **Note that this is still a direct proof ($p  \rightarrow q$) but $p$ is never directly stated. If $p$ is never directly stated, you can just think of $p$ as your set of knowledge of the world.** -->
 






## Proof By Contradiction

- $P \implies Q \equiv \neg(P \land \neg Q)$. 

- This leads to why we do proofs by contradiction. 

- Instead of proving $P \implies Q$, we prove $P \land \neg Q$ does not hold. 

- In other words, we start with $P \land \neg Q$ and get to an impossible state $\bot$. 

### Example 

- A famous proof is the proof that $\sqrt{2}$ is irrational.



## Proof By Contradiction - Example

- We want to prove: If $x^2$ is odd, $x$ is odd.  

<!-- ## Contradiction Example:

For this proof we are going to use the following statement: 

**Squared Evens Rule:** If $x^2$ is even, then $x$ is even.

Additionally, recall the definition of a rational number:

A rational number can be written as $\frac{a}{b}$ such that $a, b \in \mathbb{Z}$ and $GCD(a,b)=1$.

## Contradiction Example

\begin{equation*}
\begin{array}{l l l}
   1. &  \sqrt{2} \textrm{ is rational}  &  \textrm{Assumption} \\
   2.  & \sqrt{2} = \frac{a}{b} \land a,b \in \mathbb{Z} \land GCD(a,b) = 1 & \textrm{Definition of Rational Numbers} \\
   3. & \sqrt{2} b = a & \textrm{Took left side of 2. and multiplied both sides by } b \\
   4. & 2 b^2 = a^2 & \textrm{Squared both sides} \\
   5. & a^2 \textrm{ is even} & \textrm{Definition of even number} \\
   6. & a \textrm{ is even} & \textrm{Squared Evens Rule}\\
   7. & a = 2k \land k \in \mathbb{Z}  & \textrm{Definition of even number}\\
   8. & 2b^2 = (2k)^2 & \textrm{Plugged in 7. to 4.}\\
   9. & 2b^2 = 4k^2 & \textrm{Simplified}\\
   10. & b^2 = 2k^2 & \textrm{Divided both sides by } 2 \\
   11. & b^2 \textrm{ is even} & \textrm{Definition of even number} \\
   12. & b \textrm{ is even} & \textrm{Squared Evens Rule}\\
   13. & b= 2m \land m \in \mathbb{Z}  & \textrm{Definition of even number}\\
   14. & 2 \textrm{ is a factor of both } a \textrm{ and } b & \textrm{Lines 7. and 13.} \\
   15. & \bot & \textrm{Lines 2. and 14. contradict each other } \square
\end{array}
\end{equation*} -->

## Proof by Contrapositive

For a proof of contrapositive, you're going to use the equality we proved last class: 

$P \implies Q \equiv \neg Q \implies \neg P$.

In other words, instead of proving $P \implies Q$, we are going to assume $\neg Q$ and show that it leads to $\neg P$.



### Example 
- We want to prove: If $x^2$ is odd, $x$ is odd.  



## Proof by Counterexample

If you want to disprove something, the easiest way is usually by counter example. 

You don't have to do this in the typical two column format as long as you make your reasoning clear.

### Example

- Say I ask you to prove the following is false: If $x$ is even, $x^2$ is odd.



## Other Types of Proofs

You may see some other types of proofs that follow from the types of proofs we've already discussed. 


- Forall
    - Exhaustive
        - Proof by Cases
- Existence
    - Proof by Construction
    
    
<!-- ## Biconditional Proofs

- For our proofs, we are basically writing a $\implies$ to get from line to line.

- Sometimes, instead of proving $P \implies Q$, you'll want to prove $P \iff Q$. 

- The benefit of this type of proof is that you can start from $P$ or $Q$ to get to the other side. This is because $P \iff Q$  is the same as saying $Q \iff P$. 

- The added requirement is that you have to use $\iff$ rules to get from line to line. Thankfully, most definitions are actually defined using $\iff$. -->

<!-- ## Biconditional Proofs


### Example
We want to prove $x \in \overline{A \cap B} \iff x \in \bar{A} \cup \bar{B}$




## Logical Equivalence
Proofs of logical equivalence are of the form $P \iff Q$. 

Why? Remember that if $P \equiv Q$, then $P \iff Q$ is always true!


### Example
Say we want to prove $a \implies b \equiv \neg b \implies \neg a$.

So we can say $P: a \implies b$ and $Q: \neg b \implies \neg a$.

First, let's do this proof starting at $P$ to get to $Q$.
 
<!-- \begin{equation*}
\begin{array}{l l l}
    1. & a \implies b & \textrm{Given } (P) \\
    2. & \equiv \neg a \lor b & \textrm{Implication Definition} \\
    3. & \equiv b \lor \neg a & \textrm{Commutativity} \\
    4. & \equiv \neg (\neg b) \lor \neg a & \textrm{Double Negation} \\
    5. & \equiv \neg b \implies \neg a & \textrm{Implication Definition }  \square ~ (Q)~ \\ 
\end{array}
\end{equation*} -->

<!-- ## Logical Equivalence Cont.

As previously stated, we can also start at $Q$ to get to $P$.  -->

<!-- \begin{equation*}
\begin{array}{l l l}
    1. & \equiv \neg b \implies \neg a & \textrm{Given } (Q) \\
    2. & \equiv \neg \neg b \lor \neg a & \textrm{Implication Definition}\\
    3. & \equiv b \lor \neg a & \textrm{Double Negation} \\ 
    4. & \equiv \neg a \lor b & \textrm{Commutativity} \\
    5. & \equiv a \implies b & \textrm{Implication Definition } \square ~ (P)    \\ 
\end{array}
\end{equation*} -->

<!-- Either of these proofs are acceptable because they are saying the same thing! Which side you want to start at is really a personal preference. -->


## Forall


You may want to prove statements such as "$\forall x \in S, P(x) \implies Q(x)$."

As previously discussed, to prove a "for all" statement, you want to look at every element in $S$ and show that $P(x) \implies Q(x)$ holds. 

You can often do this with a direct proof. All of the things we've directly proved so far are actually "for all" proofs.

- $\forall x \in \mathbb{Z}$, If $x$ is even, $x^2$ is even
- $\forall x \in \mathbb{Z}, {} x-1 < \left \lfloor{x}\right \rfloor$
- $\forall a,b,c \in \{\texttt{True}, \texttt{False}\}, {} \neg a \lor \neg(b \land \neg c) \equiv a \implies (b \implies c)$
- $\forall a,b,c \in \mathbb{Z}$, if $a \mid b$ and $b \mid c$, then $a \mid c$

## Forall, Exhaustive

However, we can also prove "for all" statements by exhaustively looking at every element in $S$ and checking if $P(x)$ holds.

Fittingly, this is called a **Proof by Exhaustion**.

A good example is the set problem you've already seen:

- $F = \{$Erik, Jos&eacute;, Nicoleta, Aksana$\}$
- $V = \{$Aksana, Erik$\}$ is the set of your friends who are vegetarian
- $N = \{$Aksana$\}$ is the set of your friends who are vegan
- We want to prove: $\forall x \in F,{} x \in N \implies x \in V$




## Proof by Cases

A **Proof by Cases** is a kind of proof by exhaustion. You are breaking the set you are proving something about into smaller sets.

A good example is when we proved the definition of absolute value.

$|x| = sgn(x) \cdot x$

$sgn(x) = \begin{cases}
    -1 & x<0\\
    0 & x =0\\
    1 & x>0
    \end{cases}$
    
## Proof by Cases

A **Proof by Cases** is a kind of proof by exhaustion. You are breaking the set you are proving something about into smaller sets.

A good example is when we proved the definition of absolute value.

$|x| = sgn(x) \cdot x$

$sgn(x) = \begin{cases}
    -1 & x<0\\
    0 & x =0\\
    1 & x>0
    \end{cases}$
    
Case 1: $x > 0$

$\begin{array}{l l l}
      1. & x > 0   & \textrm{Case Assertion} \\
      2. & sgn(x) = 1  & \textrm{Signum Def.} \\
      3. & sgn(x) \cdot x = x & \textrm{Multiply both sides by } x \\
      4. & |x| = x & \textrm{Applied Def. of Absolute Value to Line 1} \\
      5. & sgn(x) = |x| & \textrm{Compared Lines 3 and 5} \\
    \end{array}$


## Proof by Cases Cont.

Case 2: $x = 0$

$\begin{array}{l l l}
      1. & x = 0   & \textrm{Case Assertion} \\
      2. & sgn(x) = 0  & \textrm{Signum Def.} \\
      3. & sgn(x) \cdot x = 0 & \textrm{Multiply both sides by } x \\
      4. & |x| = 0 & \textrm{Applied Def. of Absolute Value to Line 1} \\
      5. & sgn(x) = |x| & \textrm{Compared Lines 3 and 5} \\
    \end{array}$

Case 3: $x < 0$

$\begin{array}{l l l}
      1. & x < 0   & \textrm{Case Assertion} \\
      2. & sgn(x) = -1  & \textrm{Signum Def.} \\
      3. & sgn(x) \cdot x = -x & \textrm{Multiply both sides by } x \\
      4. & |x| = -x & \textrm{Applied Def. of Absolute Value to Line 1} \\
      5. & sgn(x) = |x| & \textrm{Compared Lines 3 and 5} \\
    \end{array}$

## Proof of Existence

Sometimes you just need to prove the existence of something. 

$\exists x \in S, {} P(x)$.

Again, like we discussed in class, you can show the existence of something by looking at every element of the set and finding an $x$ such that $P(x)$ is true. 

Let's go back to our food example:

- $F = \{$Erik, Jos&eacute;, Nicoleta, Aksana$\}$
- $V = \{$Aksana, Erik$\}$ is the set of your friends who are vegetarian
- $N = \{$Aksana$\}$ is the set of your friends who are vegan
- We want to prove: $\exists x \in F,{} x \in N \implies x \in V$





## Proof of Existence - Constructive Proof

Sometimes you will have to prove the existence of more complicated things. You might have to *construct* a solution and then prove it's a valid solution. 

This can also be called a **constructive proof** or **proof by construction** because you are literally constructing your own example.

## Proof by Construction - Example 

For example, you might want to argue the usefulness of exponential encryption by proving that exponential encryption can be decrypted:

$\exists e,d,x,N \in \mathbb{Z}, {} x^{e \cdot d} \bmod N = x$

You can do this by using RSA as an example:

### Construction

- $N = p \cdot q$
- $e \cdot d = 1 \bmod (p-1)(q-1)$

### Proof 

Plug in $N = p \cdot q$ and $e \cdot d = 1 \bmod (p-1)(q-1)$ to demonstrate $x^{e \cdot d} \bmod N = x$.



## Proof by Induction

## (Strong) Induction


- Induction is a type of proof we can do on recursively defined functions and sets
- Say we are trying to prove $R(x)$ holds in a recursively defined set $S = \{S_0, S_1, S_2, \ldots \}$
- We can prove this by:
    1. Showing $R(x)$ holds for the base case(s) of $S$
    2. Assuming $R(k)$ holds for all $k < n$ in the recursive rule, showing that it also holds for step $n$. 
    In other words, we're showing $\big(R(S_0) \land R(S_1) \land \ldots \land R(S_{n-2}) \land R(S_{n-1})\big) \implies R(S_{n})$.   
- Remember that many things can be defined recursively, so even though $x \in S$, $x$ isn't necessarily a single element. $x$ can also be a set/function/mapping etc! Think about our recursive powersets definition.




## Let's Start With an Example






## Example with Template



Recall the Fibonacci series...


- The base case: $F(0) = 0, F(1) = 1$
- Recursive rule: For $n > 1$, $F(n) = F(n-1) + F(n-2)$.


We want to prove the following about the sum of the first $n$ numbers of the series:

$\forall n \in \mathbb{N}, F(0) + F(1) + F(2) + \ldots + F(n-1) + F(n) = F(n+2) - 1$.





## Example with Template


S1. State the ‘for all’ statement that you want to prove:

- $\forall n \in \mathbb{N}, \sum_{i=0}^n F(i) = F(n+2) - 1$.

S2. Say “we prove this by induction on” and state the induction parameter.

- We prove this by induction on $n$.





## Example with Template


S3. Prove the base case(s).

- $n=0$:
    - $F(0) = F(2) - 1$
    - $0 = 0$ $\square$
- $n = 1$:
    - $F(0) + F(1) = F(3) - 1$
    - $1 = 2 - 1$ $\square$
        




## Example with Template


S4. Write Induction Step.

- For a given $n > 1$,

S5. State the Induction Hypothesis (IH)

- I can assume for all $1 \leq k \leq n$ that $\sum_{i=0}^k F(i) = F(k+2) - 1$,

S6. State what you are going to prove about your specific value of $x$ that
was given to you in S4:

- and I want to prove $\sum_{i=0}^n F(i) = F(n+2) - 1$.



## Example with Template


S7. Do the proof for the specific $x$.



## Example with Template


S7. Do the proof for the specific $x$.

$\begin{array}{l l l}
        1. & \forall 1 \leq k \leq n, {} \sum_{i=0}^k F(i) = F(k+2) - 1 & \textrm{IH} \\
        2. & \textrm{Let } k = n - 1, \textrm{ then } \sum_{i=0}^{n-1} F(i) = F(n-1+2) - 1 & \textrm{Applied IH} \\
        3. & \sum_{i=0}^{n-1} F(i) = F(n+1) - 1 & \textrm{Rewrote Line 2}\\
        4. & \sum_{i=0}^{n-1} F(i) + F(n) = F(n+1) - 1 + F(n) & \textrm{Added } F(n) \textrm{ to both sides.}\\
        5. & F(n+2) = F(n+1) + F(n) & \textrm{Fibonacci Def.}\\
        6. & \sum_{i=0}^{n-1} F(i) + F(n) = F(n+2) - 1 & \textrm{Plugged 5. into 4.}\\
        7. & \sum_{i=0}^n F(i) = \sum_{i=0}^{n-1} F(i) + F(n) & \textrm{Def. of Sum} \\
        8. & \sum_{i=0}^{n} F(i) = F(n+2) - 1 & \textrm{Plugged 7. into 6.} \square
    \end{array}$






## Example with Template


S8. Declare victory.

- Therefore, we have proved  $\forall n \in \mathbb{N}, F(0) + F(1) + F(2) + \ldots + F(n-1) + F(n) = F(n+2) - 1$.






## Tips for Proving Something by Induction (S7)


- Your Inductive Hypothesis (Step 5) should be line 1 in your proof.
- The recursive definition of any structures you're using (e.g. sum, factorial, exponents, etc.) should be the next lines of your proof.
- Step 6 is what the *last* line of your proof should be.
- To start, think about how you can use your inductive hypothesis and recursive definitions to get to step 6. (Usually this means plugging a smaller version of $x$ into your inductive hypothesis and using your recursive definitions to rewrite it.)
