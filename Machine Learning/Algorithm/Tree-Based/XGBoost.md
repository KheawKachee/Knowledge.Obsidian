---
type: knowledge-note
created: 2026-04-27 19:40
tags:
aliases: []
---

### Summary

> [!abstract] 
> Similar to [[Boosting]], which add regularzation terms and weighted quartile sketch helping gradient more smooth, prevent overfitting and avoiding 'extract greedy' which make XGB faster and scalable


### *Loss Function*

$$
\mathcal{L}(\phi) = \sum_i l(\hat{y}_i, y_i) + \sum_k \Omega(f_k)
$$
The regularization term
$$
\Omega(f) = \gamma T + \frac{1}{2}\lambda \|w_k\|^2
$$

#### The Leaf Penalty: $\gamma \,, T$

- **$T$** is the number of leaves in the tree.
- **$\gamma$ (Gamma)** is Langragian multiplier for pruning.
- $\omega$ is weights
- $\lambda$ is regularization coefficient.

Every time you add a new leaf (a new split), the loss increases by $\gamma$. If the reduction in training loss from a split is less than $\gamma$, XGBoost will choose not to split.

It also penalizes large weights and encourages the model to make small, conservative updates rather than massive jumps. This makes the model more stable and less sensitive to individual outliers.

### Weighted Quartile Sketch

- Sketch : Treat data as grouped of similar data
- Weighted : Treat each group with diffrence importanceness
- Quartile : Cut point of whole data in hand (straight to normal quatile term)

So Weighted quartile sketch is the technique respect to concept of boosting that prioritze residual term while capable for handing large dataset.

### Connections
* **Parent:** [[Boosting]]
* **Similar:** [[ ]]