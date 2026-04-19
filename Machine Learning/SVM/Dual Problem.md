---
type: knowledge-note
created: 2026-04-19 01:31
tags:
  - SVM
aliases: []
---


## Summary
> [!abstract] 
> reformulated version of the primal problem, derived using [[Lagrangian multipliers]] $(\alpha , \beta)$ and [[Karush-Kuhn-Tucker]] (KKT) conditions

## Concept

**Training data:** data pairs $\{x_j, y_j\}$

$$
\arg\max_{\alpha,\beta \in \mathbb{R}^n}
\mathbf{1}^T \alpha
-\frac{1}{2}\sum_{i=1}^{m}\sum_{j=1}^{m}\alpha_i\alpha_j y_i y_j x_i^T x_j
$$

subject to

$$
\sum_{j=1}^{m}\alpha_j y_j = 0
$$

$$
\alpha_j = C - \beta_j,\qquad \alpha_j,\beta_j \ge 0
$$

for $j=1,\ldots,m$

**Inference:** given an input $x$

$$
f(x)=x^T\hat{w}+\hat{b}
$$

- $\hat{w}=\sum_{j=1}^{m}\hat{\alpha}_j y_j x_j$, where each pair $\{x_j,y_j\}$ is from the training data. $\hat{\alpha}_j$ often takes value $0$.
- $\hat{b}_j = y_j - \hat{w}^T x_j$ for each pair $\{x_j,y_j\}$.

## Differences from Primal Problem

1. Minimize $\alpha$ ([[Lagrangian multipliers]]) instead of $w$ (geometric margin)
2. parameters like $w,b$ is not learned parameters but product of $\alpha$

### Reasons to use

1. **Computational Efficiency:** Solving for α in the dual form can be more efficient, especially when dealing with high-dimensional input features since it's mostly ***zeros***.
2. **Sparsity and Support Vectors:** In the dual solution, the value of $\alpha_j$ for most non-critical data points becomes ***zero***. Only points with non-zero $α$ are the **support vectors** allowing the model to discard the majority of the training data during inference.
3. **The "[[Kernel Mapping]]":** Because the dual form uses dot products, these products can be replaced with a **kernel function (**$K(x_i​,x_j​$)**)**. This allows SVM to implicitly map data into a **higher-dimensional kernel space**, enabling it to find linear separations for data that is nonlinearly separable in its original space.
4. **Relationship to Primal Variables:** Once the dual problem is solved for $\hat{\alpha}$, the original primal parameters $\hat{w}$ and $\hat{b}$ can be easily reconstructed using the derived relationship.

## Connections
* **Parent:** [[SVM]]
* **Similar:** [[ ]]