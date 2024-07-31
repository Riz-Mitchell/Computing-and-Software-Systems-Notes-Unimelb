# Lecture 3: Consequence and Satisfaction

## Semantic Consequence
$G$ is a `semantic consequence` of $F$ if and only if `every model of` $F$ `is a model of` $G$
> Whenever the formula $F$ is true, the formula $G$ is also true

For short, we write "$F \models G$"
> "$\models$" is pronounced "(semantically) entails" __`in this case`__

`Note:` $F \equiv G$ iff $F \models G$ and $G \models F$
> This is read as "$F$ is logically equivalent to $G$ if and only if $F$ entails $G$ and $G$ entails $F$

Two formulas are `logically equivalent` if and only if `each of them entails the other`

## Consequence and Implication
Let $F$ and $G$ be formulas

$F \models G$ if and only if $\models F \rightarrow G$
> When the double turn style $(\models)$ is used with `nothing on the left side`, it means that the `formula on the right is always true`

As an immediate [corollary](https://www.google.com/search?client=opera-gx&q=corollary+meaning&sourceid=opera&ie=UTF-8&oe=UTF-8):

$F \equiv G$ if and only if $\models F \leftrightarrow G$

### Questions
OF the following formulas, which allow us to conclude $P \rightarrow Q$?
1. $P$ `Doesn't entail`
2. $\neg P$ `Does entail`
> In any model where we have "not $P$" ($\neg P$) the left side of implication comes out false so the implication itself always comes out true.
3. $Q$ `Does entail`
> Because $Q$ is true in every such model, it does allow us to conclude the implication because the right side of the implication would always true causing the implication to always come out to true.
4. $P \rightarrow (Q \wedge R)$ `Does entail`
> $P$ = It is raining, $Q$ = I will carry umbrella, $R$ = I will wear warm clothes

> So "If `it is raining` then `I will carry an umbrella` and `wear warm clothes`"

> Does the above entail "If `it is raining` then `I will carry an umbrella`"? Yes

5. $(P \vee R) \rightarrow Q$
> Lecturer skipped this one

6. $\neg P \vee Q$ `Equivalent`
> You can write `implication as a disjunction`

> i.e $P \rightarrow Q \equiv \neg P \vee Q$

7. $\neg Q \rightarrow \neg P$ `Equivalent`
> The `contrapositive equivalence`

> i.e $P \rightarrow Q \equiv \neg Q \rightarrow \neg P$

8. $P \rightarrow (Q \vee R)$ `Doesn't entail`

9. $(P \rightarrow Q) \vee R$ `Doesn't entail`

## Tautology
A formula of propositional logic that is `always true`

$(\neg P \wedge Q) \rightarrow (P \rightarrow R)$ is an example of a `tautology`

## Contradiction
A formula of propositional logic which is `always false`

$P \wedge Q \wedge (\neg Q \leftrightarrow (\neg P \vee Q))$
> For this formula you wouldn't need to write down the whole truth table

Taking a look at the formula we see that if either $P$ or $Q$ are false, the $\wedge$ `makes the whole formula false`.

Hence the `only case we need to analyze to prove the formula is a contradiction` is the `only case in which the formula could come out true`

Let $V$ be the truth assignment $V = \{P \mapsto 1, Q \mapsto 1\}$

The formula under $V$ is `comes out to false`
> If we fill out the truth table for that assignment

| $P$ | $Q$ | $(P \wedge Q)$ | $\wedge$ | $(\neg Q \leftrightarrow (\neg P \vee Q))$ |
| :-: | :-: | :-: | :-: | :-: |
| 1 | 1 | 1 | `0` | 1 |

Therefore it is false in every case and such, it is a contradiction

> Negating a contradiction gives a tautology and vis versa

## Tautologies Are Valid
Consider the sentence: `"If Bolsonaro is sane, then Bolsonaro is sane."`

It is `true` regardless of what "Bolsonaro" or "sane" mean.

`Valid:` Always true

`Non-valid:` Sometimes false
> __Doesn't mean always false__

$\models F$ is short for "$F$ is valid"

## Contradictions Are Unsatisfiable
Consider: "Santa Claus is good and Santa Claus is not good"

It is `false` regardless of what "Santa Claus" or "good" mean

`Unsatisfiable:` Never true

`Satisfiable:` Sometimes true
> __Doesn't mean always false__

## Most Statements Are Contingent
> We call these "contingent statements" or "contingent formulas"

Consider the statement: "It is currently raining"

It is true `if and only if` it is currently raining
> Comes out to true when it's raining and false when it's not

## Questions 
Classify the following formulas as valid, contingent, or unsatisfiable:

1. $P$ `contingent`
2. $P \leftrightarrow \not P$ `unsatisfiable`
3. $P \rightarrow (\neg Q \vee P)$ `valid`
4. $\neg Q \vee \neg (P \wedge \neg Q)$ `valid`

## Substitution
Replacing all uses of a propositional letter with a given formula

### Example
Consider "$P \rightarrow P$".

Substitute $P$ with "$(Q \wedge R)$".

__Result:__ "$(Q \wedge R) \rightarrow (Q \wedge R)$".

> Substitution preserves validity!

### Does Substitution Preserve Unsatisfiability?
`Yes`

Negation of contradiction is a tautology

### Does Substitution Preserve Satisfiability?
`No` $-$ a counterexample is easy:

Take $P$ (which is clearly satisfiable).

Then substitute $P$ by $Q \wedge \neg Q$

### Substitution Preserves Logical Equivalence
Denote by $F[A:=B]$ the result of `substituting` $A$ `with` $B$ `in` $F$

__`Example:`__ $(P \rightarrow P)[P:=Q]$ is $(Q \rightarrow Q)$.
> "substitute $P$ with $Q$ in $(P \rightarrow P)$

__`Theorem:`__ Let $F$, $G$, $H$ be formulas and $P$ be `any propositional letter`.

If $F \equiv G$, then $F[P:=H] \equiv G[P:=H]$
> Logical Equivalence is `preserved through substitution` when $F \equiv G$ 

## Interchange of Equivalents
If $F \equiv G$, then $F$ can be freely replaced with $G$.

### Theorem
Let $H'$ be the result of replacing an instance of $F$ with $G$ in $H$
> That is $H' = H[F:=G]$

If $F \equiv G$, then $H \equiv H'$

Result is equivalent: all `semantic properties preserved`.

## Equivalences
`Absorption:`
* $P \wedge P \equiv P$
* $P \vee P \equiv P$

`Commutativity:`
* $P \wedge Q \equiv Q \wedge P$
* $P \vee Q \equiv Q \vee P$

`Associativity:`
* $P \wedge ( Q \wedge R) \equiv (P \wedge Q) \wedge R$
* $P \vee (Q \vee R) \equiv (P \vee Q) \vee R$

`Distributivity:`
* $P \wedge (Q \vee R) \equiv (P \wedge Q) \vee (P \wedge R)$
* $P \vee ( Q \wedge R) \equiv (P \vee Q) \wedge (P \vee R)$

$\leftrightarrow$ is also `commutative and associative`.

`Double Negation:`
* $P \equiv \neg \neg P$

`De Morgan:`
* $\neg (P \wedge Q) \equiv \neg P \vee \neg Q$
> Let $P$ be `hot` and $Q$ be `having ice cream`

> We can then read the above out as "if it is the case that it `not hot and not having ice cream`, it is certainly the case that `I am either not hot or not having ice cream`" 

* $\neg (P \vee Q) \equiv \neg P \wedge \neg Q$
> `Distribute negation` sign and `flip the and / or opperator` $(\wedge \space / \space \vee)$

> De Morgan's Laws allow us to `push negation through parenthesis`

`Implication:`
* $P \rightarrow Q \equiv \neg P \vee Q$
> Rewriting implication as a disjunction and it's `super important`

`Contraposition:`
* $\neg P \rightarrow \neg Q \equiv Q \rightarrow P$
* $P \rightarrow \neg Q \equiv Q \rightarrow \neg P$
* $\neg P \rightarrow Q \equiv \neg Q \rightarrow P$

`Biimplication:`
* $P \leftrightarrow Q \equiv (P \wedge Q) \vee (\neg P \wedge \neg Q)$

## Find an alternative way of writing biimplication $-$ as a conjunction
$P \leftrightarrow Q$ can be rewritten as $(P \rightarrow Q) \wedge (Q \rightarrow P)$
> Then we flatten these implications into disjunctions

So starting with $(P \rightarrow Q) \wedge (Q \rightarrow P)$

We look at $(P \rightarrow Q)$ and from `implication equivalence` we know it can be written as the conjunction $\neg P \vee Q$. Also, the implication $(Q \rightarrow P)$ can be rewritten as $\neg Q \vee P$

Hence we are left with the following:

$(P \rightarrow Q) \wedge (Q \rightarrow P) \equiv (\neg P \vee Q) \wedge (\neg Q \vee P)$ 

## Final Equivalences
Let $\perp$ be any unsatisfiable formula and let $\top$ be any valid formula
> $\perp$ represents `unsatisfiable (always false)`

> $\top$ represents `valid (always true)`

`Duality:`
* $\neg \top \equiv \perp$
* $\neg \perp \equiv \top$

`Negation From Absurdity:`
* $P \rightarrow \perp \equiv \neg P$

`Identity:`
* $P \vee \perp \equiv P$
* $P \wedge \top \equiv P$

`Dominance:`
* $P \wedge \perp \equiv \perp$
* $P \vee \top \equiv \top$

`Contradiction:`
* $P \wedge \neg P \equiv \perp$

`Exclude middle:`
* $P \vee \neg P \equiv \perp$

## Exit Puzzle
Vivian and her partner invited four other couples. When everyone arrived, `some` of the people shook hands with `some` of the others. Of course, nobody shook hands with their partner, or themselves, and nobody shook hands with the same person twice.

Afterwards, Vivian asked everyone how many times they shook somebody's hand. She received different answers from all nine!

How many times did Vivian's partner shake hands?