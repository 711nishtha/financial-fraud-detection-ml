# Financial Fraud Detection — ML Exploration

## Overview

This repository contains an experimental machine learning pipeline for financial fraud detection, built to study how fraud signals emerge under extreme class imbalance and how decision thresholds impact business outcomes.

The project focuses on:

- feature behavior in transaction data
- recall-precision tradeoffs under skewed distributions
- risks of overconfidence when working with large but imperfect datasets

The work prioritizes understanding failure modes and assumptions, not claiming production readiness.

## Dataset Context

- ~6.36M transaction records
- Fraud rate ≈ 0.13% (severely imbalanced)
- Dataset was provided as part of an evaluation task and is likely synthetic
- Patterns may be cleaner than real banking data

**Important:**
Results should be interpreted as educational and exploratory, not representative of live fraud systems.

## Modeling Approach

### Feature Engineering

- ~20+ derived features from 6 base columns
- Balance consistency checks
- Transaction ratio features
- Delta-based behavioral indicators

Feature design intentionally explored simple rules that explain large signal portions, which helped surface risks of shortcut learning.

### Models Evaluated

- Logistic Regression
- Random Forest
- Gradient Boosting
- LightGBM
- XGBoost (best-performing)

### Class Imbalance Handling

- SMOTE applied to training data
- Evaluation focused on recall, precision, and threshold behavior, not accuracy

## Performance Snapshot (Exploratory)

| Metric | Value |
|---|---|
| Recall | 99.63% |
| Precision | 88.20% |
| F1 Score | 93.57% |
| AUC-ROC | 0.999 |
| Selected Threshold | 0.1 |

### Interpretation Notes

- High recall is expected given dataset structure
- Metrics are likely inflated due to dataset properties
- Results should not be generalized to real-world banking systems

## Key Learnings

- Base rates dominate fraud modeling — metrics without context are misleading
- Threshold selection matters more than model choice
- Single high-importance features can indicate data shortcuts, not intelligence
- Synthetic or evaluation datasets can mask real-world failure modes

## Limitations & Known Risks

This project intentionally documents its weaknesses:

- Random train/test split used → temporal leakage risk
- No concept drift simulation or monitoring
- No post-deployment evaluation strategy
- Dataset may encode unrealistic fraud patterns
- Business impact figures are illustrative, not audited
- No adversarial behavior or evolving fraud patterns modeled

These limitations are expected at this stage and were part of the learning objective.

## Repository Contents

```text
Financial-Fraud-Detection-ML/
├── fraud_detection.ipynb        # Full exploratory notebook
├── Outputs/                     # Visual analysis & plots
├── fraud_detection_model.pkl    # Serialized model (experimental)
├── feature_scaler.pkl
├── requirements.txt
└── README.md
```
## Intended Audience

This repository is intended for:

- students learning fraud ML fundamentals
- reviewers evaluating modeling thought process
- engineers interested in why fraud models fail

It is not a production artifact.

## Author

Nishtha Sharma  
Computer Science (Big Data & Analytics)

## Closing Note

This project was built to question assumptions, not to claim mastery.
Future iterations would prioritize:

- temporal validation
- drift detection
- monitoring metrics
- operational cost modeling

Those are system problems, not notebook problems — and this repo marks the transition toward understanding that difference.
