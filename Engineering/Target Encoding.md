---
type: knowledge-note
created: 2026-05-06 10:48
tags:
  - feature-engineering
aliases:
  - Mean Encoding
  - Target Mean Encoding
  - M-Estimate Encoding
---

# Target Encoding

## Summary
> [!abstract]
> [[Target Encoding]] converts a categorial features into a numeric feature using statistics from the Target Variable.  
> Instead of representing category identity directly, it represents each category by its relationship with the target.

## Formula

Basic target mean encoding:

$$
\text{TE}(c) = \mathbb{E}[y \mid x = c]
$$

where:

- $c$ = category
- $x$ = categorical feature
- $y$ = target
- $\text{TE}(c)$ = encoded numeric value for category $c$

## Smoothed Target Encoding

Raw category means overfit when a category is rare.

Use smoothing:

$$
\text{encoding}(c)
=
w_c \cdot \bar{y}_c
+
(1 - w_c) \cdot \bar{y}
$$

where:

$$
w_c = \frac{n_c}{n_c + m}
$$

- $\bar{y}_c$ = mean target for category $c$
- $\bar{y}$ = global target mean
- $n_c$ = count of category $c$
- $m$ = smoothing strength
- larger $m$ means stronger pull toward global mean

## Use cases

Good for:

- High Cardinality Features
- categorical columns with many levels
- categories where one-hot encoding creates too many columns
- tree models, linear models, and boosting models
- domain-motivated categorical features

Examples:

- zipcode → average rating
- product category → average conversion rate
- user segment → churn rate
- parasite image source/lab/device → class tendency

Careful about:
- [[Data Leakage]] problem which fixed by
	- use [[Cross Validation]]
	- fit encoding inside each fold only
	- never fit encoders on validation/test target
- Rare categories overfit
- Temporal data leakage (time series) 
- Target Distribution Shift

## Connections

- Parent: 
- Similar: [[Categorical Encoding]], [[Mean Encoding]], [[Leave One Out Encoding]]
- Opposite: [[One Hot Encoding]], [[Label Encoding]]
- Risk: [[Data Leakage]], [[Overfitting]]
- Used with: [[Ensemble Decision Tree]]