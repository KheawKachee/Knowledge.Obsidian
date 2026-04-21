---
type: knowledge-note
created: 2026-04-19 16:16
tags:
  - Tree_Based
aliases: []
---


### Summary

> [!abstract] 
> A Decision Tree is a fundamental classifier and regressor that serves as the primary building block for the broader category of Tree-Based Methods. Within this context, a single decision tree is a "weak learner" that uses a flowchart-like structure to make predictions by partitioning the feature space into distinct regions.


### Components

1. [[Leaf Nodes]] : represent final classification and regression
2. [[Decision Nodes]] : contain threshold values to split data (Including the root node)
3. [[Node Purity]] : To decide best threshold for each [[Decision Nodes]]

### Method

use [[Recursive Binary Splitting]] , top to toe + greedy approach to select best split threshold in each Decision nodes, recursively, until the node become [[Leaf Nodes]] with judge by [[Node Purity]]. 

### Advantages

- Tree-Based algorithm is non-parametric (classified data without any assumptions unlike [[LDA]] or [[QDA]] or [[Kernel Mapping|Kernel Trick]]'s [[SVM]]). 
- Trees can easily handle qualitative predictors without the need to create dummy variables

### Disadvantage

- Basic decision tree usually underperform in terms of variance since the `cut` is basically splitting half-half-like.
- A single decision tree is notoriously unstable; a small change in the training data can result in a completely different tree structure. They are also highly ==prone to overfitting== (high variance), especially as the tree grows deeper. 

>[!note]
>To address the instability and overfitting of single decision trees, tree-based methods evolve into [[Ensemble Decision Tree|Ensemble Technique]] that combine multiple trees into a single powerful model.

### Training Parameters

#### Parameter : Splitting Thresholds 

Primary parameter that accquired during training steps to identifies specific threshold values to split data.
#### Hyper Parameters

1. `max_depth` : Specifies the maximum number of levels the tree can grow. Deep trees can capture complex patterns but are highly prone to overfitting; shallow trees may underfit.
2. `min_samples_split`: The minimum number of samples an internal node must contain to be eligible for a split. Smaller value creates very small data groups.


## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]