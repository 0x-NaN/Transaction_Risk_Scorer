# Transaction Risk Scoring using Explainable Machine Learning

## Overview

This project presents an **explainable transaction risk scoring system** that moves beyond traditional binary fraud detection. Instead of classifying transactions as simply *fraud* or *non-fraud*, the model assigns a **continuous risk score (0–100)** to each transaction, along with **human-interpretable explanations** for why a transaction is considered risky.

The work is intended for **academic evaluation and poster presentation**, with a focus on methodology, interpretability, and decision support rather than production deployment.

---

## Problem Statement

Traditional fraud detection systems treat fraud as a **binary classification problem**, which limits their usefulness in real-world decision making.

Binary outputs:

* Do not express *degree of risk*
* Force hard decisions without context
* Provide little justification for model predictions

---

## Objective

To transition from **fraud detection** to **fraud risk assessment** by:

* Producing a **continuous transaction risk score (0–100)**
* Preserving supervised learning using binary fraud labels
* Providing **explainable, feature-level insights** for each prediction
* Supporting downstream decision-making (approve, review, block)

---

## Methodology

### 1. Dataset

* Labeled transaction dataset with a **binary fraud indicator**
* Features are anonymized numerical variables (e.g., PCA-transformed)
* Highly imbalanced, reflecting real-world fraud settings

### 2. Model

* **XGBoost Classifier (CPU, histogram-based trees)**
* Chosen for:

  * Strong performance on tabular data
  * Robust handling of class imbalance
  * Compatibility with tree-based explainability methods

### 3. Risk Scoring

* Model predicts **fraud probability**
* Probability is rescaled into a **risk score**:

Risk Score = Fraud Probability × 100

This allows transactions to be ranked and grouped by relative risk rather than forced into binary outcomes.

### 4. Explainability (SHAP)

Explainability is a core component of this project.

* **SHAP (SHapley Additive exPlanations)** is used to:

  * Identify global risk-driving features
  * Explain individual transaction risk scores
* This ensures the model is **auditable and interpretable**, which is critical in financial and security domains

---

## Evaluation

The model is evaluated using standard classification metrics:

* ROC-AUC
* Precision / Recall
* Class imbalance-aware analysis

Additionally, **risk bucket analysis** is used to show how fraud prevalence varies across low, medium, and high risk score ranges.

---

## Implementation Details

* Language: **Python**
* Environment: **Jupyter Notebook**
* Libraries:

  * pandas, numpy
  * scikit-learn
  * xgboost
  * shap
  * joblib

The complete pipeline — training, evaluation, risk scoring, and explainability — is contained in a single notebook.

---

## Files

Transaction_Risk_Scoring_CPU_Academic_CORRECTED.ipynb
transactions.csv
model.pkl
scaler.pkl
README.md

*Note: model.pkl and scaler.pkl are exported artifacts for optional inference or extension.*

---

## Scope and Limitations

* This project focuses on **methodology and interpretability**
* UI and deployment are intentionally out of scope
* Feature semantics are anonymized; explanations are relative, not domain-specific
* The system is designed for **academic demonstration**, not production use

---

## Key Takeaways

* Risk scoring provides more actionable insights than binary fraud detection
* Explainability is essential when assigning continuous risk scores
* Tree-based models with SHAP offer a strong balance of performance and interpretability
* The approach is well-suited for financial, security, and governance-sensitive applications

---

## Future Work

* Threshold-based operational decision policies
* Integration with a lightweight inference API
* Time-aware or sequence-based risk modeling
* Comparative analysis with deep learning approaches

---

## Author Notes

This project emphasizes **clarity, explainability, and sound modeling choices** over system complexity. It is intended to demonstrate understanding of **applied machine learning**, not full-stack deployment.
