# Lecture 2: Propositional Logic
Propositional = Boolean Logic
> Yes as in `true` / `false` and `1` / `0` :DDDDDDD

## Intro Puzzle
Heidi, Dina and Louise are being questioned by their aunt.

Here is what they say:

* _Heidi: "Dina and Louise had equal share in it; if one is guilty, so is the other."_
* _Dina: "If Heidi is guilty, then so am I."_
* _Louise: "Dina and I are both not guilty"_

Their aunt, knows they are honest kids, and realises that they cannot tell a lie.

Has she got sufficient information to decide who (if any) are guilty?

### Answer
If we take a look at `Louise's` statement and make it less confusing, we understand that `Louise and Dina can't both be guilty at the same time`. Only one of Louise and Dina can be guilty

Now if we look at `Heidi's` statement, we see that she says Dina and Louise `have the same level of guilt`

That essentially means that the only way for these statements to hold true (Kids to be telling the truth) is that `Louise and Dina are both not guilty`

> `If you tried the contrary` and made one of Dina and Louise guilty it would invalidate Heidi's statement which is impossible because none of the children can be wrong (lie)

Hence we can conclude that `Heidi is also not guilty`
> If Heidi was guilty, Dina would also be guilty which we know to be false. If Heidi was guilty it would be impossible because it would mean that Dina is lying which is again `impossible`.

TLDR: No-one is guilty yay!!!! :DDDDDDDDDDDDDD


## Syntax
We shall build propositional formulas from this set of symbols:

![maths symbols](./Resources/image2.png)

Well-formed formulas are generated utilising this grammar:

wff $:=A \mid B \mid C \mid ... \mid Z$

$\mid \neg$ wff

$\mid($ wff $\wedge$ wff $)$

$\mid($ wff $\vee$ wff $)$

$\mid($ wff $\rightarrow$ wff $)$

$\mid($ wff $\leftrightarrow$ wff $)$

> `wff` can can be different each side

### Examples of Well-Formed Formula
* $P$ `P`
* $(P \rightarrow Q)$ `P implies Q`
* $(P \vee \neg P)$ `P or not P`
* $\neg (P \wedge \neg P)$ `not P and not P`
* $(P \leftrightarrow \neg P)$ `P if and only if not P`
* $(((P \rightarrow Q) \rightarrow P) \rightarrow P)$ `P implies Q implies P all implies P`

### Pronunciation Guide
The following symbols `do not carry the same meaning as the pronunciation would`

| Symbol | Pronunciation |
| --- | --- |
| $\neg$ | `not` |
| $\vee$ | `or; vee` |
| $\wedge$ | `and; wedge` |
| $\rightarrow$ | `if ... then; implies; only if; arrow` |
| $\leftrightarrow$ | `if and only if; biimplies; double arrow` |

> These symbols are __not__ shorthands for English words!

### Notational Conveniences
For sake of readability, we follow these __informal__ rules:

* Drop outermost parentheses
* Drop inner parentheses in nested uses of $\wedge$ and $\vee$
  * $P \wedge Q \wedge R$ is short for either of:
    * $((P \wedge Q) \wedge R)$
    * $(P \wedge (Q \wedge R))$
  * Same holds true when replacing every "$\wedge$" with "$\vee$"
  * __WARNING:__ $P \wedge Q \vee R$ is nonsense

### Well-Formed Formula According To Youtube Man
> [As seen in the Video `1.2 well-formed formulas` by Matthew Towers](https://www.youtube.com/watch?v=aAUDGmqAwa0) 

A collection of symbols is a WFF `if and only if it can be made using the following rules`:

1. A propositional variable `IS` itself a WFF.
> These -> $A \mid B \mid C \mid ... \mid Z$
2. If $\phi$ and $\psi$ are any two WFFs then:
    * $(\phi \wedge \psi)$ is a WFF
    * $(\phi \vee \psi)$ is a WFF
    * $(\phi \rightarrow \psi)$ is a WFF
    * $(\phi \leftrightarrow \psi)$ is a WFF
    * $\neg\phi$ is a WFF

## Truth Tables
> [A handy tool for `generating simple Truth Tables` using `propositional logic formulas`](https://web.stanford.edu/class/cs103/tools/truth-table-tool/)

### What is Truth?
What does it mean for $P \wedge Q$ to be true?
> Both $P$ and $Q$ are true for the propositional logic formula to be true

What about just $P$?
> $P$ is true for the propositional logic formula to be true

Is $P \vee \neg P$ true?
> We cannot tell whether or not the formula is 'true' because we do not have the inputs

There is a difference between a `propositional logic formula that is true`, and one that is `always true`

## Boolean Semantics

### Connectives
A __`Truth Function`__ is a function that `takes truth values and outputs truth values`

Boolean truth values are usually `True` and `False` or `1` and `0`

The `connectives` I introduced in the [Syntax Section](#syntax) are `truth functional`

Truth Functions can be represented as `truth tables` similar to below:

| $A$| $B$ |  | $\neg A$ | $A \wedge B$ | $A \vee B$ | $A \rightarrow B$ | $A \leftrightarrow B$ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|     |     |  |     |     |     |     |     |
| 0 | 0 |  | 1 | 0 | 0 | 1 | 1 |
| 0 | 1 |  | 1 | 0 | 1 | 1 | 0 |
| 1 | 0 |  | 0 | 0 | 1 | 0 | 0 |
| 1 | 1 |  | 0 | 1 | 1 | 1 | 1 |

> __For $A \rightarrow B$, the propositional logic formula outputs False `exactly when` $A$ `is True and` $B$ `is False`__ 

> __For $A \leftrightarrow B$, the formula outputs True `when` $A$ `and` $B$ `have the same truth value`__

### Letters
[Propositional letters (introduced in the Syntax section)](#syntax) are `Boolean variables`

A __`Truth Assignment`__ is a function that transforms a propositional letter into a truth value

Useful notation:

$V = \{P \mapsto 1, Q \mapsto 0\}$

We then have: 

$V(P) = 1$

$V(Q) = V(R) = ... = V(Z) = 0$

### Truth of a Formula
Let $V = \{P \mapsto 1, Q \mapsto 0\}$

Which of these formulas are true under $V$?

1. $P \wedge Q$ `Not True`
2. $(P \vee Q) \wedge (P \vee R)$ `True`
3. $P \rightarrow Q$ `Not True`
4. $\neg P \rightarrow \neg Q$ `True`

Using a `shorthand` "$V \models \phi$" which means "$\phi$ is true under $V$"
> Or $V$ is a `model` of $\phi$

### Logical Equivalence
Formulas are __`Logically Equivalent`__ if they have equal truth values __`under every truth assignment`__

Using a `shorthand` "$F \equiv G$" means "$F$ is logically equivalent to $G$

### Material Conditional
$\rightarrow$ is weird!

It is often read as "implies", but causality is not required!

## Modus Ponens
$P \rightarrow Q$ `Premise`

$P$ `Premise`

$Q$ `Conclusion`

> Essentially this statement translates to, `"if P implies Q and P holds, Q holds`.

A rule is `sound` if every model of the premises is a model of the conclusion.
> That is to say if the premises [semantically](https://dictionary.cambridge.org/dictionary/english/semantically) entail the conclusion

__Challenge:__ Prove that modus ponens is sound.
> Using the premises derive the conclusion

## Exit Puzzle
On the island of Knights and Knaves, everyone is a knight or a knave.
Knights always tell the truth. Knaves always lie.

Today there is a census on the island!

You are a census taker, going from house to house. Fill in what you know about each of these three houses:

* __In house 1__: We are both knaves.
> The `statement cannot be true` as no one on this island can admit to being a knave hence the speaker must be a knave

> So their statement must be false and the `other house member must be a knight`

* __In house 2__: At least one of us is a knave.
> `Cannot be a knave speaking` as it would `make this statement true`, hence the `speaker is a knight`

> As the speaker is a knight and they are telling the truth, `the other person is a knave`

* __In house 3__: If I am a knight then so is my wife.

### Eric Zheng's Take on House 3

"I'm not the lecturer, but here is my take:

For the sake of contradiction, let's `assume the person is a knave`. 

As this person is a knave, we know the `statement they said` - "If I am a knight then so is my wife" - `is false`. 
Since this statement is false, we know that it must be the case that "I" am a knight and "my" wife is not a knight. (This part is the key, as in no other circumstances is this statement false. Because in cases where "I" am a knave, then this `statement is true regardless of what my wife is`, meaning that "I" am a knave that is `telling a truth which is impossible`) 

However we arrive at a `contradiction that I am both a knight at a knave.`

Thus "I" `cannot be a knave`

Hope this helps!"
