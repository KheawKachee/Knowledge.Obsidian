---
type: knowledge-note
created: 2026-05-17 16:55
tags:
  - math
  - CNN
aliases: []
---


### Summary

> [!abstract] 
> While a **[[Depthwise Convolution]]** filters spatial features channel-by-channel without mixing them, **Pointwise Convolution** does the exact opposite. It uses a $1 \times 1$ kernel to look at a single pixel across all channels simultaneously, mixing **channel information** while ignoring surrounding spatial context.

### Methodology

1. **The $1 \times 1$ Kernel:** The filter size is strictly fixed at $1 \times 1 \times M$ (where $M$ is the number of input channels).
2. **Channel Mixing:** The kernel slides across the spatial dimensions ($H \times W$). At each pixel "point," it computes a weighted sum across all channels.
3. **Channel Manipulation:** By applying $N$ different $1 \times 1$ filters, you can freely change the output channel depth to $N$.

> Think of a pointwise convolution as applying a standard Multi-Layer Perceptron (MLP) / Linear layer to every single pixel coordinate independently.


### Key Use Cases

* **Changing Channel Dimensions (Scaling):** It is the primary tool for upscaling or downscaling the number of feature maps without altering spatial dimensions.
* **Linear Combinations:** It allows the network to learn complex interactions between different feature maps.
* **Depthwise Separable Convolution:** When chained right after a Depthwise Convolution, it completes the **Depthwise Separable Convolution** block (used heavily in MobileNet), mimicking a standard convolution at a fraction of the computational cost.

### Computational Efficiency

* **Standard Convolution ($D_K \times D_K$):** $D_K \times D_K \times M \times N$
* **Pointwise Convolution ($1 \times 1$):** $1 \times 1 \times M \times N = M \times N$

### Summary Checklist

* Kernel size is always $1 \times 1$
* Mixes information across channels, but has **zero** spatial awareness.
* Used to freely alter the number of channels ($M \rightarrow 1 \ \text{}{mostly}$).
* Functions as a computationally cheap, pixel-wise linear layer.

## Connections
* **Parent:** [[Convolution]]
* **Similar:** [[Depthwise Convolution]]