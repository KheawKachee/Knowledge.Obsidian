---
type: knowledge-note
created: 2026-05-17 16:48
tags:
  - CNN
  - math
aliases:
  - math
---


### Summary

> [!abstract] 
> Depthwise Convolution contrast to standard convolutions by perform spatial convolution on each channel independently instead of a single filter slides across all input channels simultaneously.

### Methodology

1. **Channel Separation:** The input tensor of shape $H \times W \times C$ is split into $C$ individual channels, each of shape $H \times W \times 1$.
2. **Independent Filtering:** A unique 2D kernel (e.g., $3 \times 3 \times 1$) is applied to *only* its corresponding channel.
3. **Stacking:** The resulting $C$ output channels are stacked back together to form the final output of shape $H' \times W' \times C$.

>  **Important Limitation:** Unlike a standard convolution, depthwise convolution **cannot increase or decrease the number of channels** on its own. The input channel count always equals the output channel count. To mix channels later, it is almost always paired with a **Pointwise Convolution** ($1 \times 1$) to form a **Depthwise Separable Convolution**.

### Efficiency

Because filters don't look across multiple channels simultaneously, the parameter count and computational cost drop drastically.

#### Parameter Comparison

Let $D_K$ be the kernel size, $M$ be the input channels, and $N$ be the output channels.

* **Standard Convolution:** $D_K \times D_K \times M \times N$
* **Depthwise Convolution:** $D_K \times D_K \times M$

### Summary Checklist

* Filters are strictly 2D per channel.
* No cross-channel communication.
* Number of input channels = Number of output channels.
* Drastically reduces FLOPs and parameter counts for mobile/edge deployment.

## Connections
* **Parent:** [[Convolution]]
* **Similar:** [[ ]]