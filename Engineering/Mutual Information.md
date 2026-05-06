---
type: knowledge-note
created: 2026-05-06 11:04
tags:
aliases:
  - Mutual Information Score
  - MI
---


## Summary
> [!abstract]
> [[Mutual Information]] measures how much knowing one variable reduces uncertainty about another variable.  
> In feature engineering, it estimates how useful a feature may be for predicting the [[Target Variable]].


## Formulation

$$
I(X;Y) = H(Y) - H(Y \mid X)
$$

where:

- $H(Y)$ = uncertainty of target before knowing feature
- $H(Y \mid X)$ = remaining uncertainty after knowing feature
- $I(X;Y)$ = uncertainty reduction

Equivalent form:

$$
I(X;Y)
=
\sum_x \sum_y p(x,y)
\log
\frac{p(x,y)}{p(x)p(y)}
$$

## Interpretation

| MI Score | Meaning |
|---|---|
| $0$ | feature and target are independent |
| low | weak standalone signal |
| high | strong standalone signal |

MI is non-negative:

$$
I(X;Y) \ge 0
$$

## Comparison

| Metric | Detects Linear Relation | Detects Nonlinear Relation |
|---|---:|---:|
| [[Correlation]] | yes | no |
| [[Mutual Information]] | yes | yes |

## Use Cases

Use MI to rank features before deeper feature engineering.

Workflow:

1. compute MI scores
2. inspect high-MI features
3. visualize relationships
4. create transformations/interactions
5. validate with model score

## Limitation

MI is usually univariate. It measures:

$$
I(X_i;Y)
$$

not:

$$
I(X_i, X_j;Y)
$$

So a feature can have low MI alone but become useful through interaction.

Example:

```text
feature A alone: weak
feature B alone: weak
A + B interaction: strong
```

## Practical Rules

- High MI  != automatically keep.
- Low MI does not always mean useless.
- MI does not prove causality.
- MI does not guarantee the model can learn the relationship.
- Use MI on training data only.
- Use visualization after MI ranking.

## Failure Modes

- MI says association, not cause.
- A feature can have high MI but still be hard for a linear model to use.
- MI may miss features useful only in combination.
- A suspiciously high MI score may indicate leakage.

## Connections

- Parent: 
- Similar: [[Feature Selection]], [[Information Gain]], [[Entropy]]
