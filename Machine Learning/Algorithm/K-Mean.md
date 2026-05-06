---
type: knowledge-note
created: 2026-04-20 15:21
tags:
aliases:
  - K-Means
---


### Summary

> [!abstract] 
> The core objective of K-Mean is to partition data into $k$ sets ($C_{1} \dots C_{k}$) by minimizing the distance between data points and their respective group centers. Unlike the "original" clustering problem formulation that requires computing distances between every pair of points in a cluster—which is computationally inefficient for large datasets—K-Mean simplifies this by using centroids.

### Mechanism

The training process for K-Mean Clustering follows a specific sequence of steps until it reaches a stable state:

1.  **Initialization:** The user must first predefine the number of clusters ($K$). The algorithm then **randomly assigns** a cluster label from 1 to $K$ to every data point in the training set.
2.  **Centroid Calculation:** For each assigned cluster, the algorithm computes a **centroid** ($\bar{x}_k$), which is the average of the features of all data points within that cluster.
3.  **Assignment:** Each data point is reassigned to the cluster whose centroid is the **closest** based on a distance function, typically **Euclidean distance**.
4.  **Convergence:** Steps 2 and 3 repeat until the cluster assignments stop changing or the centroid locations become unchanged.

Once training is complete, a new input feature is allocated to a cluster by simply identifying which of the trained centroids is nearest to it.

```python
import numpy as np

def k_means(data, k, max_iterations=100):
    """
    K-Means Clustering implementation for Obsidian notes.
    """
    # 1. Randomly initialize centroids from the data points
    n_samples = data.shape[0] # Shape (n,d)
    random_indices = np.random.choice(n_samples, k, replace=False) 
    
    centroids = data[random_indices] 
    
    for _ in range(max_iterations):
        # 2. Assign clusters based on Euclidean distance
        # We calculate the distance from each point to each centroid
        distances = np.linalg.norm(data[:, np.newaxis] - centroids, axis=2) # Shape (n,k,d) -> (n,k)
        cluster_labels = np.argmin(distances, axis=1)
        
        # 3. Update centroids
        new_centroids = np.array([
            data[cluster_labels == i].mean(axis=0) 
            if len(data[cluster_labels == i]) > 0 else centroids[i]
            for i in range(k)
        ])
        
        # Check for convergence (if centroids didn't move)
        if np.all(centroids == new_centroids):
            break
            
        centroids = new_centroids
        
    return centroids, cluster_labels
```

### Hyperparameters

- Number of clusters ($k$)
- The distance function (usually euclidian)
- Centriod Calculation function (usually mean)

### **Limitations**

When compared to other algorithms, the K-Mean process is distinguished by several factors:

* The K-Mean process involves a **hard decision**, where each point is ==strictly== assigned to one cluster. In contrast, the **[[Gaussian Mixture Model]] (GMM)** uses a "soft decision" process, assigning points based on the **probability** ($\tau_{jk}$) that they belong to various clusters.
* K-Mean process requires $K$ in advanced. Other processes, like **[[Hierarchical Clustering]]**, allow the user to decide the number of clusters later. Similarly, **[[DBSCAN]]** identifies clusters based on density without needing a predefined $K$.
* Reliance on Euclidean distance, which causes it to favor circular or spherical cluster shapes and unfavour to dense data or overlapping data.
* K-Mean process has no mechanism to handle outliers and will force every point into a cluster unlike [[DBSCAN]].

## Connections
* **Parent:** [[Unsupervised Learning]][[Clustering]]
* **Similar:** [[Hierarchical Clustering]]