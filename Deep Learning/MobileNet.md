---
type: knowledge-note
created: 2026-05-17 16:38
tags:
aliases: []
references: https://arxiv.org/pdf/1704.04861
---


### Summary

> [!abstract] 
> The MobileNet architecture is a streamlined deep neural network designed for efficient mobile and embedded vision applications. Its primary innovation is the replacement of standard convolutional layers with **depthwise separable convolutions**, which significantly reduces computational cost and model size.

### Core Mechanism

*   **Depthwise Convolution:** Applies a single filter to each individual input channel to perform filtering.
*   **Pointwise Convolution:** A 1×1 convolution used to create a linear combination of the outputs from the depthwise layer, effectively combining the filtered features into a new representation.

The exact computational savings ratio of a Depthwise Separable Convolution compared to a Standard Convolution is calculated using this formula:

$$\frac{\text{Depthwise} + \text{Pointwise}}{\text{Standard}} = \frac{1}{N} + \frac{1}{D_K^2}$$

* $D_K$ is the kernel size (for MobileNet, this is usually $3$).
* $N$ is the number of output channels (which is typically large, e.g., $64, 128, 256$).

### Network Structure 

*   **Initial Layer:** The network begins with a single full convolutional layer.
*   **Layer Composition:** Most of the 28 layers in the network (counting depthwise and pointwise as separate) are depthwise separable filters. Each of these layers is followed by **Batch Normalization (BN)** and a **ReLU** non-linearity.
*   **Down-sampling:** This is handled via strided convolutions in the depthwise layers and the very first layer.
*   **Final Layers:** A final average pooling layer reduces the spatial resolution to 1, followed by a **fully connected (FC) layer** (with no non-linearity) and a **softmax** layer for classification.

### Efficiency and Implementation
MobileNet is optimized for speed beyond just reducing the number of operations:
*   **1×1 Convolutions:** Roughly **95% of the computation time** and 75% of the parameters are concentrated in the 1×1 pointwise convolutions.
*   **GEMM Optimization:** Unlike standard convolutions which often require a memory reordering called `im2col`, 1×1 convolutions can be implemented directly with highly optimized **General Matrix Multiply (GEMM)** functions.

### Model Scaling Hyper-parameters
To allow developers to trade off between latency, size, and accuracy for specific application constraints, MobileNet introduces two global hyper-parameters:
*   **Width Multiplier ($\alpha$):** Thins the network uniformly at each layer by reducing the number of input and output channels.
*   **Resolution Multiplier ($\rho$):** Reduces the input image resolution and the internal representation of every layer accordingly.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]