# Telecom Customer Churn Prediction

## Project Overview

This project predicts telecom customer churn using Machine Learning models trained on customer usage behaviour, revenue patterns, service quality, and account-related features.

The objective is to identify customers likely to churn so businesses can take proactive retention actions.

---

## Dataset Information

- Total Records: 51,047 customers
- Original Features: 58
- Final Predictive Features: 65
- Target Variable: Churn (Yes/No)

Class Distribution:
- Non-Churn: 71.18%
- Churn: 28.82%

Dataset Source:
Kaggle Telecom Customer Churn Dataset

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook

---

## Machine Learning Workflow

### Data Preprocessing
- Missing value handling
- Numerical scaling using StandardScaler
- One-hot encoding for categorical variables
- Leakage-safe preprocessing using Scikit-learn Pipelines

### Feature Engineering
Created custom features such as:
- RevenuePerMinute
- CallIssuePerMinute
- UsageDropFlag
- RevenueDropFlag
- RecurringChargeRevenueRatio

### Models Implemented
- Logistic Regression
- Random Forest Classifier

### Optimisation Techniques
- Hyperparameter tuning using RandomizedSearchCV
- Threshold optimisation using validation F1 score
- Stratified Train/Validation/Test split

---

## Final Selected Model

### Random Forest Baseline with Tuned Threshold

| Metric | Value |
|---|---|
| Threshold | 0.26 |
| Accuracy | 0.5458 |
| Precision | 0.3612 |
| Recall | 0.7494 |
| F1 Score | 0.4875 |
| ROC-AUC | 0.6564 |
| PR-AUC | 0.4283 |

---

## Business Interpretation

The final model is recall-oriented, meaning it prioritises identifying potential churners even at the cost of increased false positives.

This approach is suitable for low-cost customer retention strategies such as:
- Email campaigns
- Promotional offers
- Automated customer engagement workflows

---

## Key Learnings

- Importance of leakage-safe preprocessing
- Threshold tuning vs default threshold selection
- Precision-recall tradeoff in imbalanced classification problems
- Validation vs test set separation
- Business-focused ML interpretation

---

## Repository Structure

```text
Telecom-Customer-Churn-Prediction/
│
├── notebooks/
├── reports/
├── data/
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Author

Arun SK