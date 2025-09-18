# Binary Logic

Once upon a time I was in a Mathematical Physics lecture when the professor said something along the lines "P if and only if Q" means you have to prove "P implies Q" and "Q implies P".

```math
\textnormal{(\textit{P if and only if Q}) means } (P \iff Q) \textnormal{ which means } ((P \implies Q) \land (P \impliedby Q))
```

But this sounded somewhat off to me. The use of the double arrow seemed to mean something different than the English sentence. Intuitively, I understood the sentence "P if and only if Q" to mean "P implies Q" and "False P implies False Q", that is

```math
\textnormal{(\textit{P if and only if Q}) to mean } ((P \implies Q) \land (¬P \implies ¬Q))
```

On the other hand, the double arrow did communicate the intuition of "P implies Q" and "Q implies P".

I then took it upon myself to understand if and how these two interpretations of the statement were connected. More generally, I was interested in understanding the full implications of logical equivalence. From past experiences, logical equivalence seemed to mean that two statements would always share the same truth value, knowing the state of one proposition would be definitive to know the state of the other. The overall goal was to show if the following was always the case

```math
\begin{aligned}
(P \iff Q) \textnormal{ means:} \\\\
P \implies Q \\\\
Q \implies P \\\\
¬P \implies ¬Q \\\\
¬Q \implies ¬P \\\\
\end{aligned}
```


## Contrapositives

The implication of a contrapositive

```math
(P \implies Q) \implies (¬Q \implies ¬P)
```

is readily proven because $¬Q$ and $P$ coexisting would be a contradiction to the (assumed true) $P \implies Q$. So a truth statement implies the truth of its contrapositive. Notice that we are not assuming anything about $P$ or $Q$ individually, but rather we are discussing their relation. One can apply the same argument to a contrapositive as the prior known, that is

```math
(¬Q \implies ¬P) \implies (¬(¬P) \implies ¬(¬Q))
```
Because we are dealing only with binary values of logic, $¬(¬P)$ is exactly $P$, then

```math
(¬Q \implies ¬P) \implies (P \implies Q)
```

Note that the above relations are true irrespective of the value of the atomic propositions $P$ and $Q$, since the outer implication is only applicable when the inner left one is true. When $(¬Q \implies ¬P)$ happens to be true, then we are ensured of $(P \implies Q)$ being true as well. The question then arises: what if it is false that $(P \implies Q)$? What does this imply for its contrapositive? You might be inclined to propose

```math
¬(P \implies Q) \implies ¬(¬Q \implies ¬P)
```

And this turns out to be correct. A proof by contradiction on the known relation $(¬Q \implies ¬P) \implies (P \implies Q)$ would suffice. It's impossible for the implication $(P \implies Q)$ be false while $(¬Q \implies ¬P)$ remain true, we would be reaching a contradiction. Alternatively, one could view $¬(P \implies Q) \implies ¬(¬Q \implies ¬P)$ as the contrapositive to $(¬Q \implies ¬P) \implies (P \implies Q)$ and we have established contrapositives always follow. The same can be said about the other relation,

```math
¬(¬Q \implies ¬P) \implies ¬(P \implies Q)
```

For contrapositives, one then has

```math
\begin{aligned}
(P \implies Q) \iff (¬Q \implies ¬P) \textnormal{ means always true that:} \\\\
(P \implies Q) \implies (¬Q \implies ¬P) \\\\
(¬Q \implies ¬P) \implies (P \implies Q) \\\\
¬(P \implies Q) \implies ¬(¬Q \implies ¬P) \\\\
¬(¬Q \implies ¬P) \implies ¬(P \implies Q) \\\\
\end{aligned}
```
So absolute sharing of truth value is true for an implication and its contrapositive. That is, they are logically equivalent.


## Logical Equivalence between General Propositions

Having it proved for a proposition and its contrapositive turns out to be enough for the general case. We are ensured of

```math
\begin{aligned}
(P \implies Q) \iff (¬Q \implies ¬P) \\\\
(Q \implies P) \iff (¬P \implies ¬Q) \\\\
\end{aligned}
```

It is then clear that for logical equivalence, out of

```math
\begin{aligned}
P \implies Q \\\\
Q \implies P \\\\
¬P \implies ¬Q \\\\
¬Q \implies ¬P \\\\
\end{aligned}
```

Only two are independent of each other. One needs to prove either $(P \implies Q)$ or $(¬Q \implies ¬P)$ and either $(P \impliedby Q)$ or $(¬P \impliedby ¬Q)$. Now it becomes clear that interpreting "P if and only if Q" to mean "P implies Q" and "False P implies False Q" is equivalent to interpreting it as "P implies Q" and "Q implies P". They contain the same information.
