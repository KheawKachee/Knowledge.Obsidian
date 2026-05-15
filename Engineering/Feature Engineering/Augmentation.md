---
type: knowledge-note
created: 2026-05-06 10:46
tags:
  - feature-engineering
aliases: []
---


### Summary

> [!abstract] 
> **Augmentation** is a critical **regularization technique** used primarily when training deep neural networks to ensure they generalize well to unseen data. By introducing variations into the training set, practitioners can prevent the model from overfitting to the specific pixel configurations of the original images.

## Purpose and Benefits
- **Improved Generalization:** Helps models perform better on real-world or "live" samples that may differ from the training data.
- **Robustness:** Enhances the model's ability to handle image degradation such as out-of-focus shots, motion blur, and lighting imbalances.
- **Handling Small Datasets:** Effective for medical or specialized imaging tasks where the number of unique samples is limited.

### Types
- **Shift, Scale, and Rotate:** Often applied with a specific probability (e.g., 80%) to change the orientation and position of the subject.
- **Random Cropping:** Removing up to 30% of each side to simulate different framing.
- **Normalization:** Scaling pixel values using pre-calculated mean and standard deviation (often from ImageNet) is considered standard practice.
- **Brightness and Contrast:** Randomly adjusting limits to account for different lighting conditions.
- **Gamma Correction:** Adjusting the luminance of the image.
- **Saturation:** Modifying color intensity in the HSV color space.
- **Gaussian Blur and Motion Blur:** Simulates out-of-focus or moving subjects.
- **Gaussian and Poisson Noise:** Adds electronic grain or photon noise to the channels.

## Advanced Methods
- **[[Pseudo-Labelling]]:** Using a model to label unlabeled data and then incorporating those "pseudo-labels" into the training set with augmentations to further improve performance.
- **GrabCut Augmentation:** A specialized technique mentioned in the context of object detection challenges.