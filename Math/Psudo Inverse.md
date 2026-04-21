---
type: knowledge-note
created: 2026-04-19 23:05
tags:
aliases: []
---


## Summary

> [!abstract]
> The **Moore–Penrose Pseudo Inverse** generalizes matrix inversion to non-square or singular matrices.  
> It provides a least-squares solution to linear systems and is widely used in regression, SVD, and machine learning.

### **Definition (Moore–Penrose conditions)**
$$
A^+ = \text{the unique matrix satisfying:}
$$
$$
AA^+A = A
$$
$$
A^+AA^+ = A^+
$$
$$
(AA^+)^T = AA^+
$$
$$
(A^+A)^T = A^+A
$$

### **SVD-based computation**
$$
A = U \Sigma V^T
$$
$$
A^+ = V \Sigma^+ U^T
$$

### **Least squares solution**
$$
\hat{x} = A^+ b
$$
### **Full column rank case**
$$
A^+ = (A^T A)^{-1} A^T
$$

### **Full row rank case**
$$
A^+ = A^T (A A^T)^{-1}
$$



## Connections

* **Parent:** 
* **Similar:** 