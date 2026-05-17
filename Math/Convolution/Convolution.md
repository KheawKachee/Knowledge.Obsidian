---
type: knowledge-note
created:
tags:
  - math
  - CNN
aliases:
  - Conv
---


### Summary

> [!abstract]
> Operation that combines two functions/signals by sliding one over the other. Measures local overlap. Used for filtering, feature extraction, smoothing, and CNNs.


### Core Idea

Continuous convolution:

$$
(f*g)(t)=\int_{-\infty}^{\infty}f(\tau)g(t-\tau)d\tau
$$

Discrete convolution:

$$
y[n]=\sum_{k=-\infty}^{\infty}x[k]h[n-k]
$$

Where:

- $x$ = input signal
- $h$ = kernel / filter
- $y$ = output signal


### Intuition

Convolution = sliding weighted sum.

At each position:

1. place kernel over signal
2. multiply overlapping values
3. sum result
4. move kernel


### In Signal Processing

Kernel controls effect.

Examples:

- smoothing kernel -> blur / denoise
- derivative kernel -> edge detection
- low-pass filter -> remove high-frequency noise
- high-pass filter -> emphasize sharp changes


### In Image Processing

2D convolution:

$$
Y[i,j]=\sum_m\sum_n X[i-m,j-n]K[m,n]
$$

Used for:

- blur
- sharpen
- edge detection
- feature extraction


### In CNNs

CNN convolution learns kernels from data.

Kernel becomes feature detector.

Early layers often learn:

- edges
- corners
- textures

Deeper layers learn:

- object parts
- shapes
- semantic features


### Convolution Theorem

Convolution in time domain equals multiplication in frequency domain.

$$
f*g \leftrightarrow F(\omega)G(\omega)
$$

This enables fast convolution using FFT:

1. FFT input
2. FFT kernel
3. multiply in frequency domain
4. inverse FFT


### Cross-Correlation vs Convolution

True convolution flips kernel.

Cross-correlation does not flip kernel.

Deep learning libraries usually implement cross-correlation but call it convolution.

For learned kernels, difference usually not important.


### Important Parameters in CNNs

* **Kernel Size**
	* Controls the local receptive field.
	* *Examples:* $3 \times 3$, $5 \times 5$, $7 \times 7$

* **Stride**
	* The step size of the kernel's movement across the input.
	* A larger stride results in a smaller output spatial size.

* **Padding**
	* Adds border values around the input matrix.
	* Used to precisely control the output size.
	* *Common types:*
	* **Valid:** No padding applied.
	* **Same:** Pads the input to preserve the original spatial size.

* **Dilation**
	* Adds gaps inside the kernel itself.
	* Increases the receptive field without increasing the actual parameter count.

### Common Mistakes

- Thinking convolution always means deep learning.
- Forgetting kernel flip in mathematical convolution.
- Ignoring padding effects near borders.
- Confusing convolution with matrix multiplication, though implementation may use matrix multiplication.
- Assuming larger kernel always better.


### Related Concepts

- [[Fourier Transform]]
- [[FFT]]
- [[Image Filtering]]
- [[CNN]]
- [[Kernel]]
- [[Linear Time-Invariant System]]


## Connections
* **Parent:** [[Signal Processing]]
* **Similar:** [[Correlation]], [[Filtering]], [[CNN]]