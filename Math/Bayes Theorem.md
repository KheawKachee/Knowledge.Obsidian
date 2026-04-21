---
type: knowledge-note
created: 2026-04-21 20:08
tags:
aliases: []
---


### Summary

>[!notes]
>Bayes' Theorem is a fundamental principle in probability theory used to update the probability of a hypothesis as more evidence or information becomes available. Essentially, it allows us to calculate **conditional probability**: the likelihood of an event occurring given that another event has already occurred.


### Formulation 

Mathematically, it is expressed as:

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

Where:

- **$P(A|B)$ (Posterior):** The probability of hypothesis $A$ given evidence $B$. 
- **$P(B|A)$ (Likelihood):** The probability of evidence $B$ given that hypothesis $A$ is true.
- **$P(A)$ (Prior):** The initial probability of hypothesis $A$ before seeing the evidence
- **$P(B)$ (Evidence):** The total probability of the evidence under all possible hypotheses.

### Key Topics

- **Prior vs. Posterior Probability:** Understanding how our initial beliefs (prior) are "corrected" by new data to form a refined belief (posterior).
- **False Positives and Negatives:** Bayes' Theorem is crucial in medical testing and spam filters to determine the actual probability of having a disease (or a spam email) despite an imperfect test result.
- **The Base Rate Fallacy:** A common cognitive bias where people ignore the general prevalence of an event (the prior) in favor of specific new information.
- **Bayesian Inference:** The statistical method of using Bayes' Theorem to estimate parameters and uncertainty in data science and machine learning.

