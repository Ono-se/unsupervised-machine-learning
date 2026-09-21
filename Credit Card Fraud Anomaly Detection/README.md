# Detecting Anomalous Transactions

Unsupervised anomaly detection on credit card transactions, using **Isolation Forest** and **Local Outlier Factor (LOF)** to flag potentially fraudulent transactions without relying on labels during training.

## Dataset

[Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) (Kaggle) — anonymized, PCA-transformed transaction features (`V1`–`V28`), plus `Time`, `Amount`, and a binary `Class` label (1 = fraud) used only for evaluation.

## Approach

1. Clean the data (drop duplicates, check nulls) and explore `Amount`, `Time`, and class balance
2. Log-transform `Amount` to reduce skew
3. Fit **Isolation Forest** and **Local Outlier Factor** as unsupervised anomaly detectors
4. Compare both models against the true `Class` labels using precision, recall, F1, and confusion matrices
5. Tune Isolation Forest's `contamination` parameter and retrain a final model

## Results

Isolation Forest substantially outperformed LOF at identifying known fraud cases; LOF's locally-unusual points had little overlap with actual fraud labels. Tuning `contamination` to 0.0025 gave the best F1-score trade-off for Isolation Forest.

| Model | Precision | Recall | F1 |
|---|---|---|---|
| Isolation Forest (tuned) | ~0.23 | ~0.35 | ~0.28 |
| LOF | ~0.002 | ~0.002 | ~0.002 |

## Requirements

```
pandas
numpy
scikit-learn
seaborn
matplotlib
```
