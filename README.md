AML Transaction Monitoring & Risk Scoring System
1. Problem Statement

Financial institutions are required to monitor customer transactions to detect potential money laundering and financial crime while minimizing false alerts and regulatory risk. Traditional rule-based systems generate excessive alerts, while black-box machine learning models lack explainability required for regulatory compliance.

This project demonstrates the design of an AML transaction monitoring system that combines rule-based controls, machine learning–based risk scoring, explainability, and cost-aware decision-making.

2. Business Context

In AML, the objective is not to predict fraud conclusively, but to prioritize high-risk transactions for human review.

Key constraints:

Missing suspicious activity can result in financial loss and regulatory penalties.

Excessive alerts increase operational workload and investigation cost.

Regulatory frameworks require transparent and explainable decision logic.

This project focuses on balancing these constraints using a risk-based approach.

3. System Design Overview

The AML monitoring system follows a layered architecture:

Sanctions Screening (Rule-based)
↓
Customer Risk Profiling (KYC, PEP, Geography)
↓
ML-Based Transaction Risk Scoring (Behavioral Patterns)
↓
Risk Adjustment Layer
↓
Threshold & Cost-Based Decision
↓
Alert Generation for Analyst Review


The machine learning model acts as a risk prioritization layer, not a final decision-maker.

4. Dataset Description

The dataset represents transactional activity with labeled suspicious behavior (fraud indicator used as a proxy for suspicious activity).

Key features include:

Transaction amount

Transaction frequency

Engineered behavioral features (velocity, ratios, interaction effects)

Note: This project uses simulated / public data for demonstration purposes. No real customer data is used.

5. Feature Engineering Strategy

Features were designed based on AML typologies, not raw values:

Transaction velocity to capture burst activity.

Amount per transaction ratios to detect structuring behavior.

High amount indicators to capture exposure risk.

Interaction features to model compounding risk signals.

All features are engineered to reflect behavioral deviation from expected patterns.

6. Model Selection

A Logistic Regression model was chosen due to:

Interpretability and regulatory acceptance.

Stable behavior on imbalanced data.

Clear linkage between features and risk contribution.

Class imbalance was handled using class-weight balancing.

7. Evaluation Approach

Accuracy was not used due to severe class imbalance.

Primary evaluation metrics:

Recall (fraud class) to minimize missed suspicious activity.

Precision to control alert volume.

ROC-AUC to monitor ranking performance.

8. Threshold Tuning & Cost-Based Decision Making

The default probability threshold (0.5) was replaced with a business-driven threshold.

False Negatives were assigned higher cost than False Positives.

Thresholds were evaluated to minimize total expected cost, not metric scores alone.

This aligns model behavior with business risk appetite.

9. Explainability & Regulatory Justification

Model decisions are explained using:

Logistic regression coefficients for global feature influence.

SHAP values for transaction-level explanations.

This allows analysts and auditors to understand why a transaction was flagged.

10. Limitations & Future Enhancements

No network or graph-based analysis implemented.

Sanctions screening represented conceptually, not via real watchlists.

Future work includes transaction network analysis, drift monitoring, and feedback-based retraining.
