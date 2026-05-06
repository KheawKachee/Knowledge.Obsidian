---
type: knowledge-note
created: 2026-04-27 21:48
tags:
aliases: []
---


### Summary

> [!abstract] 
> In machine learning, a **Feature Utility Metric** evaluates the contribution of individual features to a model's predictive power. While simple correlation is a common starting point, a "full option" suite involves looking at interaction, non-linear relationships, and model-specific importance.

## 1. Statistical & Model-Agnostic Metrics

These metrics evaluate features independently of any specific machine learning algorithm.

- **Mutual Information (MI):** Measures the dependency between two variables. Unlike correlation, MI captures **non-linear** relationships by calculating how much information is shared between the feature and the target.

- **Spearman’s Rank Correlation:** Assesses monotonic relationships. It is more robust than Pearson correlation because it relies on the rank of values rather than the raw values themselves.

- **Fisher Score:** Often used in supervised learning to find features such that in the selected feature space, the distances between data points of different classes are maximized, while distances between data points of the same class are minimized.

## 2. Model-Based Importance (Embedded)

These are derived directly from the training process of specific algorithms.

- **Gini Importance (Mean Decrease Impurity):** Used in Random Forests and Decision Trees. It calculates how much each feature reduces the impurity (Gini or Entropy) across all nodes.

- **Permutation Importance:** A robust technique where you randomly shuffle a single feature's values and measure the drop in model score. If the score plunges, the feature is highly "useful."

- **Weight/Gain/Cover (XGBoost/LightGBM):**
    - **Weight:** Number of times a feature is used to split data.
    - **Gain:** The average reduction in loss brought by the feature.
    - **Cover:** The number of observations related to the feature.


## 3. Information Theory & Advanced Utility

For complex pipelines, these metrics provide a deeper "utility" profile:

- **SHAP (SHapley Additive exPlanations):** Based on cooperative game theory. It assigns each feature an edge value for a specific prediction, breaking down exactly how a feature moves the output from the base value.
- **LOFO (Leave One Feature Out):** A rigorous metric that calculates the model performance by iteratively removing one feature at a time. It accounts for both the feature's importance and its redundancy.
- **Principal Component Analysis (PCA) Loading:** In unsupervised contexts, loadings tell you how much each original variable contributes to the principal components that capture the most variance.

### Comparison Table

|**Metric**|**Captures Non-Linear?**|**Computational Cost**|**Best Use Case**|
|---|---|---|---|
|**Pearson Correlation**|No|Very Low|Quick linear screening|
|**Mutual Information**|Yes|Moderate|Capturing complex dependencies|
|**Permutation Importance**|Yes|High|Validation-set utility|
|**SHAP Values**|Yes|Very High|Explainability and local utility|
|**Gain (GBDTs)**|Yes|Low (Post-train)|Fast ranking for tree models|

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]