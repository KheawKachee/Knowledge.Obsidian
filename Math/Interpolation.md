---
type: knowledge-note
created:
tags:
  - numerical-methods
  - data-processing
  - time-series
aliases:
  - Resampling
---


### Summary

> [!abstract]
> Estimate unknown values between known data points. Used for resampling, missing-value filling, image resizing, and numerical approximation.


### Core Idea

Given known points:

$$
(x_0,y_0),(x_1,y_1),...,(x_n,y_n)
$$

Interpolation estimates:

$$
y=f(x)
$$

for new $x$ inside known range.

Interpolation inside range:

$$
x_{min} \le x \le x_{max}
$$

Extrapolation outside range:

$$
x < x_{min} \quad \text{or} \quad x > x_{max}
$$

Extrapolation is riskier.


### Why It Matters

Used in:

- time-series resampling
- missing-value imputation
- image resizing
- signal reconstruction
- numerical simulation
- sensor alignment
- grid conversion


### Main Methods

## 1. Nearest Neighbor Interpolation

Choose closest known value.

$$
f(x)=y_i
$$

where $x_i$ is nearest point.

Good:

- simple
- fast
- preserves original values
- useful for labels / categorical maps

Bad:

- blocky
- discontinuous
- poor for smooth signals


## 2. Linear Interpolation

Connect two nearest points with straight line.

For $x_0 \le x \le x_1$:

$$
f(x)=y_0+\frac{x-x_0}{x_1-x_0}(y_1-y_0)
$$

Good:

- simple
- stable
- interpretable
- good baseline

Bad:

- not smooth at data points
- weak for curved patterns


## 3. Polynomial Interpolation

Fit one polynomial through all points.

$$
p(x)=a_0+a_1x+a_2x^2+...+a_nx^n
$$

Good:

- exact through points
- mathematically clean

Bad:

- unstable for many points
- can oscillate strongly
- sensitive to noise

Main risk:

- Runge phenomenon


## 4. Spline Interpolation

Fit piecewise polynomials between points.

Most common:

- linear spline
- quadratic spline
- cubic spline

Cubic spline uses cubic polynomial per interval.

Good:

- smooth
- flexible
- less unstable than global polynomial
- good for continuous curves

Bad:

- can overshoot
- not always shape-preserving
- boundary behavior matters


## 5. Cubic Interpolation

Uses nearby points to estimate smooth curve.

Common in:

- image resizing
- signal processing
- smooth numerical data

Good:

- smoother than linear
- often visually better

Bad:

- more compute
- may overshoot
- can create fake smoothness


## 6. Sinc Interpolation

Ideal reconstruction for band-limited signals.

$$
x(t)=\sum_{n=-\infty}^{\infty}x[n]\text{sinc}\left(\frac{t-nT}{T}\right)
$$

Good:

- theoretically ideal for band-limited signals
- strong signal-processing foundation

Bad:

- infinite support
- expensive
- assumes perfect band-limited signal
- sensitive to practical truncation


## 7. Forward Fill

Use previous known value.

Common in time-series.

Good:

- simple
- preserves step-like behavior
- useful for state variables

Bad:

- bad for smoothly changing values
- can hide missing-data problems


## 8. Backward Fill

Use next known value.

Good:

- simple
- useful when future value logically applies backward

Bad:

- leaks future information in forecasting
- dangerous for ML validation


### Method Choice

| Method | Best For | Main Risk |
|---|---|---|
| Nearest | labels, categorical grids | blocky output |
| Linear | simple numeric data | not smooth |
| Polynomial | small clean datasets | oscillation |
| Spline | smooth curves | overshoot |
| Cubic | images, smooth signals | fake smoothness |
| Sinc | band-limited signals | unrealistic assumption |
| Forward fill | step-like time-series | stale values |
| Backward fill | reverse filling | future leakage |


### Interpolation vs Imputation

Interpolation:

- estimates between known ordered points---
type: knowledge-note
created: 2026-05-12 14:59
tags:
aliases: []
---


￼### Summary

> [!abstract] 
> 


￼### *insert here*

￼## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]
- assumes meaningful order
- common in time / space data

Imputation:

- fills missing values generally
- may use statistical / ML methods
- does not always require order


### Common Mistakes

- Using interpolation when missingness is not random.
- Using backward fill before train/test split.
- Interpolating labels as if numeric.
- Extrapolating and trusting result.
- Creating fake precision from sparse data.
- Ignoring domain constraints.


### Practical Rule

Use boring baseline first:

1. nearest for categorical data
2. linear for numeric continuous data
3. cubic/spline only if smoothness assumption is justified
4. forward fill only for state-like time-series
5. avoid extrapolation unless domain model supports it


### Related Concepts

- [[Time Series]]
- [[Resampling]]
- [[Missing Data]]
- [[Signal Reconstruction]]
- [[Spline]]
- [[Sampling Rate]]


## Connections
* **Parent:** [[Numerical Methods]]
* **Similar:** [[Imputation]], [[Resampling]], [[Regression]]