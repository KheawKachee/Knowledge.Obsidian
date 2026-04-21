---
type: knowledge-note
created: 2026-04-19 18:34
tags:
  - Tree_Based
  - Ensemble_Tree
aliases:
  - Bootstrap Aggregation
---


### Summary

> [!abstract] 
> These advanced techniques generally involve combining multiple weak learners (simple models) to create model that generalizes better to testing data and addresses the overfitting problems inherent in single decision trees.


### Mechanism

#### Bootstrap Sampling 

The process to sampling data from dataset and train the model with that limited data. We called these models `weak learners`

#### Aggregation

After we got trained weak learners, we predict the outcome using aggregated infrences from those models.
- Classification : $f_{\text{Bag}}(x) = \operatorname{Majority}\left\{ f_b(x) \mid b \in \{1,2,\ldots,B\} \right\}$
- Regression :  $f_{\text{Bag}}(x) = \frac{1}{B} \sum_{b=1}^{B} f_b(x)$

#### Parallelism

Since each learner can be trained independently, it give parallelness and make the training process more efficiently.

### Out-of-Bag (OOB) error estimation 

On average, approximately two-thirds of the data is used to train any single bagged tree. The remaining one-third of the samples that were not included in the training set for a specific tree are known as the "out-of-bag" (OOB) samples.

1. Identifies all the trees that did not use that specific observation for training.
2. Aggregate prediction made from that left out observation.
3. Compared to the actual ground truth to determine the error rate.
4. Average these errors across all samples in the dataset.

This OOB method squezze every drop of dataset since no data is left out not using during training steps unlike `train-test-split` that exclude a portion of data.


### Limitation

This method prune to ==few dominant features== that correlate to prediction. Those features will be chosen as threshold across weak learners resulting a collection of high correlated trees. It later be patched by [[Random Forests]].

## Connections
* **Parent:** [[Ensemble Decision Tree|Ensemble Technique]]
* **Similar:** [[Boosting]], [[Random Forests]]