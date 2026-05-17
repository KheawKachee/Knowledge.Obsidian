---
type: knowledge-note
created: 2026-05-17 18:34
tags:
aliases: []
---


### Summary

> [!abstract] 
> Knowledge distillation is a machine learning technique used for model compression, where a small, compact model (the "student") is trained to reproduce the behavior and performance of a large, pre-trained, complex model (the "teacher"). This process allows for faster, more efficient deployment on edge devices (like mobile phones) without sacrificing the accuracy of the original, cumbersome model.


### Key Concepts

- Teacher Model: A large, high-capacity, pre-trained model (or ensemble of models) with high accuracy.
- Student Model: A smaller, lightweight model with fewer parameters, designed to be efficient for inference.

### Mechanism

- Knowledge Transfer: The student learns by minimizing the difference between its predictions and the teacher's predictions, rather than just learning from raw ground-truth labels.
- Soft Targets (Logits): The teacher often provides "softened" probability distributions (using a high-temperature softmax function) that reveal how the teacher model generalizes, such as which classes are similar to each other. 
- Hard Targets : Hard target is the original ground-truth label (represented as a one-hot vector) used during model training. 
$$\text{Loss}=\alpha\ \text{soft} + (1-\alpha)\ \text{hard}$$

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]