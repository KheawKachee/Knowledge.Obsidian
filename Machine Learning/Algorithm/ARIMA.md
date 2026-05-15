---
type: knowledge-note
created: 2026-05-12 14:49
tags:
  - time_series
aliases: []
---


### Summary

> [!abstract] 
> ARIMA is a classic linear forecasting model using combination of AR, MA and differential.


## Components

- Auto-regressive : Past values -> predict current value.

- Integrated : Use differencing to reduce trend/seasonality.

- Moving average : Past prediction errors -> correct next prediction.

## Parameters
ARIMA(p, d, q)

- `p` = how many past values/differences used
- `d` = differencing setting
- `q` = how many past errors used

## Good For
- small data
- simple numeric series
- explainable baseline
- stable-ish pattern
- low compute

## Weakness
- mostly linear
- weak with nonlinear pattern
- weak with regime shift
- weak with many covariates
- not great for messy real-world event effects

## Practical Rules
- Use ARIMA as sanity baseline.
- If deep model cannot beat ARIMA, deep model likely unnecessary.



## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]