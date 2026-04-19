---
type: knowledge-note
created: 2026-04-19 00:30
tags:
  - SVM
aliases: []
---


## Summary
> [!abstract] 
> Reslove [[Hard Margin]] with noisy points by using [[Slack Variables]] with $C$

## Key Ideas
###  Soft Margin
To handle noise and blurry boundaries, we introduce **slack variables** $z_j$ and a regularization parameter $C$:

$$\min_{w, b, z_j} \frac{1}{2} \|w\|_2^2 + C \sum_{j=1}^{m} z_j$$
$$\text{s.t. } y_j (w^T x_j + b) \geq 1 - z_j \quad \text{and} \quad z_j \geq 0$$

* **Large $C$:** Behaves like a [[Hard Margin]] (minimizes misclassification at all costs).
* **Small $C$:** Allows for a wider margin and some misclassifications, leading to better generalization on noisy data.

This is a **convex quadratic programming** problem because it has a quadratic objective function and linear constraints



## Connections
* **Parent:** [[SVM]]
* **Similar:** [[ ]]