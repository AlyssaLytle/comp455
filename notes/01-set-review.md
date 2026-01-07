% Set Notation Review
% Alyssa Lytle
% January 8, 2026

<!-- pandoc -t slidy -s notes/01-set-review.md -o slides/01-sets.html --webtex -->


# Review: Set Notation and Operations


## Sets - Definitions

A ***set*** is an unordered collection of objects.

The following are sets:

-  $\{1,2,3\}$
-  "all multiples of 7''
-  \{apples, $7$, $\texttt{True}$\}

Sets don't inherently have an order.

## Sets - Terminology

A set is a ***finite set*** if it has a finite number of elements. 

Any set that is not finite is an ***infinite set***.

Let $A$ be a finite set. The number of different elements in $A$ is called its ***cardinality***. 

The cardinality of a finite set  is denoted $|A|$.

### Examples
>$\{1,2,3\}$ is a finite set. Its cardinality is $3$.

>"all multiples of 7" is an infinite set. 



## Sets - Notation
$a \in A$ means $a$ is an element of $A$.

$a \notin A$ means $a$ is *not* an element of $A$.


### Example

>Let $A = \{apples, bananas, oranges\}$

>"apples" $\in A$

>"blueberries" $\notin A$



## Sets - Notation

Sets are commonly expressed using *set notation*.

Within braces, we can write a rule consisting of a function, a vertical bar, and a set to which the function is applied.

<img src="https://i.imgur.com/AG0hluA.png" width="700"/>

## Sets - Notation

### Example

>We can express the set $\{\frac{1}{2}, \frac{1}{4}, \frac{1}{8} \}$ as...

><img src="https://i.imgur.com/S8631Np.png" width="700"/>


## Subsets

$A$ is a ***subset*** of $B$ if and only if every element of $A$ is an element of $B$. 

Can also be written: $A \subseteq B$ 

### Examples

>Let $A = \{1,3,5\}$ and $B = \{1,2,3,4,5\}$.

>>$A \subseteq B$.


>Let $A = \{1,2,3\}$ and $B = \{3,2,1\}$.

>>$A \subseteq B$ and $B \subseteq A$.

## Equality 

$A = B$ if and only if every element of $A$ is an element of $B$ and conversely every element of $B$ is an element of $A$. 
That is, $A \subseteq B$ and $B \subseteq A$.

### Example
>Let $A = \{1,2,3\}$ and $B = \{3,2,1\}$. <br><br>
$A \subseteq B$ and $B \subseteq A$, so $A=B$



## Common Sets

- There are some standard symbols that represent specific sets you will see:
- The set of **Natural Numbers** $\mathbb{N}$ is the set of all whole numbers $\geq 0$, $\{0,1,2,3,4,\ldots\}$.*
- The set of **Integers** $\mathbb{Z}$ is the set of all whole numbers, $\{\ldots, -3, -2, -1, 0, 1, 2, 3, \ldots\}$.
- The set of **Rational Numbers** $\mathbb{Q}$ are numbers that can be represented as a quotient of whole numbers, $\{\frac{p}{q} \mid p,q \in \mathbb{Z}\}$
- The set of **Real Numbers** $\mathbb{R}$ is all *real* numbers. 


## Tuples

A $k$-***tuple*** is an ordered sequence of $k$ elements, which we write down in parentheses, $(a_1,a_2,\ldots,a_k)$.

> The most common tuple seen in math is the coordinate pair $(x,y)$ on a graph. 

> A 2-tuple is commonly called an *ordered pair*.

Two tuples are equal if and only if all of their corresponding elements are equal.
$(a_1,a_2,\ldots,a_k)$ iff for all $i\in[1,\ldots,k]$ we have $a_i=b_i$.

<!-- 
## Tuples - Cartesian Product

The basic operation to create tuples is the Cartesian Product of two sets.

The \textbf{cartesian product} of $A$ and $B$, $A \times B = \{(a,b)|$ for all $a \in A$ and for all $b \in B\}$

### Example
>Let $L=\{a,b,c\}$ and let $D = \{0,1\}$
$L \times D = \{(a,0),(a,1),(b,0),(b,1),(c,0),(c,1)\}$
$D \times L = \{(0,a),(0,b),(0,c),(1,a),(1, b),(1,c)\}$
$L \times L = L^2 = \{(a,a),(a,b),(a,c),(b,a),(b, b),(b,c),(c,a),(c, b),(c,c)\}$

The cartesian product is associative: $D \times(L \times D) = (D \times L) \times D$.

The cartesian product is not necessarily commutative: $D\times L \neq L \times D$.
 -->


## Concatenation

***Concatenation*** is used to join two strings or lists by putting all elements of the second string behind all elements of the first.

### Example
>The concatenation of "hello" and "world" is "helloworld".

## Range

$[a,b]$ is the set of whole numbers $\geq a$  and $\leq b$.

$(a,b)$ is the set of whole numbers $> a$  and $< b$.

### Examples

>$[1,5] = \{1,2,3,4,5\}$

>$(1,5) = \{2,3,4\}$

>$[1,5) = \{1,2,3,4\}$


# Set Operations

## Set Operations 


<img src="https://i.imgur.com/0c94JPz.png" width="240"/>

- $a \in B$ means $a$ is an element of $B$.<br>

## Set Operations 


<img src="https://i.imgur.com/UwPfgSt.png" width="300"/>

- $a \notin B$ means $a$ is *not* an element of $B$.



- Note that technically, $a \in B$ and $a \notin B$ are predicates! They take an element and a set as input and give True or False as an output.




## Subset

<img src="https://i.imgur.com/ZLuhg2i.png" width="300"/>

Let $A$ and $B$ be sets. We say that $A$ is a **subset** of $B$ if and only if every element of $A$ is an element of $B$. 

We write $A \subseteq B$ to denote the fact that $A$ is a subset of $B$.




<!-- ## Subsets Cont.


### Using Predicate Logic 

- $\forall A,B,  A \subseteq B \leftrightarrow \forall x \in A,  x \in A \rightarrow x \in B$
- Technically, we didn't define the domains for $A$ and $B$, but given the context, we know they are sets, so we'll let it slide... 
- We *could* say that all sets exist in some universe of sets $S$. 
- Then our quantifier would say $\forall A,B \in S \ldots$ 
- However, for the rest of these slides, we will just do it the lazy/easier to read way...  -->



## Equality

<img src="https://i.imgur.com/sHL4goN.png" width="150"/>

### Using Predicate Logic

- Remember this?
- For all sets $A$ and $B$, $A = B$  if and only if every element of $A$ is an element of $B$ and every element of $B$ is an element of $A$
- $\forall A,B, A = B \leftrightarrow (A \subseteq B$ and $B \subseteq A)$
<!-- - $\forall A,B,  A = B \leftrightarrow (\forall x,  (x \in A \leftrightarrow x \in B))$ -->




## Complement

<img src="https://i.imgur.com/R9uDave.png" width="200"/>





The complement of a set $A$, denoted $A^\mathcal{C}$ is the set of all elements in the universe $U$ that are *not* in $A$.


### Using Set Notation

>$A^\mathcal{C} = \{x  |  x \notin A\}$

### Using Predicate Logic

>$\forall a,  a \in A^\mathcal{C} \leftrightarrow a \notin A$

>or, equivalently, $\forall a \in U,  a \notin A^\mathcal{C} \leftrightarrow a \in A$




## Intersection

<img src="https://i.imgur.com/HpI6xVu.png" width="300"/>



$A \cap B$ are the elements that are both in $A$ and $B$.

### Using Set Notation

>$A \cap B = \{ x  |  x \in A \land x \in B \}$

### Using Predicate Logic

>$\forall A, B, x,  x \in A \cap B \leftrightarrow (x \in A \land x \in B)$






## Union

<img src="https://i.imgur.com/thTdr8m.png" width="300"/>





$A \cup B$ are the elements that are either in $A$ or $B$.

### Using Set Notation

>$A \cup B = \{ x  |  x \in A \lor x \in B \}$

### Using Predicate Logic

>$\forall A, B, x,  x \in A \cup B \leftrightarrow (x \in A \lor x \in B)$






## Difference


<img src="https://i.imgur.com/FOqpwIS.png" width="300"/>





The **difference** of sets $A$ and $B$ is the set that contains all elements in $A$ that are not in $B$.

### Using Set Notation

>$A - B = A \backslash B =\{\, x  |  x \in A \land x \notin B \}$

### Using Predicate Logic

>$\forall A, B, x,  x \in A - B \leftrightarrow x \in A \land x \notin B$
 




## Difference Cont.

### Example 

>Let $A=\{1,3,5,7\}$ and $B=\{4,5,6,7,8\}$.

>$A-B = \{1,3\}$.


### Example 

>Let $C=\{\bigcirc,\diamondsuit,\Box,\heartsuit\}$ and $e = \heartsuit$. 

>$C-\{e\} = \{\bigcirc, \diamondsuit, \Box\}$.





## Xor

<img src="https://i.imgur.com/lF0EPYP.png" width="300"/>





### Using Set Notation

>$A \oplus B = \{x  |  x \in A \oplus x \in B\}$

### Using Predicate Logic

> $\forall A,B,x,  x \in A \oplus B \leftrightarrow x \in A \oplus x \in B$




<!-- 
## Disjoint Sets


Two sets are **disjoint** if they share no elements.

>$\forall A,B,$ $A$ and $B$ are disjoint $\leftrightarrow A \cap B = \emptyset$ 

>$\forall A,B,$ $A$ and $B$ are disjoint $\leftrightarrow \forall x, (x \in B \rightarrow x \notin A) \land (x \in A \rightarrow x \notin B)$ -->




<!-- 
## Disjoint Union

<img src="https://i.imgur.com/e1baS8x.png" width="300"/> -->





<!-- $A \uplus B$ is the union of two **disjoint** sets.



If $A$ and $B$ are disjoint (share no elements), then $A \uplus B = A \cup B$

If $A$ and $B$ share elements, then $A \uplus B = ERROR$

### Using Predicate Logic

>$\forall A,B, A \uplus B = A \cup B \leftrightarrow A \cap B = \emptyset$

 -->



## Cartesian Product


<img src="https://i.imgur.com/SgxWVdP.png" width="300"/>





The **cartesian product** of $A$ and $B$, 

### Using Set Notation

> $A \times B = \{(a,b)| \forall a \in A$,  $\forall b \in B\}$

### Using Predicate Logic

> $\forall A,B, a,b,  ((a,b) \in A \times B) \leftrightarrow (a \in A \land b \in B)$  






## Powerset

<img src="https://i.imgur.com/THuABsa.png" width="300"/>

The powerset of a set $A$, denoted $\mathcal{P}(A)$ is the set of all subsets of $A$

### Using Set Notation

>$\mathcal{P}(A) = \{ S  |  S \subseteq A\}$

- $|\mathcal{P}(A)| = 2^{|A|}$

## Next

There's a lesson on Gradescope!


