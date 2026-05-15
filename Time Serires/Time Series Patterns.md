---
type: knowledge-note
created: 2026-05-12 14:48
tags:
aliases: []
---


### Summary

> [!abstract] 
> Patten occured in time series data.

## Trend
Long-term direction.

Example:
- demand rising
- price slowly falling
- user count increasing

## Seasonality
Repeating pattern at fixed interval.

Example:
- daily traffic peak
- weekly sales cycle
- monthly bill cycle

## Holiday Effect
Calendar-specific anomaly.

Example:
- New Year spike
- Songkran drop
- promotion-day surge

## Cycle
Long repeated behavior with irregular interval.

Example:
- economy boom/crash/recovery
- product hype cycle

## DS Rule
Separate these mentally:

Signal = trend + seasonality + event effect + noise.

## Practical Features
Useful engineered features:
- lag values
- rolling mean
- rolling std
- day of week
- month
- holiday flag
- promotion flag

## Failure Mode
Model sees holiday spike once -> assumes normal pattern.

### *insert here*

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]