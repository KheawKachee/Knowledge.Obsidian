---
type: knowledge-note
created: 2026-05-06 10:40
tags:
aliases: []
---
## Summary

> [!abstract] 
> EfficientNet addresses the problem of scaling Convolutional Neural Networks (CNNs) efficiently. Traditionally, researchers scaled models by increasing only one dimension: **Depth** (layers), **Width** (channels), or **Resolution** (image size). EfficientNet introduces **Compound Scaling**, which scales all three dimensions together using a fixed ratio.


## Compound Scaling

EfficientNet’s compound scaling approach aims to scale neural networks across three dimensions: depth, width, and resolution in a balanced way. The goal is to *maximize accuracy* while staying within resource constraints, such as memory and computational power. This creates an optimization problem finding the best combination of scaling factors to maximize accuracy while staying within resource limits.

## Parameters
1. **Depth ($d$):** More layers capture more complex features but suffer from vanishing gradients.
2. **Width ($w$):** More channels capture finer details but saturated quickly in accuracy gains.
3. **Resolution ($r$):** Higher input resolution allows the network to see smaller patterns but increases computational cost significantly.

