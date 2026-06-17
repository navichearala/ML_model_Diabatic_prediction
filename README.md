# 🩺 Diabetes Risk Prediction — ML Classification Pipeline

> End-to-end machine learning pipeline to predict diabetes risk using clinical and lifestyle features, built on a dataset of 500,000+ patient records.

---

## 📌 Problem Statement

Diabetes affects hundreds of millions globally, yet early detection significantly improves outcomes. This project builds a robust, multi-model classification system to predict whether a patient is at risk of diabetes based on clinical indicators such as BMI, age, HbA1c levels, and blood glucose readings.

---

## 📊 Dataset

| Split | Records | Features |
|-------|---------|----------|
| Train | ~500,000 | 8 clinical features |
| Test | ~500,000 | 8 clinical features |

**Key Features:** Age, BMI, HbA1c Level, Blood Glucose Level, Hypertension, Heart Disease, Smoking History, Gender

---

## 🛠️ Approach & Methodology

1. **Exploratory Data Analysis (EDA)** — Distribution plots, correlation heatmaps, class imbalance analysis
2. **Data Preprocessing** — Missing value treatment, label encoding, feature scaling
3. **Feature Engineering** — Interaction terms, binning of continuous variables
4. **Model Training** — Multiple classifiers benchmarked:
   - Logistic Regression (baseline)
   - Random Forest Classifier
   - XGBoost Classifier
   - Gradient Boosting
5. **Model Evaluation** — Cross-validation, ROC-AUC, Precision-Recall curves
6. **Prediction & Submission** — Final predictions exported to `submission.csv`

---

## 📈 Results

| Model | ROC-AUC | Notes |
|-------|---------|-------|
| Logistic Regression | Baseline | Feature importance reference |
| Random Forest | High | Handles non-linearity well |
| XGBoost | **Best** | Tuned with cross-validation |

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/navichearala/ML_model_Diabatic_prediction.git
cd ML_model_Diabatic_prediction

# Install dependencies
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter

# Launch notebook
jupyter notebook Diabatic.ipynb
```

---

## 📁 Project Structure

```
ML_model_Diabatic_prediction/
├── Diabatic.ipynb       # Main analysis & modeling notebook
├── train.csv            # Training dataset
├── test.csv             # Test dataset
├── submission.csv       # Final predictions
└── README.md
```

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-AA4A44?style=flat-square&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)

---

## 💬 Key Learnings

- Handling large-scale imbalanced medical datasets
- Cross-validation strategies to prevent overfitting
- Feature importance analysis with tree-based models
- Trade-offs between model interpretability and performance in healthcare ML

---

*Part of my Data Science portfolio — [View more projects](https://github.com/navichearala)*
