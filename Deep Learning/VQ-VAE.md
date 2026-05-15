---
type: knowledge-note
created: 2026-05-11 22:18
tags:
  - CNN
aliases: []
---
### Summary

> [!abstract] 
> VQ-VAE is a VAE-style autoencoder that learns discrete latent representations by mapping continuous encoder outputs to the nearest vectors in a learnable codebook.


### Components

1. Encoder : a CNN that maps an input image into continuous latent vectors.$$z_e(x) = \text{Encoder}(x)$$

2. Codebook : a learnable table of discrete latent embeddings that maps continuous encoder outputs to the nearest codebook vector.$$E = \{e_1, e_2, \dots, e_K\}, \quad e_i \in \mathbb{R}^D$$ $$z_q(x) = e_k, \quad \text{where } k = \arg\min_j \|z_e(x) - e_j\|_2$$
3. Decoder : a CNN that maps the picture in [[Latent Space]] back into pixel-wise form
### Loss Function

Since $\arg\min$ is non-differentiable, VQ-VAE uses the [[Straight-Through Estimator]] so gradients from the decoder pass through $z_q$ as if it were $z_e$.

$$\mathcal{L} = \log p(x|z_q(x)) + \| \text{sg}[z_e(x)] - e \|_2^2 + \beta \| z_e(x) - \text{sg}[e] \|_2^2$$

1. **Reconstruction Loss** ($\log p(x|z_q(x))$): encourages the whole VQ-VAE to reconstruct images more similar to the original images 
2. **Codebook Loss** ($\| \text{sg}[z_e(x)] - e \|_2^2$): updates the Codebook to be similar to the Encoder output and uses $\text{sg}$ (Stop Gradient) to prevent gradient update in the Encoder
3. **Commitment Loss** ($\beta \| z_e(x) - \text{sg}[e] \|_2^2$): updates the Encoder to be similar to known latent vectors in the Codebook. Uses $\text{sg}$ to prevent gradient update in the Codebook

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]