---
type: knowledge-note
created: 2026-05-18 09:53
tags:
aliases: [YOLO, You Only Look Once]
references: [https://arxiv.org/abs/1506.02640]
---

### Summary

> [!abstract]
> YOLO reframes object detection as **one regression problem**: from full-image pixels directly to bounding boxes and class probabilities. It is fast because detection uses **one CNN evaluation**, not a multi-stage proposal/classification pipeline. The method gives strong real-time speed and fewer background false positives, but weaker localization, especially for small or grouped objects. 

### Statement

YOLO is best understood as the shift from:

```text
proposal → classify → refine → suppress
```

to:

```text
image → single CNN → boxes + classes
```

It trades some localization precision for speed, simplicity, and global reasoning.

### Core Idea

* Treat object detection as **single-stage regression**.
* Input image → CNN → bounding boxes + class probabilities.
* The model sees the **whole image**, so it can use global context.
* This helps reduce background false positives compared with region-based methods.

### Detection Formulation

* Image is divided into an `S × S` grid.
* If an object center falls inside a grid cell, that cell is responsible for detecting it.
* Each grid cell predicts:

  * `B` bounding boxes
  * confidence score for each box
  * `C` conditional class probabilities

For PASCAL VOC:

```text
S = 7
B = 2
C = 20

output = 7 × 7 × (2 × 5 + 20)
       = 7 × 7 × 30
```

### Bounding Box Prediction

Each predicted box contains:

```text
x, y, w, h, confidence
```

* `x, y` = box center relative to grid cell
* `w, h` = width and height relative to full image
* `confidence` = how likely the box contains an object and how well it overlaps the ground truth

Confidence:

$$
\text{confidence} = Pr(\text{Object}) \times IOU^{truth}_{pred}
$$

At test time:

$$
Pr(Class_i|Object) \times Pr(Object) \times IOU^{truth}_{pred}
$$$$
Pr(Class_i) \times IOU^{truth}_{pred}
$$

Meaning:

* class probability
* objectness
* localization quality
  are merged into one class-specific confidence score.

### Architecture

* Base YOLO:

  * 24 convolutional layers
  * 2 fully connected layers
* Inspired by GoogLeNet.
* Uses `1 × 1` convolution layers to reduce feature dimension.
* Uses `3 × 3` convolution layers for feature extraction.
* Pretrains convolution layers on ImageNet at `224 × 224`.
* Detection training uses larger `448 × 448` input.

Fast YOLO:

* smaller version
* 9 convolutional layers
* fewer filters
* same training/testing setup
* faster but lower mAP

### Training

* Loss function: sum-squared error.
* Problem: plain SSE does not perfectly match detection quality.
* Fix:

  * increase weight for bounding-box coordinate loss
  * decrease weight for confidence loss when no object exists

Parameters:

```text
λcoord = 5
λnoobj = 0.5
```

* Uses square root of width and height:

  * reduces over-penalty on large boxes
  * makes small-box errors matter more

### Box Responsibility

* YOLO predicts multiple boxes per grid cell.
* During training, only one predictor is responsible for each object.
* Responsibility goes to the predicted box with highest IOU with the ground truth.
* This encourages predictors to specialize in different:

  * object sizes
  * aspect ratios
  * classes

### Inference

* One image requires one network evaluation.
* On VOC:

  * predicts 98 boxes per image
  * class probabilities are predicted for each box
* [[NMS]] is still used.
* NMS adds around `2–3%` mAP, but is less central than in R-CNN/DPM pipelines.

### Limitations

* Strong spatial constraint:

  * each grid cell predicts only limited boxes
  * each grid cell predicts one class
* Struggles with:

  * small objects
  * grouped objects
  * unusual aspect ratios
  * unusual object configurations
* Main error source: localization.
* Coarse features from downsampling make precise box localization harder.



## Connections

* **Parent:** 
* **Similar:**
