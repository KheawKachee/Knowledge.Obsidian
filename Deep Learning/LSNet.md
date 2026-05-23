---
type: knowledge-note
created: 2026-05-23 14:39
tags:
aliases: []
references: https://cvpr.thecvf.com/virtual/2025/poster/34284#:~:text=To%20tackle%20this%20issue%2C%20researchers,and%20convolutions%20for%20token%20mixing.
---


### Summary

> [!abstract] 
> Most lightweight models rely heavily on either standard depthwise convolutions or scaled-down self-attention mechanisms for token mixing (spatial information exchange). However, these approaches often force a compromise between broad contextual awareness and processing speed. LSNet breaks this bottleneck by imitating the dual-scale nature of the human eye through its signature "See Large, Focus Small" architecture strategy.

 
### Core Concept

The core innovation of LSNet is the **Large-Small (LS) Convolution**, a token-mixing block designed to separate spatial relationship modeling into two distinct, highly optimized phases:

```
1. [Input Feature Map]
2. Large-Kernel Static Conv 
3. Small-Kernel Dynamic Conv
4. [Output] 
```

#### Large-Kernel Perception

Mimicking human peripheral vision, this step captures wide spatial context across an expanded neighborhood.

* It uses a **large-kernel static depthwise convolution** to map long-range spatial dependencies.
* Because it is static and depthwise, it remains computationally cheap while providing the model with a global-like field of view.

#### Small-Kernel Aggregation 

Mimicking the human fovea (the center of the retina used for sharp, high-detail focus), this step zeroes in on local fine features.

* Backed by the broad context from Stage 1, it employs a **small-kernel dynamic convolution** to adaptively fuse local visual features.
* It utilizes a **group mechanism** that restricts the scope of aggregation to a precise, localized region, drastically lowering FLOPs (Floating Point Operations) while retaining intricate textural details.
 
### Acrhitecture

LSNet integrates the LS Convolution into a standard, robust 4-stage hierarchical structure similar to other modern lightweight backbones (like FastViT or RepViT):

* **Input Stem:** An early convolutional downsampling stem reduces the initial image spatial dimensions quickly to conserve compute power.
* **4-Stage Hierarchy:** The model processes features across 4 sequential stages, progressively reducing spatial resolution while doubling the channel capacity.
* **The LS Block:** Each stage consists of stacked LS Blocks, where token mixing is performed entirely by the LS Convolution, completely replacing expensive Multi-Head Self-Attention (MHSA) modules without losing global context.
 
## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]