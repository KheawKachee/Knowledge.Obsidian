---
type: knowledge-note
created:
tags:
  - signal-processing
  - algorithm
  - frequency-domain
aliases:
  - Fast Fourier Transform
---


### Summary

> [!abstract]
> Efficient algorithm for computing the Discrete Fourier Transform. Same result as DFT, much faster.


### Core Idea

FFT is not a different transform.

FFT = fast algorithm for DFT.

DFT:

$$
X_k=\sum_{n=0}^{N-1}x_n e^{-j2\pi kn/N}
$$

Inverse DFT:

$$
x_n=\frac{1}{N}\sum_{k=0}^{N-1}X_k e^{j2\pi kn/N}
$$


### Why FFT Exists

Naive DFT cost:

$$
O(N^2)
$$

FFT cost:

$$
O(N\log N)
$$

Huge speedup for large signals.


### Intuition

FFT exploits symmetry and periodicity in complex exponentials.

Instead of computing every frequency independently, it reuses repeated structure.

Classic Cooley-Tukey FFT splits signal into:

- even-indexed samples
- odd-indexed samples

Then recursively combines smaller DFTs.


### Use Cases

Used when data is discrete:

- digital audio
- time-series
- images
- sensor data
- numerical simulation
- convolution acceleration


### FFT Output

For input signal length $N$:

$$
x_0, x_1, ..., x_{N-1}
$$

FFT returns $N$ frequency bins:

$$
X_0, X_1, ..., X_{N-1}
$$

Bin meaning depends on sampling rate.

Frequency resolution:

$$
\Delta f = \frac{f_s}{N}
$$

Where:

- $f_s$ = sampling rate
- $N$ = number of samples


### Nyquist Limit

Highest meaningful frequency:

$$
f_{max} = \frac{f_s}{2}
$$

If signal contains frequency above Nyquist, aliasing can happen.


### Practical Notes

Before FFT, usually consider:

- remove mean
- detrend signal
- apply window function
- choose suitable sample length
- check sampling rate
- inspect magnitude spectrum


### Windowing

FFT assumes finite signal segment repeats periodically.

If segment edges do not match, spectral leakage occurs.

Window functions reduce leakage.

Common windows:

- Hann
- Hamming
- Blackman
- Rectangular


### Common Mistakes

- Confusing FFT with Fourier Transform itself.
- Ignoring sampling rate.
- Reading bin index as frequency directly.
- Forgetting Nyquist limit.
- Ignoring spectral leakage.
- Using FFT on non-stationary signal without caution.


### Related Concepts

- [[Fourier Transform]]
- [[Discrete Fourier Transform]]
- [[Convolution]]
- [[Spectral Leakage]]
- [[Nyquist Frequency]]
- [[Window Function]]


## Connections
* **Parent:** [[Fourier Transform]]
* **Similar:** [[Discrete Fourier Transform]], [[Spectral Analysis]]