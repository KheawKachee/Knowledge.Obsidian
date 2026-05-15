---
type: knowledge-note
created: 2026-05-12 14:46
tags:
aliases: []
---


### Summary

> [!abstract] 
> 

## Stable Properties
- mean stable
- variance stable
- autocovariance stable

## Non-Stationary
Non-stationary = these properties change over time.

Common cases:
- trend changes mean
- volatility changes variance
- lag relationship changes
- regime shift breaks old pattern

## Why It Matters
Many classic models assume stable structure.

If data shifts, model trained on past may fail future.

## DS Rule
Plot first.

If mean/variance visibly changes -> treat as non-stationary.

## Fix Options
- differencing
- detrending
- log transform
- rolling normalization
- train on recent window
- use model robust to drift

## Failure Mode
Forcing stationary assumption on unstable data -> fake confidence.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]