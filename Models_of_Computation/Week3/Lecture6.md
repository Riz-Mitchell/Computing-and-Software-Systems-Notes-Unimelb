# Lecture 6:

## Claim:

Let $\Sigma$ be a set of disjunctive clauses. Let $F$ be a formula. If $\Sigma \vdash_R F$, then $\Sigma \models F$

> $\Sigma \vdash_R F$ reads as "If there is a resolution proof from $\Sigma$ to $F$"

> $\Sigma \models F$ reads as "$\Sigma$ semantically entails $F$"

## Proof:

Let $Z$ be a set of disjunctive clauses. Let $F$ be a formula. 

* Let $x$ be any proof of $F$ from $Z$

> $x$ is a string

* Let $v$ be a model of $\Sigma$

> $z$ is a model of every disjunctive clause in $\Sigma$

* Let $C_1$, ..., $C_n$ be the conclusions after the $\vdash$ in $x$

  * By the definition of resolution proof, $C_1$ is either a member of $\Sigma$, or the result of resolution of two premises from $\Sigma$

* If $C_1 \in \Sigma$, then $v \models C_1$, by assumption

* If $C_1 \notin \Sigma$, then $V_1$ is a model of $C_1$ because $C_1$ is the result of resolution of two premises of two formulas in $\Sigma$ <u>and</u> because resolution is sound

Try induction
> If things are built from previous things

$P(k)$: the __`first`__ $k$ conclusions are true under $v$

> To use induction we must prove that $P(k)$ implies $P(k+1)$ 

> If the first $k$ conclusions are `true` under `v`, then the first $k+1$ conclusions are `true` under $v$

Suppose that the first $k$ conclusions are `all true` under $v$ for any given $k \in \Z$. That is, that $v \models C_1$, ..., $C_k$

> This is just an __`assumption`__ called the `inductive hypothesis`

> Goal is to extend this further

* If $k \geq n$, then $v \models C_1$, ..., $C_k$

* Suppose that $k < n$

Consider $C_{k+1}$,

By definition, either $C_{k+1} \in \Sigma$ or it is the result of resolving two earlier formulas $A$ and $B$ against each other 
> From `resolution`

* If $C_{k+1} \in \Sigma$, then $v \models C_{k+1}$ by assumption

* If $C_{k+1} \notin \Sigma$, then by the soundness of the resolution value, since $v \models A$ and $v \models B$, $v \models C_{k+1}$

So in either case, $v \models C_{k+1}$

So therefore, since $v \models C_1$, ..., $C_k$ and $v \models C_{k+1}$, it is true that $v \models C_1$, ..., $C_{k+1}$

So $v$ is a model of the first $k+1$ conclusions

$\therefore$ By induction, $v$ is a model of the first $m$ conclusions for all integers $m \in \Z$

In particular $v$ is a model of $C_n$ and $C_n = F$.

So $V \models F$. So every model of $\Sigma$ is a model of $F$,

That is, $Sigma \models F$ by definition
> `Symantically` entails
