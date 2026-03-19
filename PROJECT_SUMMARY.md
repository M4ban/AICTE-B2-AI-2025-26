# Project Summary — Employee Salary Prediction

## Executive Summary

This project applies supervised machine learning to predict whether an employee's annual income is `≤50K` or `>50K`, using the UCI Adult Census Income dataset. Five classification algorithms were trained, evaluated, and compared. The **Gradient Boosting Classifier** achieved the highest accuracy of **85.71%** and was saved as the production model, deployed via a **Streamlit** web application.

---

## Key Findings

| Finding | Detail |
|---------|--------|
| **Best Model** | Gradient Boosting Classifier |
| **Best Accuracy** | 85.71% |
| **Dataset Size** | ~48,842 records, 14 features |
| **Target Classes** | `<=50K` (majority) / `>50K` (minority) |
| **Top Predictors** | Age, education level, occupation, hours per week, capital gain |
| **Preprocessing** | Missing value replacement, outlier removal, label encoding |
| **Deployment** | Streamlit web app with real-time prediction |

### Model Comparison

| Model | Accuracy |
|-------|----------|
| Logistic Regression | 79.32% |
| K-Nearest Neighbors | 77.04% |
| Support Vector Machine | 78.84% |
| Random Forest | 85.25% |
| **Gradient Boosting** | **85.71%** ✅ |

### Observations

- Tree-based ensemble models (Random Forest, Gradient Boosting) significantly outperform linear models on this dataset.
- The dataset is moderately imbalanced (~75% `≤50K`, ~25% `>50K`), which impacts recall for the minority class.
- Outlier removal improved model generalisation, particularly for the `age` and `educational-num` features.
- Label encoding was sufficient for this dataset size; one-hot encoding could be explored for further improvements.

---

## Deliverables

| Deliverable | Status |
|-------------|--------|
| Jupyter Notebook (EDA + Training) | ✅ Complete |
| Trained Model (`best_model.pkl`) | ✅ Complete |
| Streamlit Web App (`app.py`) | ✅ Complete |
| Project Presentation (`Employee Salary Prediction.pptx`) | ✅ Complete |
| README.md | ✅ Complete |
| requirements.txt | ✅ Complete |
| .gitignore | ✅ Complete |
| LICENSE | ✅ Complete |

---

## Next Steps

1. **Hyperparameter Optimisation** — Use `GridSearchCV` to tune Gradient Boosting parameters (e.g., `n_estimators`, `learning_rate`, `max_depth`).
2. **Address Class Imbalance** — Apply SMOTE oversampling or `class_weight='balanced'` to improve recall for the `>50K` class.
3. **Model Explainability** — Integrate SHAP values to explain individual predictions and feature importance.
4. **Extended Feature Engineering** — Explore interaction terms and polynomial features.
5. **Cloud Deployment** — Deploy the Streamlit app to Streamlit Community Cloud or Heroku for public access.
6. **API Development** — Wrap the model in a REST API (FastAPI/Flask) for integration with other systems.
7. **Automated Retraining** — Set up a pipeline for periodic retraining as new census data becomes available.

---

*AICTE B2 AI Program 2025–26 | Edunet Foundation*
