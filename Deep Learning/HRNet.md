---
type: knowledge-note
created: 2026-05-23 14:56
tags:
aliases: []
references:
---


### Summary

> [!abstract] 
> HRNet (High-Resolution Network) is a powerful convolutional neural network architecture specifically designed for spatially sensitive computer vision tasks like human pose estimation, semantic segmentation, and object detection.

Traditional backbones (like ResNet or VGG) process images by sequentially downsampling them into low-resolution, high-channel feature maps before attempting to upsample them back to the original size. HRNet flips this paradigm completely by **maintaining a high-resolution representation throughout the entire depth of the network**.

### Architecture

Instead of treating high-to-low and low-to-high resolution tracking as a serial process, HRNet connects them in parallel.

#### Parallel High-to-Low Resolution Substreams

The network starts with a high-resolution stream ($1\times$ scale). As it goes deeper, it gradually adds lower-resolution streams in parallel (e.g., $2\times$ downsampled, $4\times$ downsampled), rather than replacing the high-resolution stream. This allows the network to simultaneously focus on sharp, precise localized pixels *and* rich, semantic global context.

#### Repeated Multi-Resolution Fusions (Cross-Talk)

This is where the magic happens. The parallel streams do not run in isolation; they constantly talk to each other through **fusion modules**.

* **High-to-Low Fusion:** High-resolution features pass through stride convolutions to match the lower-resolution scale.
* **Low-to-High Fusion:** Low-resolution features are upsampled using bilinear upsampling combined with $1 \times 1$ convolutions to align channels.
* Because these representations are fused repeatedly, every resolution scale continuously benefits from the information learned by the others.
 
## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]