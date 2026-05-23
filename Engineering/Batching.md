---
type: knowledge-note
created: 2026-05-18 12:04
tags:
aliases: []
references:
---

### Summary

> [!abstract]
> Maximizing GPU throughput requires balancing resource utilization with strict latency bounds. While standard batching works well for static, offline workloads, production services rely on dynamic batching and continuous batching to efficiently handle concurrent, unpredictable real-time traffic.

### Standard Batching

Standard (or static) batching groups a fixed number of inference inputs together into a single tensor before executing the forward pass.

* **How it works:** The execution thread blocks until a predetermined number of requests (e.g., $N = 32$ or $64$) are accumulated in the queue.
* **Why it matters:** It achieves maximal GPU compute efficiency and memory bandwidth utilization by executing identical operations in parallel across the batch.
* **The Drawback:** It introduces severe latency penalties under low-traffic conditions, as early requests must wait indefinitely in the queue until the batch size threshold is met.

### Dynamic Batching

Instead of waiting for a fixed batch size, the inference engine uses a time-threshold window to opportunistically group incoming requests.

* **How it works:** The engine collects incoming requests until *either* the maximum batch size is reached OR a maximum timeout window (e.g., 5ms) expires.
* **Why it matters:** This bounds worst-case latency during low-traffic periods while still exploiting GPU parallelism during peak traffic spikes.

### Continuous Batching (Iteration-Level Scheduling)

For generative models (like LLMs) where output lengths vary wildly, traditional request-level batching suffers from the "farthest-behind" characteristic—the entire batch is held up until the longest sequence finishes generation.

* **How it works:** Instead of waiting for the entire batch to complete, scheduling happens at the iteration (token) level. Completed requests are dropped from the batch immediately, and new pending requests are inserted into the running batch at the next token-generation step.
* **Why it matters:** It drastically reduces time-to-first-token (TTFT) and eliminates GPU underutilization caused by idle slots ("bubble" time) waiting for long sequences to finish.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]