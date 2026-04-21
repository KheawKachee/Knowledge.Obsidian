---
type: knowledge-note
created: 2026-04-19 17:11
tags:
  - Tree_Based
aliases: []
---


### Summary

> [!abstract] 
> Recursive binary splitting is the fundamental, top-down, greedy algorithm used to partition the feature space into distinct regions. Because it is computationally infeasible to consider every possible partition of data simultaneously, this approach builds the tree through a sequence of local optimizations.


### The Mechanism of Splitting

The process follows a specific logical structure to build a "big tree" from many "small trees":
Top-Down Approach: The algorithm begins at the very top of the tree, where all observations initially belong to a single region.

- **Greedy Logic:** At each step, the algorithm identifies the best split for that particular node without considering whether a different split might lead to a better tree overall in later steps.
- **Binary Splitting:** The algorithm successively splits the predictor space into exactly two child nodes (left and right) based on a threshold value.
- **Threshold Selection:** To find the optimal "cut," the algorithm typically sorts the training samples and evaluates which feature and specific value (threshold) provide the ==most significant improvement in [[Node Purity]].

### Optimization and Purity Metrics

The goal of each split is to create child nodes that are more ***pure*** than the parent node. The method for measuring this depends on the task

- Regression Trees: The algorithm seeks to minimize the [[Node Purity#Sample Variance|sample variance]]. It chooses the threshold that offers the greatest variance reduction, which is the differenc.e between the variance of the parent and the weighted variance of the two children.
- Classification Trees: The algorithm aims to minimize the classification error rate. This is measured using Information Gain based on either [[Node Purity#Entropy|Entropy]] (which measures uncertainty) or the [[Node Purity#Gini Index|Gini Index]] (which measures total probability across classes).


## Connections
* **Parent:** [[Decision Tree]] 
* **Similar:** [[ ]]