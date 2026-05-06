---
type: knowledge-note
created: 2026-04-20 15:38
tags:
aliases: []
---

### Summary
>[!note]
>A clustering using a **latent variable** $z$, which represents the cluster assignment of each data point.  Each data point  $x_{j}$ is generated from a distribution conditioned on its cluster.

### Core Concept

The probability that the kth cluster exists is controlled by pZ
$$
z \sim p_Z(z = k; \pi_k)
$$
- $z$ : latent cluster label  
- $\pi _k$ : prior probability of cluster   
- $\sum_k p_{z}(z=k ;\pi_k)$ = 1 

$$x_j \overset{\text{iid}}{\sim} p_X(x_j \mid z = k), \quad \text{for } j \in \text{the } k\text{-th cluster}$$
- Since the problem assumed for independently identical generation for distributions  

Probability that  “cluster k was chosen AND it produced $x_{j}$​”
$$p_{X,Z}(x_j, z = k) = p_{X \mid Z}(x_j \mid z = k)\, p_Z(z = k; \pi_k)$$
Sum over all possibilities that each cluster could have produce that $x$ to get **marginal probability**
$$p_X(x_j) = \sum_{k=1}^{K} \pi_k \, p_{X|Z}(x_j \mid z = k)$$
use [[Bayes Theorem]] to reverse into generative problem 
$$p_{Z \mid X}(z = k \mid x_j) =
\frac{p_Z(z = k; \pi_k)\, p_X(x_j \mid z = k)}{p_X(x_j)}$$

This is called ==**Mixture Model**==

>[!note]
> We use $p_X(x)$ (not $p_{X \mid Z}$) because it represents the **total probability of observing $x$ across all clusters**, which is required to normalize $p(z \mid x)$ into a valid probability distribution.

![[Pasted image 20260421203322.png]]


In **Gaussian Mixture Model**, we define:

* $p(z = k) = \pi_k$ → mixing weight
* $p(x_j \mid z = k) = \mathcal{N}(x_j \mid \mu_k, \Sigma_k)$ → Gaussian
* $p(x_j) = \sum_{k=1}^K \pi_k, p(x_j \mid z = k)$ → mixture

Then, Gaussian distribution for cluster (k)

$$  
p_{X}(x_j) = \sum_{k=1}^{K} \pi_k \times \mathcal{N}(x_j \mid \mu_k, \Sigma_k)
$$  
Which is total probability of each $Likelihood \, \times \, Prior$
So Bayes becomes

$$  
\tau_{jk} := p(z = k \mid x_j) =  
\frac{\pi_k , p_{X|Z}(x_j \mid z = k)}{p(x_j)}  
$$
![[Pasted image 20260421205101.png]]

### Advantages:
- GMMs can model clusters with various shapes depending on the assumption imposed on the covariance matrix, i.e., $Σz_{k}$. Thus, it is more flexible than K-mean clustering.
- GMMs have probabilistic assignment, which gives a better overview of how likely the data can be grouped into different clusters.
### Disadvantages:
- Similar to [[K-Mean]] clustering, it needs a predefined value of the number of clusters K. Also, the initial parameter estimates can affect the final result.
- Similar to K-mean clustering, GMMs do not have a function to identify noises in data samples.
- GMMs are more computationally intensive than K-mean clustering.


## Connections
- **Parent:** [[Clustering]]
- **Related:** [[K-Mean|K-Means]], [[EM Algorithm]], [[Latent Variable Models]]