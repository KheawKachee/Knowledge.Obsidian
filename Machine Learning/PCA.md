---
type: knowledge-note
created: 2026-04-19 22:05
tags:
  - PCA
aliases:
  - Principal Component Analysis
---

## Summary

> [!abstract] 
>A fundamental [[Unsupervised Learning]] technique primarily used for dimensionality reduction, data visualization, and data compression.

### Core Concept

The primary objective of PCA is to find a projection matrix ($P$ or $Q^T$ ) that maps high-dimensional input features (n dimensions) onto a lower-dimensional space ($p$ dimensions, where $p≤n$) .

for first iteration
$$\arg\max_{q_1} \; q_1^{T} X X^{T} q_1 
\quad \text{subject to} \quad q_1^{T} q_1 = 1$$
for later iterations$$\arg\max_{q_2} \; q_2^{T} X X^{T} q_2 
\quad \text{subject to} \quad q_2^{T} q_2 = 1,\; q_2^{T} q_1 = 0$$

### Citeria of Good Projection

- Maximization of Information (Variance)
	The foremost criterion for a good projection vector ($q_1$) is that it must **capture as much information as possible** from the original dataset obtained by maximizing the variance of the projected data $$ZZ^T = q_1^TXX^Tq_1$$
	
- Stability Constrain
	The projection vector $q$ must satisfy $q^Tq = 1$ to ensure stability (no increasing or decreasing).

- Orthogonality Between Components
	Each subsequent projection vector must be orthogonal to all previous ones (e.g., $q_2^Tq_1 = 0$). This ensures that :
	*   Each principal component represents a **unique direction** of variance.
	*   No redundant information shared between the components.
	*   The resulting transformation matrix $Q$ is an **orthogonal matrix**, which simplifies the reconstruction of data.

- Minimization of Reconstruction Error
	A good projection can also be evaluated by how well the original data can be recovered from the lower-dimensional representation. $$\hat{x} = \Omega z$$
	When $p < n$, the first $p$ principal components are considered the "best" because they provide the lowest possible reconstruction error for that specific dimension.

- Practical Utility
	*   **Data Visualization:** A good projection should allow humans to perceive **clusters** and associations in 2D or 3D.
	*   **Data Compression:** A good projection must be **efficient**, highly compression and reconstruction as close to the original as possible.
	*   **Matrix Completion:** A good projection is one that can successfully **interpolate missing values** by extracting "data behavior" even from a partial observation set.


### Implementaion Steps

#### 1. The Lagrangian Formulation

To find the first principal component ($q_1$), PCA sets up a constrained optimization problem: maximize the variance ($q_1^T XX^T q_1$) subject to the constraint that the vector has unit length ($q_1^T q_1 = 1$). This is solved using the **[[Lagrangian Multipliers|Lagrangian Form]]**:
*   The Lagrangian function is defined as $$\mathcal{L}(q, \alpha) = (q^T XX^T q) - \alpha(q^T q - 1)$$where $\alpha$ is the **Lagrange multiplier**.
*   By taking the gradient with respect to $q$ and setting it to zero ($\nabla_q \mathcal{L} = 0$), the stationary point is found at $$XX^T q = \alpha q$$

#### 2. Eigen-decomposition Solutions

The equation $XX^T q = \alpha q$ reveals that the optimal projection vectors ($q$) are the **[[Eigenvector]]** of the matrix $XX^T$.
	- *The First Principal Component $q_{1}$** corresponds to the eigenvector associated with the largest eigenvalue.
	- Subsequent components ($q_2, q_3, \dots, q_p$) are found by solving similar optimization problems with added **orthogonality constraints** (e.g., $q_2^T q_1 = 0$), ensuring each vector captures a unique direction of variance.
	- The final solution is an orthogonal matrix $Q$ composed of these eigenvectors.

#### 3. Minimum-Error and Pseudo-Inverse

An alternative mathematical perspective is the **minimum-error formulation**, which seeks to minimize the squared difference between original data and its reconstruction: $$argmin \quad \sum ||x_j - \Omega z_j||^2$$When the target dimension $p \le n$, the data cannot be perfectly inverted. In these cases, the solution involves using the [[Psudo Inverse]] of the projection matrix ($\Omega$) to provide the best possible $p$-dimensional approximation.

#### 4. Iterative Solutions for Incomplete Data

In the context of **matrix completion** (where data $X$ is missing values), the solution is not a simple one-step eigen-decomposition. Instead, an **iterative algorithm** is used

1. Fill missing values are filled with $\bar{x}_{i,j}$.
2. Solve the following problem by computing the principal components P and Z; then compute Ω using the pseudo inverse (P)
3. Repeats until the **objective loss** is minimized.

## Connections
* **Parent:** [[Unsupervised Learning]][[Clustering]]
* **Similar:** [[ ]]