---
type: knowledge-note
created: 2026-04-19 00:30
tags:
  - SVM
aliases: []
---


## Summary
> [!abstract] 
> 


### The Optimization Problem
The hard margin is defined by the following quadratic programming problem:

$$\min_{b \in \mathbb{R}, w \in \mathbb{R}^n} \frac{1}{2} \|w\|_2^2$$
$$\text{subject to: } y_j (w^T x_j + b) \geq 1, \quad j = 1, \dots, m$$


Because the constraint $y_j (w^T x_j + b) \geq 1$ is **strict**, every single data point must lie on the correct side of the margin. This leads to two major issues in real-world data:

* **Sensitivity to Outliers:** A single noisy data point near the decision boundary forces the margin to shrink or the hyperplane to tilt *significantly* to maintain "perfect" classification.
* **Non-Linearly Separable Data:** If a single point from Class A crosses into the cluster of Class B, the Hard Margin SVM will fail to find any feasible solution (the solver will return no result).

To handle noise and blurry boundaries, we introduce **slack variables** $\xi_j$ and a regularization parameter $C$ in [[Soft Margin]]

## Connections
* **Parent:** [[SVM]]
* **Similar:** [[Soft Margin]]