---
type: knowledge-note
created: 2026-05-06 10:47
tags:
  - feature-engineering
aliases: []
---

### Summary

> [!abstract] 
> **Pseudo-labeling** is a **semi-supervised learning** strategy used to improve model performance by leveraging unlabeled data. It involves using a model (trained on a labeled dataset) to predict labels for an unlabeled dataset. These "pseudo-labels" are then treated as ground truth to retrain or fine-tune the model, effectively increasing the size of the training set.

## Core Concept
- **Feature Discovery:** It is used to help models learn the underlying structure of data that was not originally available for training.
- **Robustness:** By incorporating unlabeled samples (such as those from a fixed test set), the model becomes more robust to "rare" values or categories that appear infrequently in the initial training data but are present in the test environment.

## Best Practices
1.  **Initial Training:** Train a model on the available labeled data.
2.  **Label Generation:** Use the trained model to generate predictions for unlabeled or test data.
3.  **Concatenation:** Combine the original training data with the newly "pseudo-labeled" data.
4.  **Final Training:** Retrain the model on this combined dataset.
5.  **Validation (Crucial Step):** To prevent **overfitting**, you must design your cross-validation to replicate the prediction process. This means performing the same concatenation and pseudo-labeling logic within each fold to ensure the validation set remains representative of truly unseen data.

