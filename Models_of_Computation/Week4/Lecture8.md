# Lecture 6: Predicate Logic: Semantics

True or false?

$\forall_x \forall_z(x < z \rightarrow \exists_y (x < y \wedge y < z))$

Depends on the interpretation.

1. `False` if discussing $\Z$ and $<$ is "less than".

2. `True` if discussing $\Z$ and $<$ is "less than or equal".

3. `True` if discussing $\R$ and $<$ is "less than".

4. Unconditionally `true` if universe is $\{0\}$

## Universe of Discourse

The set of things we are talking about.

Quantifiers range over the universe of discourse.

__`Analogy:`__ Who is "everyone" in "everyone loves Eva"?

## Interpretation Functions

__`Non-logical symbols:`__ predicate, function and constant symbols.

__`Interpretation function:`__ maps every non-logical symbol to its interpretation

Constant symbol $\mapsto$ element of universe.

Predicate symbol $\mapsto$ relation of universe.

Function symbol $\mapsto$ function from universe to universe.

## Models

__`Model:`__ universe of discourse $+$ interpretation function.

$\Z$ with usual $+$ is a model of $\forall_x \exists_y (x + y = 1)$

$\N$ with usual $+$ is `not` a model of $\forall_x \exists_y (x + y = 1)$

## Free Variables

Truth of $P(x)$ depends on choice of $x$.

A `variable assignment` is a function $v$ from variables to universe $U$.

### Example

Consider a model $M$ with universe $U = \{0, 1\}$ and interpretation function $I$ such that $I(P) = \{1\}$. Let $v: var \rightarrow U$ be a variable assignment. Then,

* $P(x)$ is `true` in $M$ under $v$ if $v(x) = 1$

* $P(x)$ is `false` in $M$ under $v$ if $v(x) = 0$

## Truth of a Formula

The truth of a `closed` formula should depend only on the given interpretation.

The only reason why we are interested in formulas with free variables (and hence in variable assignments) is that we want to define the truth of a formula `compositionally` as seen in the [next section](#making-a-formula-true)

__`Notation:`__

$\begin{equation}
v_{x \mapsto d}(y) = 
    \begin{cases}{}
        d & \text{if } y = x\\
        v(y) & \text{otherwise}
    \end{cases}
\end{equation}$

Read this as "the map v, updated to the map x to d"

## Making a Formula True
Given an interpretation $\mathcal{I}$ (with universe $U$), and variable assignment $v$,

* $v$ makes $P(t_1, ..., t_n)$ true iff $(v(t_1), ..., v(t_n)) \in \mathcal{I}(P)$

* $v$ makes $\exists x \space F$ true iff $v_{x \mapsto d}$ makes $F$ true for at least one $d \in U$

If we now `define`

$
\begin{equation}
\forall x \space F \equiv \neg \exists x \space \neg F
\end{equation}
$

Then the meaning of every other formula follows from this.

## Quantifier Order

The order of different quantifiers is important.

$\forall x \exists y$ is not the same as $\exists y \forall x$

The former says each $x$ has a $y$ that satisfies $P(x, y)$; the latter says there's an individual $y$ that satisfies $P(x, y)$ for every $x$.

But $\forall x \forall y$ is the same as $\forall y \forall x$ and $\exists x \exists y$ is the same as $\exists y \exists x$.

## Quantified Formulas as a Two-Person Game

The truth or falsehood of a quantified formula can be expressed as a question of winning strategies for a two-person game. Say I make a claim (the quantified statement) and you try to disprove it. You get to supply values for the universally quantified variables.

* If I claim $\forall x \exists y \space\space P(x, y)$, then you can challenge me by choosing an $x$ and asking me to find the $y$ that satisfies $P(x, y)$, `but I get to know the x you chose`.

* If I claim $\exists y \forall x \space\space P(x, y)$, then you can challenge me by asking me to provide the $y$, and then you just have to find an $x$ that does not satisfy $P(x, y)$, `knowing the y that I chose.`

* If I claim $\exists x \exists y \space\space P(x, y)$, then I have to find both $x$ and $y$, so it doesn't matter what order they appear.

* If I claim $\forall y \forall x \space \space P(x, y)$, then you get to pick both $x$ and $y$, so again their order doesn't matter

## Rules of Passage for the Quantifiers

We cannot in general `"push quantifiers in"`.

For example, there is no immediate simplification of a formula of the form $\exists x \space (P(x) \wedge Q(x))$.

However, we do get, for formulas $F_1$ and $F_2$:

$
\begin{align}
\exists x \space (\neg F_1) \equiv \neg \forall x \space F_1 \\
∀x (¬F1) ≡ ¬∃x F1 \\
∃x (F1 ∨ F2) ≡ (∃x F1) ∨ (∃x F2) \\
∀x (F1 ∧ F2) ≡ (∀x F1) ∧ (∀x F2) \\
\end{align}
$

It follows that

$
\begin{equation}
\exists x (F_1 \rightarrow F_2) \equiv (\forall x \space F_1) \rightarrow (\exists x \space F_2)
\end{equation}
$

## More Rules of Passage for Quantifiers

If $G$ is a formula with `no free occurrences` of $x$, then we also get

$
\begin{align}
∃x G ≡ G\\
∀x G ≡ G\\
∃x (F ∧ G) ≡ (∃x F) ∧ G\\
∀x (F ∨ G) ≡ (∀x F) ∨ G\\
∀x (F → G) ≡ (∃x F) → G\\
∀x (G → F) ≡ G → (∀x F)\\
\end{align}
$

> If $G$ doesn't depend on $x$ you can pull it out

> $x$ is free in $G$ if $G(x)$

> That is to say $G$ doesn't depend on $x$

No matter what $F$ is. In particular $F$ may have free occurrences of $x$

## Models and Validity of Formulas

A wff $F$ is `true in interpretation` $\mathcal{I}$ iff every variable assignment makes
$F$ true (for $\mathcal{I}$). If not true then it is `false in interpretation` $\mathcal{I}$.

A `model` for $F$ is an interpretation $\mathcal{I}$ such that F is true in $\mathcal{I}$. We write $\mathcal{I} \models F$.

A wff $F$ is `logically valid` iff `every` interpretation is a model for $F$. In that case we write $\models F$.

$F_2$ is a `logical consequence` of $F_1$ iff $\mathcal{I} \models F_2$ whenever $\mathcal{I} \models $F_1$. We write $F_1 \models F_2$.

$F_1$ and $F_2$ are `logically equivalent` iff $F_1 \models F_2$ and $F_2 \models F_1$. We write $F_1 \equiv F_2$.

## Summarising: Satisfiability and Validity

A closed, well-formed formula $F$ is 

* __`Satisfiable`__ iff $\mathcal{I} \models F$ for some interpretation $\mathcal{I}$;

* __`Valid`__ iff $\mathcal{I} \models F$ for every interpretation $\mathcal{I}$;

* __`Unsatisfiable`__ iff $\mathcal{I} \cancel{\models} F$ for every interpretation $\mathcal{I}$;

* __`Non-valid`__ iff $\mathcal{I} \cancel{\models} F$ for some interpretation $\mathcal{I}$.

As in the propositional case, we have

* $F$ is valid iff $\neg F$ is unsatisfiable;

* $F$ is non-valid iff $\neg F$ is satisfiable.

## Example of Non-Validity

Consider the formula

$
\begin{equation}
(\forall y \exists x \space P(x, y)) \rightarrow (\exists x \forall y \space P(x, y))
\end{equation}
$

It is __`not valid`__.

For example, considering the interpretation with universe $U = \Z$ and the predicate $P$ meaning "less than".

Or, let $U = \{0, 1\}$ and let $P$ mean "equals".

The formula __`is`__ satisfiable, as it is true, for example, in the interpretation where $U = \{0, 1\}$ and $P$ means "less than or equal".


## Example of Validity

$F = (\exists y \forall x \space P(x, y)) \rightarrow (\forall x \exists y \space P(x, y))$ is valid.

If we negate $F$ and rewrite it we get
$
\begin{equation}
(\exists y \forall x \space P(x, y)) \wedge (\exists x \forall y \space \neg P(x, y))
\end{equation}
$

The right conjunct is made true `only if` there is some $d_0 \in U$ for which $p(d_0, d)$ is false for all $d \in U$.

But the left conjunct requires that $p(d_0, d)$ be true for at least some $d$.

Since $F$'s negation is unsatisfiable, $F$ is valid

## Another Example of Validity
Consider
$
\begin{equation}
F = (\forall x \space P(x)) \rightarrow P(t)
\end{equation}
$

$F$ is valid no matter what term $t$ is

To see this, again it is easier to consider
> Negation of $F$

$
\begin{equation}
\neg F = (\forall x \space P(x)) \wedge \neg P(t)
\end{equation}
$

The term $t$ denotes some element of the universe $U$, so $\neg F$ cannot be satisfied.
