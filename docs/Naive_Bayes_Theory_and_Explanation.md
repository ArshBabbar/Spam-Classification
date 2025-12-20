# Naive Bayes Theory and Explanation (Spam Classification)

> 📘 **Note**  
> This document explains the theoretical foundation of the Naive Bayes algorithm used in this project.  
> The probability values shown in example calculations are **illustrative**, adapted for learning purposes and inspired by explanations from HTB Academy.  
> In the actual implementation, all probabilities are **automatically learned from the dataset during model training**.

---

## Why Naive Bayes?

Naive Bayes is a **supervised machine learning algorithm** based on probability theory.  
It is widely used for spam detection because:

- It performs well on text-based data
- It is computationally efficient
- It works effectively even with limited training data
- It scales well with a large number of features (words)

---

## Bayes’ Theorem

Bayes’ Theorem is defined as:

\[
P(A|B) = (P(B|A) * P(A)) / P(B)
\]

### Where:

- **P(A|B)** → Probability of A occuring when B is given to happen or true
              (example: what is Prob of (A)raining when its cloudy(B))
- **P(B|A)** → Probability of B occurring when A is given to happen or true
- **P(A)** → Prior Probability of A
              (Like what is prob of A before observation(calculations) like we didn't go outside our room but we think it will rain given it rained last few day's)
- **P(B)** → Prior Probability of B

---

## Mapping Bayes’ Theorem to Spam Detection

In the context of spam classification:

| Probability | Meaning |
|------------|--------|
| P(Spam \| Features) | Probability that an email/SMS is spam given its features |
| P(Features \| Spam) | Probability of observing features in spam messages |
| P(Spam) | Prior probability that a message is spam |
| P(Features) | Probability of observing features in any message |

The final formula becomes:

\[
P(Spam|Features) = ( P(Features|Spam) * P(Spam) ) / P(Features)
\]

---

## The Naive Assumption

Naive Bayes assumes that **all features are conditionally independent** given the class label.

For example, the presence of words like *"free"* and *"urgent"* in a message are assumed to be independent of each other once we know whether the message is spam or not.

This simplifies computation:

\[
P(Features|Spam) = P(feature1|Spam) * P(feature2|Spam) * ... * P(featureN|Spam)
\]

Similarly:

\[
P(Features|Not Spam) = P(feature1|Not Spam) * P(feature2|Not Spam) * ... * P(featureN|Not Spam)
\]

---

## Example Calculation (Illustrative)

Assume a dataset containing **1000 messages**:

- Spam messages = 300 → **P(Spam) = 0.3**
- Not spam messages = 700 → **P(Not Spam) = 0.7**

Let two features be:
- **F1** (e.g., word = "FREE")
- **F2** (e.g., word = "WIN")

Illustrative probabilities:

- P(F1 | Spam) = 0.4  
- P(F2 | Spam) = 0.5  
- P(F1 | Not Spam) = 0.2  
- P(F2 | Not Spam) = 0.3  
(here P(F1 | Spam) means Prob of having Feature1 in a spam and same for others) 
---

### Entering these Values in the Formula:

\[
P(F1, F2|Spam) = P(F1|Spam) * P(F2|Spam) = 0.4 * 0.5 = 0.2
\]

\[
P(F1, F2|Not Spam) = P(F1|Not Spam) * P(F2|Not Spam) = 0.2 * 0.3 = 0.06
\]

---

### The Final Formula Looks like:

P(Spam|F1, F2) = (P(F1, F2|Spam) * P(Spam)) / P(F1, F2)

---

### Filling in the Values

\[
P(F1, F2) = P(F1, F2|Spam) * P(Spam) + P(F1, F2|Not Spam) * P(Not Spam)
          = (0.2 * 0.3) + (0.06 * 0.7)
          = 0.06 + 0.042
          = 0.102 
\]

---

### Thus the Final Values We get:

\[
P(Spam|F1, F2) = (0.2 * 0.3) / 0.102
= 0.06 / 0.102
= 0.588
\]

\[
P(Not Spam|F1, F2) = (P(F1, F2|Not Spam) * P(Not Spam)) / P(F1, F2) 
 = (0.06 * 0.7) / 0.102
 = 0.042 / 0.102
 = 0.412
\]

---

## Final Classification

Since:

\[
P(Spam|F1, F2) > P(Not Spam|F1, F2) 
\]

The message is classified as **Spam**.

---

## Practical Implementation Note

In this project, **Multinomial Naive Bayes (Scikit-learn)** automatically estimates all probabilities from the training dataset using **maximum likelihood estimation with Laplace smoothing**.

The manual calculations shown above are included **only for conceptual understanding**.

---

## Summary

- Naive Bayes uses probability theory to classify messages
- Prior probabilities represent class distribution
- Likelihoods represent feature behavior within each class
- Independence assumptions simplify computation
- In practice, all probabilities are learned automatically during training
