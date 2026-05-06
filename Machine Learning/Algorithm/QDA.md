---
type: knowledge-note
created: 2026-04-19 16:29
tags:
  - Discriminant_Analysis
aliases: []
---


## Summary
> [!abstract] 
> 


### Formulation

According to the model above, the log of the posterior is

$$\begin{split}\log P(y=k | x) &= \log P(x | y=k) + \log P(y = k) + Cst \\
&= -\frac{1}{2} \log |\Sigma_k| -\frac{1}{2} (x-\mu_k)^T \Sigma_k^{-1} (x-\mu_k) + \log P(y = k) + Cst,\end{split}$$

>[!note]
>If in the QDA model one assumes that the covariance matrices are diagonal, then the inputs are assumed to be conditionally independent in each class, and the resulting classifier is equivalent to the Gaussian Naive Bayes classifier



## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]