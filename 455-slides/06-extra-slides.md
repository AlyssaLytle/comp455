<!-- 
# Why the PL Doesn't Work 

We are going to assume $B$ *is* a regular language and demonstrate that this leads to a contradiction!


<v-clicks>

So, going off this idea, that means there exists a DFA $M$ such that $B = L(M)$. 

We know that an automaton has a finite set of states $Q$. Let's say $|Q| = k$. 

Since we are looking at strings of the form $a^nb^n$ for arbitrarily large $n$, this means that there will inevitably be strings where $n > k$. In other words, there are more *inputs* that *states* which, by the pigeonhole principle, means one state must be visited more than once!

So, let's consider this case of an input of the form $a^nb^n$ with a very large $n$ (specifically, greater than $k$).

It'll have to have a start state $s$ and end at an accept state $r \in F$.

<img src="/public/pumping-lemma/pl-1.png" width="500"/> 

</v-clicks>


---

# Why the PL Doesn't Work

<v-clicks>

And now, let's consider this fact that at least one state must be visited more than once. Let's call that state $p$. 


<img src="/public/pumping-lemma/pl-2.png" width="500"/>

We can also represent our string $a^nb^n=uvw$ where after the last character of $u$ and before the first character of $w$, we are at state $p$. 

Additionally, since there are $n$ many $a$'s in this string, and $n>k$, we are safe to define it so that both instances of state $p$ appear over the part of the string that is strictly $a$s.


Since $v$ begins in and ends in the same state, then we should be able to delete it and still have an acceptable string. However, this isn't the case because if we delete $v$, then we have more $b$s than $a$s which should *not* be an accepted string for this language! Therefore, we have a contradiction. $\rightarrow \leftarrow$

</v-clicks>
-->
