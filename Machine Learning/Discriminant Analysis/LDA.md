---
type: knowledge-note
created: 2026-04-19 16:28
tags:
  - Discriminant_Analysis
aliases: []
---


## Summary
> [!abstract] 
> 


### Formulation

[[LDA]] is a special case of [[QDA]], where the Gaussians for each class are assumed to share the same covariance matrix: $\Sigma_k = \Sigma$ for all k. This reduces the log posterior to : 

$$\log P(y=k | x) = -\frac{1}{2} (x-\mu_k)^T \Sigma^{-1} (x-\mu_k) + \log P(y = k) + Cst.$$

The log-posterior of LDA can also be written [3] as

$$\log P(y=k | x) = \omega_k^T x + \omega_{k0} + Cst.$$



## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]