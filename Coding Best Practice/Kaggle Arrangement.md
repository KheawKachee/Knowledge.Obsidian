---
type: knowledge-note
created: 2026-05-06 12:26
tags:
aliases:
  - Project Arrangement
---


### Summary

> [!abstract] 
>Arranging a machine learning project properly is essential for **reproducibility, scalability, and collaboration**. A standardized structure allows practitioners to treat most problems as "plug n' play," where a model can be trained or improved without significant code changes.

## Standard Project Directory Structure
For any new project, a dedicated folder should be created with the following subdirectories:

- **`input/`**: Contains all input data files (e.g., `train.csv`, `test.csv`). For specialized tasks, this may include subfolders for images or NLP embeddings.
- **`src/`**: Stores all executable Python scripts (`.py` files). Logic should be moved here once it is stable.
- **`models/`**: A repository for trained and serialized model files (e.g., `.bin` or `.pkl`).
- **`notebooks/`**: Reserved for Jupyter Notebooks used for **data exploration** and **plotting** only.
- **`README.md`**: A markdown file providing project descriptions and instructions on how to train or serve the model.
- **`LICENSE`**: A text file defining the project's licensing terms (e.g., MIT, Apache).

## Best Practices for Arrangement
- Baseline first, fine tune later
- Simple model to test POC (prefer [[Ensemble Decision Tree|Ensemble Technique]] before [[Efficient-net]])
- **Decide the Metric First:** Before coding, identify the evaluation metric (e.g., AUC, F1, Accuracy) based on the target distribution.
- **Move Beyond Notebooks:** While notebooks are great for exploration, production-ready frameworks should reside in IDEs/text editors as scripts.
- **Use `argparse`:** Pass fold numbers or model names as command-line arguments to prevent memory leaks and program crashes when running multiple folds.
- **Avoid Global Imports:** Explicit imports (e.g., `import config`) make the code understandable for others without needing constant consultation.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]