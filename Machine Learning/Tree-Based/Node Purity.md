---
type: knowledge-note
created: 2026-04-19 17:31
tags:
aliases: []
---


### Summary

> [!abstract] 
> node purity is a fundamental metric used to determine how to partition data into distinct regions. A node is considered pure if all the data samples within it belong to the same class. Conversely, a node is impure if it contains a mixture of samples from different classes.


### Metrics for Measuring Purity

For classification tasks, the sources identify two primary mathematical tools to quantify this purity: Entropy and the Gini Index.

#### Sample Variance

- $$\frac{1}{M - 1} \sum_{i=1}^{M} (y_i - \bar{y})^2$$
-  For regression task, we use sample variance to measure the purity of node, higher variance leads to impurity.

> [!notes]
> RSS is applied in decision tree problem formulation while sample variance used finding best threshold to split data in [[Recursive Binary Splitting]]

### Core Concept

The better splitting threshold gives the more variance reduction

$$R = \operatorname{Purity}(\text{Parents}) - \sum_{i \in \{L, R\}} w_i \operatorname{Purity}(\text{Child}_i)$$
where $w_{i}$is the ratio of the samples in the left/right child nodes against the total number of
samples without splitting.

#### Entropy

- $$- \sum_{c \in C} \hat{p}(y_{R_t} = c)\,\log \hat{p}(y_{R_t} = c)$$
- This measures purity through certainty and uncertainty. The entropy value is near zero when the samples in a node are nearly all from one class (high certainty/high purity). It reaches its maximum (e.g., 0.5 in a two-class setting) when the classes are perfectly mixed, indicating high uncertainty and low purity. 

#### Gini Index

- $$1 - \sum_{c \in C} \hat{p}(y_{R_t} = c)^2$$
- This measures purity via the total probability of the assigned classes. Like entropy, a small Gini value indicates that the node is highly pure, while a larger value indicates higher impurity. 


For both metrics, the higher the Entropy or Gini index, the lower the node purity. These two quantities generally provide very similar results when evaluating potential splits.



## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]