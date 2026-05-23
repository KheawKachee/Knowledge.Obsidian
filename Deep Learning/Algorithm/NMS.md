---
type: knowledge-note
created: 2026-05-18 13:55
tags:  
aliases: [Non-Maximum Suppression]
references: https://arxiv.org/pdf/1704.04861
---


### Summary

> [!abstract] 
> Non-Maximum Suppression (NMS) is a critical post-processing algorithm in object detection pipelines used to eliminate redundant, overlapping bounding boxes predicted for the same object instance. By filtering candidate boxes based on class confidence scores and spatial overlap thresholds (Intersection over Union, or IoU), NMS ensures that each detected object is represented by exactly one optimal bounding box.


### Mathematical & Algorithmic Process

The standard NMS algorithm operates on a set of predicted bounding boxes $B = \{b_1, \dots, b_n\}$ and their corresponding confidence scores $S = \{s_1, \dots, s_n\}$ for a given class:

1. **Initialization**: Select an Intersection over Union (IoU) threshold $N$ (typically between 0.4 and 0.7). Initialize an empty list for finalized detections $D$.
2. **Sorting**: Sort the candidate bounding boxes in descending order based on their confidence scores $S$.
3. **Selection & Suppression Loop**:
    * Select the box with the highest confidence score, $m \in B$, and move it to the final detections list $D$. Remove $m$ from $B$.
    * Calculate the IoU of $m$ with all remaining boxes $b_i \in B$.
    * If $\text{IoU}(m, b_i) \ge N$, suppress and remove $b_i$ from $B$ under the assumption that it detects the same object.
4. **Termination**: Repeat Step 3 until the candidate set $B$ is empty.

$$\text{IoU}(A, B) = \frac{|A \cap B|}{|A \cup B|}$$

### Limitations & Variants

* **Hard Thresholding Problem**: If two objects of the same class are highly crowded or physically overlap (e.g., a herd of cattle or pedestrians in a crowd), standard NMS may mistakenly suppress the true bounding box of the obscured object because its IoU exceeds the threshold $N$.
* **Soft-NMS**: Rather than abruptly setting the confidence score of overlapping boxes to zero, Soft-NMS decays the confidence score of neighboring boxes as a continuous function of their overlap magnitude:
  $$s_i = s_i e^{-\frac{\text{IoU}(m, b_i)^2}{\sigma}}$$
  This allows heavily overlapped objects to survive the pruning phase if their initial prediction confidence was sufficiently high.

## Connections
* **Parent:** 
* **Similar:** 