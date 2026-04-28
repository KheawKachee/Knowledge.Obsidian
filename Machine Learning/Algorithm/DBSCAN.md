---
type: knowledge-note
created: 2026-04-20 15:38
tags:
aliases: []
---


### Summary

> [!abstract] 
> **DBSCAN** (Density-Based Spatial Clustering of Applications with Noise) is an **unsupervised learning** algorithm categorized as a **density-based** method. Within the broader landscape of data clustering, it is distinguished by its ability to identify clusters of various shapes and handle data noise, which are significant limitations in other common algorithms like K-means.

### **Algorithm**

DBSCAN determines clusters by categorizing every data point based on two hyperparameters: a radius ($\epsilon$) and a minimum number of neighbors ($K$)

1.  **Core Points:** A point is a "core point" if it has at least $K$ neighbors within its $\epsilon$ radius.
2.  **Border Points:** These fall within the $\epsilon$ radius of a core point but do not have enough neighbors themselves to be considered core points.
3.  **Noise Points:** These are points that are neither core nor border points, typically representing outliers in low-density regions.

**The Clustering Process:**
1. The algorithm searches for a **core point** to initiate a new cluster.
2. Once found, all points within the $\epsilon$ distance of that core point and any subsequent core points connected to it are grouped into the same cluster.
3. This process repeats until all points are labeled. Points that cannot be reached from any core point are labeled as **noise**.



### *insert here*

## Connections
* **Parent:** [[Unsupervised Learning]][[Clustering]]
* **Similar:** [[ ]]