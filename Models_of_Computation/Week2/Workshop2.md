# Workshop 2: propositional Logic

## Question 1
For each pair of formulas, write down and compare their truth tables. In which rows (if any) are they different

`i`
| $P$ | $Q$ | $\neg P$ | $\neg Q$ | $\neg P \rightarrow Q$ | $P \rightarrow \neg Q$ |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 1 | 0 |

`ii`
| $P$ | $Q$ | $R$ | $(P \wedge Q) \rightarrow R$ | $P \rightarrow (Q \rightarrow R)$ |
| :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 | 1 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

`iii`
| $P$ | $Q$ | $\neg (P \wedge \neg Q)$ | $P \rightarrow Q$ |
| :-: | :-: | :-: | :-: |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 0 |

`iv`
| $P$ | $Q$ | $R$ | $P \rightarrow (Q \rightarrow R)$ | $(P \rightarrow Q) \rightarrow R$ |
| :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 1 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

## Question 2
Find a formula that is equivalent to $(P \wedge \neg Q) \vee P$ but shorter
| $P$ | $Q$ | $(P \wedge \neg Q) \vee P$ | $P$ |
| :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 |

## Question 3
Write down the definitions of _`satisfiable`_, _`valid`_, _`unsatisfiable`_ and _`non-valid`_. Explain why any given propositional formula must have exactly two of these properties and `describe the following propositional values`

`i)` $P \vee Q$

`ii)` $P \wedge \neg P$

`iii)` $((P \rightarrow Q) \rightarrow P) \rightarrow P$

`iv)` $(P \wedge \neg P) \rightarrow P$