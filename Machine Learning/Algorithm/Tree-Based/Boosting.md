---
type: knowledge-note
created: 2026-04-19 18:34
tags:
  - Ensemble_Tree
  - Tree_Based
aliases: []
---
### Summary

> [!abstract] 
> Boosting is an [[Ensemble Decision Tree|Ensemble Technique]] that builds models sequentially, where each new model focuses on correcting the errors made by the previous ensemble.

Boosting differs from Bagging and Random Forests because models are **trained sequentially**, not independently.

## Boosting Algorithm

Boosting can be viewed as a **stage-wise additive model**:

$$
f(x) = \sum_{t=1}^{T} \lambda f_t(x)
$$

### Loss Function

$$L(h(x),y) = \frac{1}{2}\lvert\lvert \hat{y}-y \rvert\rvert^2_{2}$$

### Steps:

1. Compute residuals (for MSE case):

$$
r_j^{(t)} = y_j - \hat{y}_j^{(t-1)}
$$

Train weak learner:

$$
f_t(\cdot; \beta_t) = \operatorname{Train}\left( \{ (x_j, r_j^{(t)}) \}_{j=1}^{m} \right)
$$

2. Update model:

$$
f_{\text{Boost}}^{(t)}(x) = f_{\text{Boost}}^{(t-1)}(x) + \lambda f_t(x)
$$

3. Update prediction:

$$
\hat{y}_j^{(t)} = f_{\text{Boost}}^{(t)}(x_j)
$$

where \( \lambda \) is the shrinkage (learning rate).


### Effect of  $\lambda$

- Large $\lambda$ : faster learning, higher risk of overfitting  
- Small $\lambda$ : slower learning, better generalization  


## Gradient Boosting

Generalizes boosting by optimizing a loss function:

$$
r_j^{(t)} = - \left. \frac{\partial L(y_j, f(x_j))}{\partial f(x_j)} \right|_{f = f^{(t-1)}}
$$

Each model fits the **negative gradient (steepest descent direction)**.



## Connections

* **Parent:** [[Ensemble Decision Tree|Ensemble Technique]]
* **Similar:** [[Bagging]], [[Random Forests]]