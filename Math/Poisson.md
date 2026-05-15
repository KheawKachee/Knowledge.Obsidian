---
type: knowledge-note
created: 2026-05-15 16:44
tags:
aliases: []
---


### Summary

> [!abstract] 
> The Poisson distribution is a discrete probability distribution that expresses the probability of a given number of events occurring in a fixed interval of time or space. It is used when you are counting occurrences of "rare" events that happen independently and at a constant average rate.

### **Formulation**

The probability of observing exactly $k$ events in an interval is:

$$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$$

Where:

* $\lambda$ = The average number of events (Mean and Variance are both $\lambda$).
* $e$ = Euler's number ($\approx 2.718$).
* $k$ = The number of occurrences ($0, 1, 2, \dots$).
* $k!$ = $k$ factorial.


### Poisson Regression in Machine Learning

In your work with XGBoost or LightGBM, you might encounter the **Poisson Objective**. This is used when your target variable is a **count** (non-negative integers).

| Objective | Typical Use Case |
| --- | --- |
| **Regression (MSE)** | Predicting continuous values (e.g., house prices). |
| **Poisson Regression** | Predicting counts (e.g., number of clicks, hospital visits, or customer arrivals). |

**Why not just use standard Regression?**
Standard regression assumes a normal distribution and can predict negative numbers. Poisson regression ensures predictions are always positive and better handles data that is "skewed" toward zero (lots of small counts, few large ones).

### Poisson vs. Binomial**

A helpful way to remember it:

* **Binomial:** You have $n$ trials and want to know how many "successes" occur (e.g., flipping a coin 10 times).
* **Poisson:** There is no fixed "number of trials," only a continuous flow of time/space where events happen (e.g., waiting for emails to arrive).

> **Pro Tip:** As $n$ becomes very large and $p$ (probability) becomes very small, the Binomial distribution converges to the Poisson distribution.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]