---
type: knowledge-note
created: 2026-04-19 01:51
tags:
  - Math_Optimization
aliases:
  - Lagrangian Form
---


## Summary

> [!abstract] 
> Lagrangian multipliers are a method for solving constrained optimization problems. Instead of solving ordinary objective function, we convert it into an unconstrained problem by using multiplier $\alpha$.  


### Core Formulation

#### Problem

Minimize:
$$
f(x)
$$

Subject to:
$$
g_i(x) = 0
$$

#### Langragian
$$
\mathcal{L}(x, \lambda) = f(x) + \sum_{i=1}^{m} \lambda_i g_i(x)
$$

#### Optimality condition

$$
\nabla_x \mathcal{L}(x, \lambda) = 0
$$

$$
g_i(x) = 0
$$

### Inequality Constraints

For constraints:
$$
g_i(x) \le 0
$$

Lagrangian:
$$
\mathcal{L}(x, \lambda) = f(x) + \sum_{i=1}^{m} \lambda_i g_i(x)
$$
$$\text{s.t.}\quad \alpha \ge 0$$

[[Karush-Kuhn-Tucker]] Conditions aim to test if 

- Stationarity : $\nabla_x \mathcal{L}(x, \lambda) = 0$

- Primal feasibility: $g_i(x) \le 0$

- Dual feasibility: $\lambda_i \ge 0$

- Complementary slackness : $\lambda_i g_i(x) = 0$

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]