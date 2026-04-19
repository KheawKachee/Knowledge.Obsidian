---
type: Algorithm
created: 2026-04-18 23:43
tags:
  - SVM
aliases:
  - Support Vector Machine
---


## Summary
> [!abstract] 
> The core concept of a **Support Vector Machine (SVM)** is to perform classification by finding a **target hyperplane**—often described as a mathematical "knife"—that separates data points into two distinct classes. Unlike other classification methods like K-Nearest Neighbor (KNN) or Linear Discriminant Analysis (LDA), SVM is fundamentally a binary classifier that defines its decision boundary based on the interaction between classes


### Concept

SVM constructs a decision boundary described by the equation $$ f(x) = w^{T}x+ b$$
 - $w$ **(Normal Vector):** Defines the orientation of the hyperplane.
 - $b$ **(Bias):** Determines the hyperplane's offset from the origin.
 - **Classification:** During inference, a data point is assigned a class label based on which side of the hyperplane it falls (typically identified by whether $f(x)$ is positive or negative).
 
### Objective function 

to find *best hyperplane* by maximizing the margin    $$\hat{b}, \hat{w} = \arg\min_{b \in \mathbb{R}, w \in \mathbb{R}^n} \frac{1}{2} \|w\|_2^2$$
$$\text{s.t. } y_j (w^T x_j + b) \geq 1, \quad j = 1, 2, \dots, m$$ originate from  
$$distance = \frac{|w^T (x^+ - x^-)|}{\|w\|_2} = \frac{|1 - b - (-1 - b)|}{\|w\|_2} = \frac{2}{\|w\|_2}$$To maximize the margin $d$, we must **minimize** the $L_2$ norm $\|w\|^2$.

### Hard vs Soft Margin

[[Hard Margin]] make noisy data shift hyperplane drastically, [[Soft Margin]] relaxes the objective function with [[Slack Variables]] and *regularization parameter*

### [[Dual Problem]] formulation
 
$$
\arg\max_{\alpha,\beta \in \mathbb{R}^n}
\mathbf{1}^T \alpha
-\frac{1}{2}\sum_{i=1}^{m}\sum_{j=1}^{m}\alpha_i\alpha_j y_i y_j x_i^T x_j
$$

subject to

$$
\sum_{j=1}^{m}\alpha_j y_j = 0
$$

$$
\alpha_j = C - \beta_j,\qquad \alpha_j,\beta_j \ge 0
$$

for $j=1,\ldots,m$



### One Versus the Rest

A sequential or logical operation to identify specific categories among several possibilities:

- **Sequential Elimination :** For a dataset with multiple classes (e.g., Classes 1, 2, 3, and 4), the SVM first attempts to classify **==Class 1 against all other classes combined==** (the "rest"). Once Class 1 is identified or removed from the set, the algorithm performs a new classification for **Class 2 against the remaining classes**, continuing this process until all points are categorized.
- **Logical Grouping :** Alternatively, the model may ==group similar classes together== (e.g., separating Classes 1 & 2 from Classes 3 & 4) before performing further binary splits to isolate individual classes. This process often incorporates **logical operations** and can function similarly to a **decision tree** structure to reach a final classification.

> [!note] 
> Algorithms like **K-Nearest Neighbor (KNN)** naturally handle multiple classes by identifying the majority label among the k closest training features. Similarly, **Linear Discriminant Analysis (LDA)** and **Quadratic Discriminant Analysis (QDA)** use the mean and covariance of training statistics to model class-conditional probabilities for any number of categories

>[!summary]
>SVM is preferred when the **interaction between specific classes** is useful for the model's accuracy. Because it captures these interactions through the construction of a target hyperplane (a "knife" that cuts the feature space), it must rely on extensions like "[[#One versus the rest]]" to apply this binary logic across complex, multi-labeled datasets.

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]