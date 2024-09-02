# Models of Computation Assignment 1

> [!IMPORTANT]
> `Name:` Riley Mitchell 
>
> `Email:` rmmitc@student.unimelb.edu.au
> 
> `Student ID:` 1353040

## __Q1__ Propositional Logic: Island Puzzle

### Task A

Propositional Letters

$$
\begin{array}{lcl}
A: \text{A is a knight}\\ \\
B: \text{B is a knight} \\ \\
C: \text{C is a knight}\\ \\
M_K: \text{Mimic is a knight}\\ \\
M_A: \text{A is the mimic} \\ \\
M_B: \text{B is the mimic} \\ \\
M_C: \text{C is the mimic}
\end{array}
$$

Using these propositional letters we will form our propositional formulas based on each of the statements made:

$$
\begin{array}{lcl}
A \rightarrow (M_C \vee C) &\text{C is either the mimic or a knight, or both.}\\ \\
B \rightarrow \neg (M_A \wedge \neg C) & \text{It is not the case that both A is the mimic and C is a knave} \\ \\
C \rightarrow (B \rightarrow \neg M_K) & \text{If B is a knight, then the mimic is a knave}
\end{array}
$$

### Task B

#### Assume Mimic is a knave:

##### Assume A is the Mimic:

$\therefore \{A \mapsto 0, M_A \mapsto 1, M_K \mapsto 0\}$ and $A$'s hence the following is true
* $C$ is NEITHER a mimic or a knight or both
  * That is $\{M_C \mapsto 0, C \mapsto 0\}$
  * $\therefore$ $C$'s statement is false and they are a knave

And so far $\{A \mapsto 0, M_A \mapsto 1, M_K, \mapsto 0, M_C \mapsto 0, C \mapsto 0\}$

So if A is the mimic and a knave and C is also a knave, we know that B too must be a knave because their statement would be a lie in this case and otherwise we get a contradiction.

$\therefore B \mapsto 0$

So for C's statement to be a lie the Mimic must be a knave which it is making it "not the case that if B is a knight, then the mimic is a knave"

So if all of A, B and C are lying, their statements hold and in this case `A is the mimic`



---


## __Q2__ Propositional Logic: Validity and Satisfiability

### 1.

Simplify to a logically equivalent formula

$$
\begin{array}{lcl}
\neg P \wedge (P \rightarrow \neg P) \\ \\
\equiv \neg P \wedge (\neg P  \vee \neg P) \\ \\
\equiv \neg P \wedge \neg P \\ \\
\equiv \neg P
\end{array}
$$

Under the truth assignment $\{P \mapsto 1\}$, the equation comes out to $0$, and under $\{P \mapsto 0\}$ and the formula comes out to $1$.

Hence, $\neg P \wedge (P \rightarrow \neg P)$ is `contingent`

---

### 2.

Simplify to a logically equivalent formula

$$
\begin{array}{lcl}
(P \vee (P \wedge ( Q \rightarrow Q))) \wedge (\neg P \vee \neg (\neg Q \rightarrow \neg Q)) \\ \\
\equiv (P \vee (P \wedge \top)) \wedge (\neg P \vee \neg \top) \\ \\
\equiv (P \vee (P \wedge \top)) \wedge (\neg P \vee \bot)\\ \\
\equiv (P \vee (P \wedge \top)) \wedge (\neg P \vee \bot)\\ \\
\end{array}
$$

Consider the following:

$(P \wedge \top) \equiv P$ and $(\neg P \vee \bot) \equiv \neg P$

Knowing this we can now put the formula in CNF:

$$
\begin{array}{lcl}
(P \vee P) \wedge \neg P\\ \\
\equiv (P \wedge \neg P)
\end{array}
$$

Then using refutation resolution we get:

$$
\begin{array}{lcl}
P &&& \neg P
\end{array}
$$

$$
\bot
$$

Hence, $(P \vee (P \wedge ( Q \rightarrow Q))) \wedge (\neg P \vee \neg (\neg Q \rightarrow \neg Q))$ is `unsatisfiable`

---

### 3.

Formula:

$$
\begin{array}{lcl}
\neg((Q \vee P) \rightarrow P) \vee (P \leftrightarrow Q) \vee (P \wedge \neg Q)\\ \\
\end{array}
$$

`Truth table` for the formula:

| $P$ | $Q$ | $(Q \vee P)$ | $((Q \vee P) \rightarrow P)$ | $\neg((Q \vee P) \rightarrow P)$ | $(P \leftrightarrow Q)$ | $(\neg Q)$ | $(P \wedge \neg Q)$ | Formula Result |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 | 0 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 | 1 | 0 | 0 | 1 |

According to our truth table the formula is valid

Let us prove using resolution refutation:

Eliminate the implication: $(Q \vee P) \rightarrow P \equiv \neg (Q \vee P) \vee P$

Deal with the biimplication: $(P \leftrightarrow Q)$

$$
\begin{array}{lcl}
(P \leftrightarrow Q) \\
\equiv (P \wedge Q) \vee (\neg P \wedge \neg Q)\\
\end{array}
$$

To prove that the formula is valid using refutation we will assume the the contrary (that it is unsatisfiable) and negate it :

$$
\begin{array}{lcl}
\neg (\neg (\neg (Q \vee P) \vee P) \vee ((P \wedge Q) \vee (\neg P \wedge \neg Q)) \vee (P \wedge \neg Q)) \\ \\

\equiv (\neg (Q \vee P) \vee P) \wedge \neg ((P \wedge Q) \vee (\neg P \wedge \neg Q)) \wedge \neg (P \wedge \neg Q)\\ \\

\equiv ((\neg Q \wedge \neg P) \vee P) \wedge (\neg (P \wedge Q) \wedge \neg (\neg P \wedge \neg Q)) \wedge (\neg P \vee Q)\\ \\

\equiv ((P \vee \neg Q) \wedge (P \vee \neg P)) \wedge ((\neg P \vee \neg Q) \wedge (P \vee Q)) \wedge (\neg P \vee Q) \\ \\

\equiv ((P \vee \neg Q) \wedge \top) \wedge (\neg P \vee \neg Q) \wedge (P \vee Q) \wedge (\neg P \vee Q)\\ \\

\equiv (P \vee \neg Q) \wedge (\neg P \vee \neg Q) \wedge (P \vee Q) \wedge (\neg P \vee Q) \\ \hline
\end{array}
$$

Now resolving the CNF formula:

$$
\begin{array}{lcl}
(P \vee \neg Q) &&& (\neg P \vee \neg Q) &&& (P \vee Q) &&& (\neg P \vee Q) \\ \\
& (\neg Q \vee \neg Q) &&&&&&& (Q \vee Q) \\ \\
& \neg Q &&&&&&& Q \\ \\
&&&& \bot
\end{array}
$$

Therefore because the resolution of the negation of the formula: $\neg((Q \vee P) \rightarrow P) \vee (P \leftrightarrow Q) \vee (P \wedge \neg Q)$ is unsatisfiable, $\neg((Q \vee P) \rightarrow P) \vee (P \leftrightarrow Q) \vee (P \wedge \neg Q)$ is `valid`




---

### 4.

Formula:

$$
\begin{array}{lcl}
(R \leftrightarrow P) \rightarrow ((R \rightarrow Q) \leftrightarrow (P \leftrightarrow Q))
\end{array}
$$

`Truth table` for the formula:

| $P$ | $Q$ | $R$ | $(R \leftrightarrow P)$ | $(P \leftrightarrow Q)$ | $(R \rightarrow Q)$ | $((R \rightarrow Q) \leftrightarrow (P \leftrightarrow Q))$ | $(R \leftrightarrow P) \rightarrow ((R \rightarrow Q) \leftrightarrow (P \leftrightarrow Q))$ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | 1
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1
| 0 | 1 | 0 | 1 | 0 | 1 | 0 | 0
| 0 | 1 | 1 | 0 | 0 | 1 | 0 | 1
| 1 | 0 | 0 | 0 | 0 | 1 | 0 | 1
| 1 | 0 | 1 | 1 | 0 | 0 | 1 | 1
| 1 | 1 | 0 | 0 | 1 | 1 | 1 | 1
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1

According to our truth table the formula is contingent

Let us now validate this with two different truth assignments to show both case

Consider the truth assignment $\{P \mapsto 0, Q \mapsto 1, R \mapsto 0\}$ to the formula:

$$
\begin{array}{lcl}
(0 \leftrightarrow 0) \rightarrow ((0 \rightarrow 1) \leftrightarrow (0 \leftrightarrow 1)) \\ \\

= 1 \rightarrow (1 \leftrightarrow 0) \\ \\

= 1 \rightarrow 0 \\ \\

= 0 \\ \hline
\end{array}
$$

Consider the truth assignment $\{P \mapsto 0, Q \mapsto 0, R \mapsto 0\}$ to the formula:

$$
\begin{array}{lcl}
(0 \leftrightarrow 0) \rightarrow ((0 \rightarrow 0) \leftrightarrow (0 \leftrightarrow 0)) \\ \\

= 1 \rightarrow (1 \leftrightarrow 1) \\ \\

= 1 \rightarrow 1 \\ \\

= 1 \\ \hline
\end{array}
$$

---

## __Q3__ Predicate Logic: Translation and Semantics

### Task A

1. `Iron is heavier than oxygen`

$$
\begin{array}{lcl}
i: & \text{Iron (Const.)} \\ \\
o: & \text{Oxygen (Const.)} \\ \\
H(a, b) & \text{"a" heavier than "b" (Pred.)} \\ \\
H(i, o) & \text{Iron is heavier than oxygen} \\ \hline
\end{array}
$$

2. `All actinides are radioactive`

$$
\begin{array}{lcl}
A(x) & \text{x is an actinide} \\ \\
R(x) & \text{x is radioactive} \\ \\
\forall x & \text{All x} \\ \\
\forall x(A(x) \rightarrow R(x)) & \text{All actinides are radioactive}\\ \hline
\end{array}
$$

3. `Some, but not all, lanthanides are radioactive`

$$
\begin{array}{lcl}
x, y & \text{variables within the universe of discourse} \\ \\
L(a) & \text{"a" is a lanthanide} \\ \\
\exists x (L(x) \wedge R(x)) \wedge \exists y (L(y) \wedge R(y)) & \text{Some, but not all, lanthanides are radioactive} \\ \hline
\end{array}
$$

4. `Actinides are heavier than lanthanides`

$$
\begin{array}{lcl}
\forall x \forall y ((A(x) \wedge L(y)) \rightarrow H(x, y)) & \text{Actinides are heavier than lanthanides} \\ \hline
\end{array}
$$

5. `Both lanthanides and actinides are heavier than iron and oxygen`

$$
\begin{array}{lcl}
\forall x ((L(x) \vee A(x)) \rightarrow (H(x, i) \wedge H(x, o)))  & \text{Both lanthanides and actinides are heavier than iron and oxygen} \\ \hline
\end{array}
$$

6. `At least three isotopes of lanthanides are radioactive, but the only lanthanide without any non-radioactive isotopes is promethium`

$$
\begin{array}{lcl}
P(x) & \text{x is prometium} \\ \\
I(x) & \text{x is an isotope} \\ \\
x_n & \text{$n$th element} \\ \\
\exists x_1 \exists x_2 \exists_3 ((I(x_1) \wedge I(x_2) \wedge I(x_3 )) \wedge (R(x_1) \wedge R(x_2) \wedge R(x_3)))
\end{array}
$$


### Task B

To prove that the universe of every model of the formula;

$$
\forall x \forall y (P(x,y) \rightarrow \neg P(y, x)) \wedge \forall x \exists y (P(x, y))
$$

has at least 3 distict elements that is $U = \{a, b, c\}$, we shall assume for the sake of contradiction that the universe has 1 $U = \{a\}$, or 2 $U = \{a, b\}$ distinct elements.

#### Universe with 1 Element

Let $U = \{a\}$

If we obvserve the formula $\forall x \exists y (P(x, y))$ for $a$ we need some $y$ such that $P(a, y)$ holds,

However, since $a$ is the only element in $U$, $y$ must also be $a$.

$\therefore$ we need $P(a, a)$ to hold.

For $\forall x \forall y (P(x, y) \rightarrow \neg P(y, x))$ to be true we require $P(a, a) \rightarrow \neg P(a, a)$ to hold.

However this is a contradiction as it implies that if $P(a, a)$ holds, then $P(a, a)$ doesn't hold.

#### Universe with 2 Elements

Let $U = \{a, b\}$

The formula $\forall x \exists y (P(x, y))$ requires that $P(a, b)$ and $P(b, a)$ hold for the elements $a$ and $b$ respectively.

For the constraint $\forall x \forall y (P(x,y) \rightarrow \neg P(y, x))$, if $P(a, b)$ is true then $P(b, a)$ must false and vis versa.

However, $\forall x \exists y (P(x, y))$ requires both $P(a, b)$ and $P(b, a)$ to be true which is a contradiction.


## __Q4__ Predicate Logic: Red-Black Trees

To prove that it is not a red black tree we must first negate the 2nd constraint:

$$
\begin{array}{lcl}
\neg \forall x (R(x) \rightarrow (\neg R(l(x)) \wedge \neg R(r(x)))) \\ \\

\equiv \exists x \neg(\neg R(x) \vee (\neg R(l(x)) \wedge \neg R(r(x)))) \\ \\

\equiv \exists x (R(x) \wedge \neg (\neg R(l(x)) \wedge \neg R(r(x)))) \\ \\

\equiv \exists x (R(x) \wedge (R(l(x)) \vee R(r(x)))) \\ \\
\end{array}
$$
> [!NOTE]
> This translates to:
>
> "There exists an x such that x is a root node and it's left or right child is also red"

To apply resolution we then convert the second constraint to CNF:

$$
\begin{array}{lcl}
R(x) \rightarrow (\neg R(l(x)) \wedge \neg R(r(x))) \\ \\

\equiv \neg R(x) \vee (\neg R(l(x)) \wedge \neg R(r(x))) \\ \\

\equiv (\neg R(x) \vee \neg R(l(x))) \wedge (\neg R(x) \vee \neg R(r(x)))
\end{array}
$$

Now we have our clauses so we perform refutation:

$$
\begin{array}{lcl}
R(x) && (\neg R(x) \vee \neg R(l(x))) && (R(l(x)) \vee R(r(x))) && (\neg R(x) \vee \neg R(r(x))) \\ \\ \\
& \neg R(l(x)) &&&& (R(l(x)) \vee \neg R(x)) \\ \\ \\ \\
&&&\neg R(x)
\end{array}
$$

At this point we have derived $\neg R(x)$, however this contradicts our assumption $R(x)$.

$\therefore$ since the assumption was that $R(x) \wedge (R(l(x)) \vee R(r(x)))$ and that was shown to lead to $\neg R(x)$ when resolved against $(\neg R(x) \vee \neg R(l(x))) \wedge (\neg R(x) \vee \neg R(r(x)))$, it must be that tree in question is not a red-black tree.



## __Q5__ Informal Proof: Palindromes

### Issues

* The theory doesn't explicitly show how the reverse of the concatenation $ss$ and how it results in $ss$.
* The theory fails to explicitly apply the definition of reversal correctly.
* The conclusion is uncrear, confusing and doesn't provide a clear and logical progression.

### Corrected Proof

`Theorem:` Let s be a palindrome. Then their concatenation ss is also a palindrome

`Proof:` Let $s = a_1 ... a_n$ be a string of length $n$ such that $s$ is a palindrome. By definition, the palindrome $s$ is equal to its reverse, so $s = a_n ... a_1$.

As $s$ is a string and $ss$ is their concatenation, it is also a string and is given by:

$$
ss = a_1 ... a_n \space a_1 ... a_n
$$

We want to reverse $ss$ to show it is equal to $ss$:

$$
\begin{array}{lcl}
\text{reverse}(ss) = \text{reverse}(s) \space \text{reverse}(s)\\\\
= \text{reverse}(a_1 ... a_n) \space \text{reverse}(a_1 ... a_n)
\end{array}
$$

We then apply the definition of reversal from definition `4.c`, that is "the reverse of a nonempty string $a_1 ... a_n$ of length $n$ is the reverse $b_1 ... b_n$" which gives us for $i = 1 ... i = n$:

$$
\begin{array}{lcl}
= b_1 ... b_n \space b_1 ... b_n
\end{array}
$$

In the definition $b_i = a_{n-i+1}$ for all positive integers, so we now have:

$$
\begin{array}{lcl}
= a_n ... a_1 \space a_n ... a_1 \\ \\
\text{so} \\ \\
\text{reverse}(ss) == a_n ... a_1 \space a_n ... a_1
\end{array}
$$

$\therefore$ as per our original definition of the reverse of $s$ and our derived $s$

$$
\begin{array}{lcl}
a_n ... a_1 \space a_n ... a_1 = \text{reverse}(a_1 ... a_n) \space \text{reverse}(a_1 ... a_n) = ss
\end{array}
$$

$\therefore$, $ss$ is also a palindrome