---
type: knowledge-note
created: 2026-04-19 22:48
tags:
aliases: []
---

### Summary

> [!abstract]
> Eigenvectors are special directions of a matrix transformation that **do not change direction**, only scale by a factor (the eigenvalue).

### Definition

Given a square matrix:

$$
A \in \mathbb{R}^{n \times n}
$$

A vector $$ v \neq 0 $$ is an **eigenvector** if:

$$

A \mathbf{v} = \lambda \mathbf{v},
\quad \text{where } \lambda \text{ is an eigenvalue and } \mathbf{v} \text{ is the corresponding eigenvector.}

$$


### Properties

- Most vectors **change direction** after transformation. Eigenvectors **stay on the same line** but change it's size.
- Eigenvectors are **linearly independent** (if eigenvalues distinct)  
- Symmetric matrix → eigenvectors are **orthogonal**  
- Diagonalization : $A = Q \Lambda Q^{-1}$



### How to Find Eigenvectors

Start from:

$$
A v = \lambda v
$$

Rearrange:

$$
(A - \lambda I)v = 0
$$

For non-trivial solution $$ v \neq 0 $$
$$
\det(A - \lambda I) = 0
$$

#### Steps

1. Solve characteristic equation → eigenvalues $$ \lambda $$
2. Plug back → solve $$ (A - \lambda I)v = 0 $$
3. Get eigenvectors $$ v $$

### Geometric Meaning

- Matrix = transformation  
- Eigenvector = invariant direction  
- Eigenvalue = scaling factor  

| Eigenvalue | Effect |
|----------|--------|
| $$ \lambda > 1 $$ | Stretch |
| $$ 0 < \lambda < 1 $$ | Shrink |
| $$ \lambda < 0 $$ | Flip direction |
| $$ \lambda = 0 $$ | Collapse to zero |


### Example

Let:

$$
A =
\begin{bmatrix}
2 & 0 \\
0 & 3
\end{bmatrix}
$$

Then:

$$
v_1 =
\begin{bmatrix}
1 \\
0
\end{bmatrix}, \quad \lambda = 2
$$

$$
v_2 =
\begin{bmatrix}
0 \\
1
\end{bmatrix}, \quad \lambda = 3
$$


