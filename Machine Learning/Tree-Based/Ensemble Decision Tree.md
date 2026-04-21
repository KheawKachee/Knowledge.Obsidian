---
type: knowledge-note
created: 2026-04-19 17:16
tags:
  - Tree_Based
  - Ensemble_Tree
aliases:
  - Ensemble Technique
---


## Summary

> [!abstract] 
>Advanced techniques in tree-based methods—specifically **[[Bagging]]**, **[[Random Forests]]**, and **[[Boosting]]**—are designed to address the inherent weaknesses of single decision trees, such as their high variance, instability, and tendency to overfit training data. While a single decision tree is naturally nonlinear and mirrors human logic, it is highly sensitive to small changes in training data, which can result in a completely different tree structure. These advanced methods typically utilize **weak learners** (simple models) and combine their results to create a more powerful and generalized model.

### 1. Bagging (Bootstrap Aggregation)

![[Bagging#Summary]]
### 2. Random Forests

![[Random Forests#Summary]]

### 3. Boosting

![[Boosting#Summary]]

### 4. Key Concepts in Advanced Tree Methods

*   **[[Bagging#Out-of-Bag (OOB) error estimation|Out Of Bag Estimation]]:** In Bagging and Random Forests, approximately one-third of the data is typically left out of each bootstrapped training set. These "out-of-bag" samples act as a built-in validation set to estimate model performance without wasting training data.
*   **Variable Importance:** While ensemble methods are less interpretable than a single tree, the importance of specific features can still be measured by recording how much each feature reduces variance (in regression) or increases information gain (in classification) across all trees.
*   **Interpretability vs. Complexity:** There is a trade-off: as the complexity (number of trees or depth) increases, the model's accuracy generally improves, but its interpretability decreases.

### *insert here*

## Connections
* **Parent:** [[Decision Tree]]
* **Similar:** [[ ]]