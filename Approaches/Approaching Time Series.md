---
type: knowledge-note
created: 2026-05-11 14:26
tags:
  - approach
aliases: []
---

### **Handling Temporal Data**

* **Non-IID Samples:** Temporal data is not IID. Consequently, traditional random splits must be avoided in favor of temporal splitting to maintain the integrity of the time sequence and prevent data leakage.
* **Multi-Temporal Architecture:** This approach utilizes multiple **lookback windows**, enabling the model to capture complex relationships across different time resolutions (e.g., hourly, daily, and weekly patterns simultaneously).
* **Multi-Horizon Forecasting:** A technique designed to address multi-temporal challenges by utilizing features across various time steps. This method is frequently applied in **Deep Learning** architectures to exploit intricate, interconnected patterns over long sequences.
* **Multi-Output Prediction:** An alternative strategy typically used when ensembling **classical Machine Learning** (often tree-based models). Instead of a recursive approach, the model is designed to predict multiple future time steps simultaneously or through dedicated regressors for each step.

### **Policy & Evaluation**

* **Metric Policy:** Choosing between **MAE, MSE, or MAPE** defines your actual business or operational policy (e.g., how much you penalize large outliers).

### Feature Engineering Technique

*   **Lag Features:** These represent past values of the target variable (e.g., $Hs_{t-1}$ for wave height or sales from previous weeks/months) to teach the model about immediate historical context.
*   **Rolling Statistics:** To smooth out daily fluctuations and capture statistical patterns, practitioners generate **rolling means, standard deviations, maximums, and minimums** over various time windows (such as 7, 30, 90, or 180 days).
*   **Exponential Smoothing (ES):** This is sometimes used as a pre-processing step to provide a smoothed representation of noisy demand values before they are passed to a primary model like LightGBM.

In retail contexts, pricing is a major driver of demand and requires extensive engineering.

*   **Extreme and Central Metrics** including maximum prices at store or daily levels, overall minimum/maximum prices across all locations, and the mean and standard deviation of prices to capture distribution and volatility.
*   **Price Normalization**
*   **Price Momentum or Price Shift**

External factors and cyclical patterns significantly impact retail sales and are incorporated through specific markers.

*   **Seasonality Indicators:** Raw timestamps are decomposed into features like **day of the week, week of the year, month, quarter, and year**. Binary flags for the **start or end of a month** also capture periodic shopping spikes.
*   **Season Classification:** Months are often grouped into distinct seasons (e.g., Spring, Summer, Autumn, Winter) to address quarterly demand variations.
*   **Event Counters:** These track the number of days until, into, and after an event such as a holiday or promotion. For weekly data, engineers may calculate the number of occurrences of specific event types per week.
*   **Promotion Markers:** Features include binary indicators or weekly counts for programs like **SNAP benefits**, which signal periods of increased purchasing power.


Because many machine learning models require numerical input, categorical variables must be transformed.

*   **Label Encoding**
*   **[[Target Encoding]]** 
*   **One-Hot Encoding**

### Data Preprocessing and Cleaning

- Outlier Detection
- Target Transformation such as log-transform
- Clipping
- EDA including correlation analysis 
- Memory Optimization such as int64 to int16 to reduce the memory footprint during training.
- Autocorrelation Analysis Techniques to identify the most significant lag values that capture relevant historical patterns.

---
### **Causality & Model Sustainability**

* **Correlation $\neq$ Causation:** Never equate correlation with causation without a proven direct link.
* **Granger Causality:** A "predictive" causality checking if $X$ precedes $Y$. If $Y$ precedes $X$, $X$ cannot be the cause.
* **Logic:** If adding past $X$ to past $Y$ significantly improves the prediction of $Y_t$, then $X$ Granger-causes $Y$.
* **Stationarity:** Data must be stable (constant mean/variance); use **Differencing** if trends exist.
* **Time Lag:** The lookback period ($p$) must be optimized to capture the delayed impact.


* **The "Weak Feature" Rule:** Features with weak Granger causality often hide latent variables. Avoid these "noisy" features to ensure long-term model stability in production.
* **Proving Causation:**
* **RCT / A/B Testing:** The gold standard; uses random allocation to isolate impact.
* **Natural Experiments:** Exploits "accidental" environmental shifts when RCTs are unethical or impossible.
* **DAGs (Directed Acyclic Graphs):** Visual maps used to distinguish direct causes from shared "confounder" variables.


### **Vector Autoregression (VAR)**

VAR is a stochastic process model used to capture the linear interdependencies among multiple time series.

#### **Mathematical Framework**

In a **VAR(1)** system with two variables:


$$X_t = a_1X_{t-1} + a_2Y_{t-1} + e_{x,t}$$

$$Y_t = b_1Y_{t-1} + b_2X_{t-1} + e_{y,t}$$

For a general **VAR(p)** model:


$$Z_t = A_1Z_{t-1} + A_2Z_{t-2} + \dots + A_pZ_{t-p} + e_t$$

* $Z_t$: Vector of all variables at time $t$.
* $p$: Number of lags.
* $A_i$: Coefficient matrices.

#### **Link to Granger Causality**

VAR provides the foundation for Granger tests. If the coefficients for past $X$ in the $Y_t$ equation are statistically significant (while accounting for past $Y$), then **$X$ Granger-causes $Y$**.

#### **Key Assumptions & Constraints**

* **Stationarity:** Requires mean-reverting data to avoid spurious results.
* **Lag Selection:** Choosing $p$ is critical (often via AIC/BIC).
* **Linearity:** Assumes relationships between variables are linear.
* **Confounding:** Results can be misled by omitted "hidden" variables.

---
### Tools

- LGTD Paradigm Shift https://arxiv.org/html/2601.04820v1
- mFLICA

---



