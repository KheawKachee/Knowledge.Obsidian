---
type: knowledge-note
created: 2026-04-20 15:38
tags:
aliases: []
---

### Summary
>[!note]
>Agglomerative Hierarchical Clustering starts by treating each data point as its own cluster and iteratively merges the closest clusters until only one cluster remains. The process is visualized using a **dendrogram**, where the height represents the distance (or dissimilarity) at which clusters are merged.

### Algorithm

#### Initialization
- Given **m training samples**, assign each sample to its own cluster  
  → Total clusters = **m**
- Compute pairwise distances between all clusters  
  → Number of distance pairs $\binom{k}{2}$

#### Build Dendrogram

For number of clusters = **m, m−1, ..., 2**

1. **Compute distances** : Measure distances between all current clusters
2. **Merge clusters** : Fuse the closest pair of clusters  (e.g., using **single linkage**)
3. **Record height** : Store the distance at which clusters merge. This becomes the **height in the dendrogram**
4. **Update clusters** : Reduce number of clusters by **1**
### Linkage

- **Single Linkage** : ==Minimum distance== between any two points in the clusters

$$
d(A, B) = \min_{x \in A, y \in B} ||x - y||
$$
- **Complete Linkage** : Records the maximal intercluster dissimilarity by looking at the ==largest distance== between points in separate clusters. 
 $$
 D(X, Y) = \max \{ d(x, y) : x \in X, y \in Y \}
$$
- **Average Linkage** : Calculates the mean distance between all pairs of observations in the two clusters.
- **Centroid Linkage** : Measures the distance between the mean vectors (centroids) of cluster A and cluster B, though the sources warn this can lead to "undesirable inversions" where branches cross.

### Hyperparameters

- Type of linkage (cluster-to-cluster) 
- Dissimilarity /Distance calculation (point-to-point) 
- Where to horizontal cut the tree (higher = fewer cluster, deeper = fine-grained)

### Advantage & Disadvantages

- Strengths: Not require an initial assumption for the number of clusters (K) and effectively captures nested relationships.
- Weaknesses: Highly sensitive to outliers and noise; a single noisy data point can significantly alter the tree's structure. Additionally, it performs poorly if the underlying data does not naturally exhibit a nested or hierarchical relationship.
- Categorization: While K-means and GMM are often categorized by their use of centroids and probabilities respectively, hierarchical clustering via a dendrogram is primarily distance-based and provides a hard decision for cluster membership once the cut is made.
## Connections
- **Parent:** [[Unsupervised Learning]][[Clustering]]
- **Related:** [[K-Mean|K-Means]]