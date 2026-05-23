---
type: knowledge-note
created: 2026-05-23 14:34
tags:
aliases: []
references:
---


### Summary

> [!abstract] 
> RepViT starts from [[MobileNet]]V3-Large, then modernizes it using efficient ViT design ideas, but keeps it as a pure CNN. The paper says it separates token mixer and channel mixer, uses a ViT-like MetaFormer structure, and applies structural re-parameterization to reduce inference cost.


### Architecture

#### MetaFormer Block Structure

Vision Transformers separate information processing into two distinct parts: *Token Mixing* (spatial/global communication) and *Channel Mixing* (feature modification). RepViT restructures the MobileNet block to strictly follow this MetaFormer layout:

* **Token Mixer:** Utilizes structural reparameterization with **$3 \times 3$ Depthwise Convolutions**. During training, it uses a multi-branch topology (overcoming optimization hurdles); during inference, these fold back into a single, lightning-fast $3 \times 3$ layer.
* **Channel Mixer (Feed-Forward Network):** Employs consecutive $1 \times 1$ convolutions to mix channels, strictly separated from the spatial token mixing step.

#### Reducing the Expansion Ratio & Increasing Width

Traditional ViTs expand channel dimensions inside their Feed-Forward Networks (FFN) by a factor of 4, while MobileNetV3 expands by up to 6. This is incredibly memory-intensive for mobile devices.

* RepViT slashes this expansion ratio down to **2**.
* To compensate for the loss of representation power, it increases the overall **base width (number of channels)** of the network. This trade-off maintains high accuracy while drastically dropping latency.

#### Stem and Downsampling

Instead of dividing images into non-overlapping patches (like native ViTs), RepViT uses an **Early Convolution Stem** consisting of two stride-2 convolutions. This downsamples the input by a factor of 4 early on, saving massive amounts of compute.

Furthermore, instead of relying on basic downsampling layers later in the stages, it implements optimized **deeper downsampling layers** using stride-2 depthwise separable convolutions to safely modify resolutions and channel dimensions.

#### FC Layer

Many mobile models use heavy pooling and dense layers right at the end of the network. RepViT strips this down to a highly streamlined classifier consisting solely of a **Global Average Pooling** layer followed by a single **Linear Layer**, slashing final-stage latency to near zero.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]