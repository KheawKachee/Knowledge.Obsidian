---
type: knowledge-note
created: 2026-05-11 22:39
tags:
aliases: []
---
### Summary

> [!abstract] 
> Straight-Through Estimator is a gradient approximation technique that lets gradients pass through non-differentiable operations during backpropagation.


### Components

1. Forward Pass : use the real non-differentiable operation during model prediction, such as rounding, sampling, or nearest-neighbor lookup $$z_q(x) = \text{quantize}(z_e(x))$$

2. Backward Pass : approximate the gradient by copying the gradient from the output back to the input as if the operation were an identity function $$\frac{\partial z_q}{\partial z_e} \approx I$$

3. Stop Gradient Trick : control which part of the computation receives gradient update $$z_q = z_e + \text{sg}[e - z_e]$$


## Connections
* **Parent:** 
* **Similar:** 