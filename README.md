# Employee Salary Prediction

A supervised machine learning project that predicts whether an employee's annual income exceeds $50K using the UCI Adult Census Income dataset. This project was developed as part of the **AICTE B2 AI Program 2025–26** in collaboration with Edunet Foundation.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Methodology and Approach](#methodology-and-approach)
- [Model Performance and Results](#model-performance-and-results)
- [Installation and Usage](#installation-and-usage)
- [File Descriptions](#file-descriptions)
- [Future Scope and Improvements](#future-scope-and-improvements)
- [References](#references)

---

## Project Overview

**Objective:** Build a binary classification model to predict whether an employee earns `≤50K` or `>50K` per year based on demographic and employment attributes.

**Problem Type:** Binary Classification

**Key Goals:**
- Explore and clean the Adult Census Income dataset
- Engineer features and handle missing values
- Train and compare multiple classification algorithms
- Deploy the best model through an interactive Streamlit web application

---

## Dataset Description

The project uses the **UCI Adult Census Income** dataset (`adult.csv`), derived from the 1994 US Census database.

| Attribute | Details |
|-----------|---------|
| **Source** | UCI Machine Learning Repository |
| **Records** | ~48,842 (after cleaning: ~48,811) |
| **Features** | 14 (after dropping redundant columns: 13) |
| **Target** | `income` — `<=50K` or `>50K` |

### Feature Overview

| Feature | Type | Description |
|---------|------|-------------|
| `age` | Numerical | Age of the individual |
| `workclass` | Categorical | Employment type (Private, Self-emp, etc.) |
| `fnlwgt` | Numerical | Final weight (census sampling weight) |
| `educational-num` | Numerical | Years of education (numerical) |
| `marital-status` | Categorical | Marital status |
| `occupation` | Categorical | Type of occupation |
| `relationship` | Categorical | Family relationship |
| `race` | Categorical | Race |
| `gender` | Categorical | Gender |
| `capital-gain` | Numerical | Capital gains |
| `capital-loss` | Numerical | Capital losses |
| `hours-per-week` | Numerical | Average hours worked per week |
| `native-country` | Categorical | Country of origin |
| `income` | Target | `<=50K` or `>50K` |

> **Note:** The `education` column was dropped as it is redundant with `educational-num`.

---

## Methodology and Approach

### 1. Data Loading & Exploration
- Loaded data using `pandas`
- Explored shape, null values, and value distributions

### 2. Data Preprocessing
- **Missing values:** Replaced `'?'` entries in `workclass` and `occupation` with `'Others'`
- **Outlier removal:** Filtered `age` to [17, 75] and `educational-num` to [5, 16]
- **Noise removal:** Removed rows with `workclass` values `'Without-pay'` and `'Never-worked'`
- **Feature engineering:** Dropped the redundant `education` column

### 3. Encoding
- Applied `LabelEncoder` to all categorical features (`workclass`, `marital-status`, `occupation`, `relationship`, `race`, `gender`, `native-country`, `income`)

### 4. Model Training
- Split data: 80% training / 20% testing (`random_state=42`)
- Trained five classification models:
  - Logistic Regression
  - Random Forest Classifier
  - K-Nearest Neighbors (KNN)
  - Support Vector Machine (SVM)
  - Gradient Boosting Classifier

### 5. Model Evaluation
- Evaluated using `accuracy_score` and `classification_report`
- Selected the best-performing model automatically

### 6. Model Deployment
- Serialised the best model with `joblib` (`best_model.pkl`)
- Built an interactive web app with **Streamlit** (`app.py`)

---

## Model Performance and Results

| Model | Accuracy |
|-------|----------|
| Logistic Regression | 79.32% |
| K-Nearest Neighbors | 77.04% |
| Support Vector Machine | 78.84% |
| Random Forest | 85.25% |
| **Gradient Boosting** | **85.71%** ✅ |

**Best Model:** Gradient Boosting Classifier with **85.71% accuracy**

### Classification Report (Logistic Regression — sample)

| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| ≤50K | 0.84 | 0.93 | 0.88 |
| >50K | 0.69 | 0.46 | 0.55 |

---

## Installation and Usage

### Prerequisites

- Python 3.8 or higher
- pip

### 1. Clone the Repository

```bash
git clone https://github.com/M4ban/AICTE-B2-AI-2025-26.git
cd AICTE-B2-AI-2025-26
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Add the Dataset

Download `adult.csv` from the [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/adult) and place it in the project root directory.

### 4. Run the Jupyter Notebook

```bash
jupyter notebook "employee salary prediction.ipynb"
```

Execute all cells to preprocess the data, train the models, and generate `best_model.pkl`.

### 5. Launch the Streamlit App

```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501` to interact with the salary prediction application.

---

## File Descriptions

| File | Description |
|------|-------------|
| `employee salary prediction.ipynb` | Main Jupyter notebook — EDA, preprocessing, model training, and evaluation |
| `Employee Salary Prediction.pptx` | Project presentation slides |
| `app.py` | Streamlit web application (generated by the notebook) |
| `best_model.pkl` | Serialised best-performing Gradient Boosting model (generated by the notebook) |
| `requirements.txt` | Python package dependencies |
| `README.md` | Project documentation (this file) |
| `PROJECT_SUMMARY.md` | Executive summary and key findings |
| `LICENSE` | MIT License |

---

## Future Scope and Improvements

- **Hyperparameter Tuning:** Apply `GridSearchCV` or `RandomizedSearchCV` to further optimise model accuracy
- **Feature Engineering:** Explore interaction features (e.g., `age × hours-per-week`)
- **SHAP / LIME Explanations:** Add explainability to the predictions for better interpretability
- **Cross-Validation:** Use k-fold cross-validation for more robust performance estimates
- **Class Imbalance Handling:** Apply SMOTE or class-weight adjustments to improve `>50K` recall
- **Data Pipeline Automation:** Migrate preprocessing steps into a `scikit-learn` `Pipeline`
- **Docker Deployment:** Containerise the Streamlit app for easy cloud deployment
- **CI/CD:** Add GitHub Actions for automated testing and deployment

---

## References

1. Dua, D. and Graff, C. (2019). *UCI Machine Learning Repository* — Adult Dataset. University of California, Irvine. [https://archive.ics.uci.edu/ml/datasets/adult](https://archive.ics.uci.edu/ml/datasets/adult)
2. Pedregosa, F. et al. (2011). *Scikit-learn: Machine Learning in Python*. JMLR 12, pp. 2825–2830.
3. McKinney, W. (2010). *Data Structures for Statistical Computing in Python*. Proceedings of the 9th Python in Science Conference.
4. Streamlit Documentation — [https://docs.streamlit.io](https://docs.streamlit.io)
5. AICTE Edunet Foundation AI Program 2025–26 — [https://www.edunetfoundation.org](https://www.edunetfoundation.org)

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

*Developed as part of the AICTE B2 AI Program 2025–26 | Edunet Foundation*