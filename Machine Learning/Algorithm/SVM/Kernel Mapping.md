---
type: knowledge-note
created: 2026-04-19 01:59
tags:
  - SVM
aliases:
  - Kernel Trick
---


## Summary
> [!abstract] 
> While a standard [[SVM]] seeks a linear "knife-like" cut to separate two classes, the nonlinear version uses mathematical transformations to address more complex data distributions.


### Mechanism

- **Dimensionality Expansion:** The "beautiful part" of [[SVM]] is that these kernels map input features into a higher-dimensional **"kernel space"** with a kernel function $K(x_i​,x_{j}​)$.
- **The Linear Cut in Higher Space:** Once the data is mapped into this enlarged space, a standard **linear hyperplane** can often cut the data quite neatly, even if a straight line was impossible in the original lower-dimensional space.

### Types

- Polynomial:
$$
K(x_1, x_2) = (\gamma x_1^T x_2 + \beta)^d
$$

- Radial Basis (RBF): a real-valued function whose output depends solely on the Euclidean distance between an input point and a fixed center.
$$
K(x_1, x_2) = e^{-\gamma \|x_1 - x_2\|_2^2}
$$
	γ is the decay rate of RBF.
	- Low γ : the model cannot capture the complexity of data ⇒ underfitting.
	- High γ : the model considers only the support vector itself ⇒ overfitting.
- Tanh (Sigmoid):
$$
K(x_1, x_2) = \tanh(\gamma x_1^T x_2 + \beta)
$$

## Penalty Parameter $(c)$

$C$ is the penalty parameter common to all choices of kernel
- Low C : SVM will allow the inclusion of the wrong sides and can be very rough (high bias), if too small. ⇒ Underfitting to training data. 
- High C : SVM will strictly classify the data according to its label and can exhibit high variance, if too large. ⇒ Overfitting to training data.
## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]