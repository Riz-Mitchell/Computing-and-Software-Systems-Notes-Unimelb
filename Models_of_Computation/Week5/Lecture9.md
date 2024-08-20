# Lecture 9: Predicate Logic: Clausal Form

## Resolution for Predicate Logic

Resolution generalises to predicate logic.

Same strat: try to derive $\bot$

__`However`__ , quantifiers mean that not every predicate logic formula has a CNF.

Work around by giving up on equivalence.

## Eliminating Existential Quantifiers

Consider $F$: $\exists x \forall y P(x, y)$.

Consider $G$: $\forall y P(a, y)$, where $a$ is a constant symbol

## Theorem

$G$ is `satisfiable` iff $F$ is.

## Proof (sketch).

Every model of $G$ is a model of $F$: pick $I(a)$ for $\exists x$.

We can extend every model of $F$ to a model of $G$ by defining $I(a)$ to be the same object we picked for $\exists x$

## Skolem Constants and Functions

Consider $F: \forall y \exists x \space P(x, y)$.

We `cannot` conclude that $\forall y \space P(a, y)$ is satisfiable iff $F$ is.

Since $\exists x$ is within the scope of $\forall y$, the value of $x$ for which $P(x, y)$ holds depends on the value $y$

Thus cannot replace $x$ by a constant.

Treat the value of $x$ as a `function of the value of y:`

$\forall y \space P(f(y), y)$ is satisfiable iff $F$ is.

Note that f is a `fresh` function symbol.

## Skolemization

We call $a$ a `Skolem constant`, and $f$ a `Skolem function`.

Skolem functions can be of arbitrary arity. To eliminate $\exists y$ in $\forall x_1 \forall x_2 \forall x_3 \exists y [...]$ we replace each occurence of $y$ in its scope by $f(x_1, x_2, x_3)$.

Namely, $y$ may depend on all three $x$ s

Each introduced Skolem constant or function `must be fresh.`

Recall also our convention: We use letters from the start of the alphabet $(a, b, c, ...)$ for constants, and letters from the end of the alphabet $(u, v, x, y, ...)$ for variables.

## Skolemization Example

This formula has three existential quantifiers - we remove them one by one:

$
\begin{equation}
\begin{split}
\exists u \forall v \exists x \forall y \exists z ((\neg P(u, f(v), x, b) \vee R(g(x, y), u)) \wedge S (y, g (a, z))) \\
\approx \forall v \exists x \forall y \exists z ((\neg P(c, f(v), x, b) \vee R(g(x, y), c)) \wedge S (y, g, (a, z))) \\
\approx \forall v \forall y \exists z ((\neg P (c, f(v), h(v), b) \vee R (g(h(v), y), c)) \wedge S (y, g (a, z))) \\
\exists \forall v \forall y ((\neg P (c, f(v), h(v), b) \vee R (g(h(v), y), c)) \wedge S (y, g (a, j (v, y))))
\end{split}
\end{equation}
$

Instead of $j(v, y)$ we could have chosen $k(v, y)$, or even $j(y, v)$ - as long as we replace each occurrence of $z$ by the same term of course.

## From Predicate Logic Formulas to Clausal Form

The process is similar to what we did with propositional formulas:

1. Eliminate $\leftrightarrow$ and $\rightarrow$.
2. Push negation in. (Bring NNF.)
3. Rename shadowed variables.
* A variable is `shadowed` iff it is within the scope of a quantifier binding the same variable (e.g. the second $x$, in $\forall x \exists x$ or $\forall x \forall x$)
4. Eliminate existential quantifiers (Skolemize).
5. Eliminate universal quantifiers (just remove them).
Bring to CNF (using the distributive laws).

## Clausal Form: Step 1 - Use Just $\vee$, $\wedge$, $\neg$

Let us use this running example:

$
\begin{equation}
\forall x (P(x) \leftrightarrow \exists y (R(x, y) \forall z R (z, y)))
\end{equation}
$

First use the usual translations to eliminate $\leftrightarrow$ and $\rightarrow$:

$
\begin{equation}
\forall x ((P(x) \rightarrow \exists y (R (x, y) \wedge \forall z R (z, y))) \wedge (\exists y (R (x, y) \wedge \forall z R (z, y)) \rightarrow P(x)))
\end{equation}
$

which then becomes:

$
\begin{equation}
\forall x ((\neg P(x) \vee \exists y (R(x, y) \wedge \forall z R (z, y))) \wedge (\exists y (R (x, y) \wedge \forall z R (z, y)) \rightarrow P (x)))
\end{equation}
$

## Clausal Form: Step 2 - Push Negation

Next drive negation in.

$
\begin{equation}
\forall x ((\neg P(x) \vee \exists y (R(x, y) \wedge \forall z R(z, y))) \wedge ( \neg \exists y (R (x, y) \wedge \forall z R (z, y)) \vee P(x)))
\end{equation}
$

then becomes

$
\begin{equation}
\forall x ((\neg P(x) \vee \exists y (R (x, y) \wedge \forall z R (z, y))) \wedge (\forall y (\neg R (x, y) \vee \exists z \neg R (z, y)) \vee P(x)))
\end{equation}
$

## Clausal Form: Step 3 - Rename Apart

Now rename variables so that no two quantifiers use the same variable name. With that,

$
\begin{equation}
\forall x ((\neg P(x) \vee \exists y (R (x, y) \wedge \forall z R (z, y))) \wedge (\forall y (\neg R (x, y) \vee \exists z \neg R (z, y)) \vee P(x)))
\end{equation}
$

turns into, say

$
\begin{equation}
\forall x ((\neg P (x) \vee \exists y (R (x, y) \wedge \forall z R (z, y))) \wedge (\forall u (\neg R (x, u) \vee \exists v \neg R (v, u)) \vee P (x)))
\end{equation}
$