---
type: knowledge-note
created: 2026-04-20 15:38
tags:
aliases: []
---

### Summary
>[!note]
>A clustering using a **latent variable** $z$, which represents the cluster assignment of each data point.  Each data point  $x_{j}$ is generated from a distribution conditioned on its cluster.

### Latent Variable (Cluster Assignment)
$$
z \sim p_Z(z = k; \pi_k)
$$

- $z$ : cluster label  
- $pi_k$ : prior probability of cluster \( k \)  
- $\sum_k \pi_k$ = 1 

### Data Generation (Likelihood)
$$
x_j \sim p_X(x_j \mid z = k), \quad \text{for } j \in \text{cluster } k
$$

- Each data point is drawn from a distribution depending on its cluster  
- In GMM: this is typically a **Gaussian distribution**

### Joint Probability

Combining prior and likelihood:

$$
p_{X,Z}(x_j, z = k) = p_X(x_j \mid z = k)\, p_Z(z = k; \pi_k)
$$

- $z$ : cluster label  
- $pi_k$ : prior probability of cluster \( k \)  
- $\sum_k \pi_k$ = 1 

- Each data point is drawn from a distribution depending on its cluster  
- In GMM: this is typically a **Gaussian distribution**

## Marginal Probability

We can marginalize over all possible clusters to get the probability of ( $x_j$ ):

$$
p_X(x_j) = \sum_{k=1}^{K} p_{X,Z}(x_j, z = k)
$$


## Posterior Probability (Responsibility)

The probability that ( $x_j$ ) belongs to cluster ( $k$ ) is:

$$
p_{Z|X}(z = k \mid x_j) = \frac{p_X(x_j \mid z = k) p_Z(z = k; \pi_k)}{p_X(x_j)}
$$


## Connections
- **Parent:** [[Clustering Algorithms]]
- **Related:** [[K-Means]], [[EM Algorithm]], [[Latent Variable Models]]