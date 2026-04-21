---
type: knowledge-note
created: 2026-04-19 18:35
tags:
  - Ensemble_Tree
  - Tree_Based
aliases: []
---

### Summary

> [!abstract] 
> Random Forest is an advanced ensemble technique built upon the foundation of [[Bagging]] to improve the performance and robustness. While Bagging focuses on reducing variance by averaging multiple independent trees, Random Forests introduce a critical mechanism to decorrelate these trees, leading to a more thorough exploration of the model space.


### Core Concepts

- **Feature Sampling:** In addition to sampling data ([[Bagging]]), Random Forests also **randomly sample a subset of features** at each split in the tree-building process. This ensures that each tree is ==decorrelated== from each others.
* **Performance:** The sources indicate that decreasing the number of features used at each split (often $\sqrt{p}\quad \text{or}\quad \frac{p}{2}$ ) can significantly improve performance and lower error.
* **Parallelism** : Random forest also inherit the parallelness from [[Bagging]].
 

### *insert here*

## Connections
* **Parent:** [[Ensemble Decision Tree|Ensemble Technique]] [[Bagging]]
* **Similar:** [[Bagging]], [[Boosting]]