---
type: knowledge-note
created: <% tp.date.now("YYYY-MM-DD HH:mm") %>
tags:
  - signal-processing
  - math
  - frequency-domain
aliases:
  - Fourier Transform
  - FT
  - Continuous Fourier Transform
---


### Summary

> [!abstract]
> Transform signal from time / space domain into frequency domain. Shows what frequencies exist and how strong each frequency is.


### Core Idea

Fourier Transform decomposes a signal into weighted sinusoids.

Time domain:

$$x(t)$$

Frequency domain:

$$X(f)$$

Continuous Fourier Transform:

$$
X(f)=\int_{-\infty}^{\infty}x(t)e^{-j2\pi ft}dt
$$

Inverse Fourier Transform:

$$
x(t)=\int_{-\infty}^{\infty}X(f)e^{j2\pi ft}df
$$


### Intuition

Signal = mixture of waves.

Fourier Transform asks:

> “How much of each frequency exists inside this signal?”

Example:

- low frequency -> slow trend
- high frequency -> fast change / edge / noise
- strong magnitude -> important frequency
- phase -> timing / alignment


### Output

Fourier output is complex:

$$
X(f)=a+jb
$$

Magnitude:

$$
|X(f)|
$$

Phase:

$$
\angle X(f)
$$

Meaning:

- magnitude -> strength of frequency
- phase -> shift of frequency component


### Why It Matters

Used in:

- signal processing
- image processing
- audio analysis
- time-series analysis
- filtering
- compression
- convolution acceleration
- spectral analysis


### Common Uses

#### Frequency Analysis

Detect dominant cycles.

Example:

- daily seasonality
- weekly seasonality
- vibration frequency
- audio pitch


#### Filtering

Remove unwanted frequency.

Examples:

- low-pass filter -> remove high-frequency noise
- high-pass filter -> remove slow trend
- band-pass filter -> keep target frequency range


#### Image Processing

In images:

- low frequency -> smooth shapes / lighting
- high frequency -> edges / texture / noise


### Important Assumptions

Fourier Transform assumes signal can be represented by sinusoids.

Works best when:

- signal is stationary enough
- frequency content is meaningful
- global frequency view is useful

Weak when:

- signal changes behavior over time
- local timing matters
- non-stationary signal dominates


### Common Mistakes

- Magnitude alone loses phase info.
- Frequency domain does not directly show when event happened.
- Strong high frequency can mean edge, noise, or sharp transition.
- Sampling rate limits detectable frequency.


### Related Concepts

- [[FFT]]
- [[Convolution]]
- [[Frequency Domain]]
- [[Signal Processing]]
- [[Time Series]]
- [[Spectral Analysis]]


## Connections
* **Parent:** [[Signal Processing]]
* **Similar:** [[FFT]], [[Convolution]], [[Wavelet Transform]]