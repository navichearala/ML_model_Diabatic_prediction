🩺 Diabetes Risk Prediction – End-to-End Machine Learning Project
📌 Project Overview

			  Diabetes is a chronic condition that often goes undetected until serious complications arise.
        The objective of this project was to build an end-to-end machine learning pipeline that predicts the probability of diabetes using demographic, lifestyle, and clinical data.

        Instead of producing a strict yes/no diagnosis, the model focuses on risk prediction, which is more practical for:

        early screening,

        preventive healthcare,

and prioritizing patients for further medical evaluation.

This project follows a production-oriented workflow, not just a Kaggle shortcut.

📊 Data Understanding

The project uses two datasets:

Training dataset – contains patient features and confirmed diabetes outcomes

Test dataset – contains patient features only, used for final prediction

Each row represents a patient with attributes such as:

age, BMI, blood pressure, cholesterol,

physical activity, diet, sleep habits,

smoking status, income, education,

family history and cardiovascular indicators.

Why this step matters

Machine learning models learn from patterns in data, not medical theory.
Understanding the data early helps avoid learning from errors, leakage, or unrealistic values.

✅ Data Validation & Sanity Checks

Before modeling, the data was carefully validated to ensure real-world consistency.

Checks included:

missing values (none found),

correct data types (numeric vs categorical),

medical plausibility (age, BMI, BP, cholesterol ranges),

consistent category labels (gender, education, smoking status).

Why this step was chosen

Poor data leads to confident but incorrect models.
These checks prevent unit errors, encoding issues, and misleading correlations.

🧩 Feature Categorization

Different feature types were handled appropriately:

Numeric Features

Examples: age, BMI, cholesterol, blood pressure
→ Used directly (or scaled when required)

Binary Features

Examples: family_history_diabetes (0/1)
→ Passed through unchanged

Ordinal Categorical Features

Examples:

education_level: No formal → Highschool → Graduate → Postgraduate

income_level: Low → High

→ Encoded using Ordinal Encoding to preserve order

Nominal Categorical Features

Examples:

gender, ethnicity, smoking_status

→ Encoded using One-Hot Encoding

Why this matters

Incorrect encoding can destroy meaningful relationships or introduce false signals.
This design preserves information correctly for modeling.

🔀 Train–Validation Split

The training data was split into:

Training set – used to learn patterns

Validation set – used to evaluate performance on unseen data

Stratified splitting was applied to maintain the diabetes class distribution.

Why this step was chosen

Evaluating a model on its training data leads to overly optimistic results.
This split simulates real-world deployment.

📉 Baseline Model – Logistic Regression

A Logistic Regression model was trained as the baseline.

Why Logistic Regression

simple and interpretable,

strong baseline for binary classification,

easy to debug and explain.

Baseline performance:

ROC-AUC ≈ 0.68

High recall, capturing most diabetic patients

This confirmed that the dataset contains meaningful predictive signal.

📏 Evaluation Metric – ROC-AUC

ROC-AUC was chosen as the primary metric.

What ROC-AUC means (simple explanation)

It measures how well the model ranks high-risk patients above low-risk patients, independent of any fixed threshold.

Why ROC-AUC was chosen

robust to class imbalance,

threshold-independent,

aligns with Kaggle evaluation and healthcare screening goals.

🌲 Advanced Model – LightGBM

To capture non-linear relationships, the model was upgraded to LightGBM.

Why LightGBM

handles non-linear patterns,

learns feature interactions automatically,

performs very well on tabular data,

widely used in industry.

This improved validation ROC-AUC to approximately 0.73.

🧹 Preprocessing Adjustment for Trees

Scaling was removed when using tree-based models.

Why

decision trees do not rely on distances,

raw values create better split decisions,

simpler and faster pipeline.

⏱️ Early Stopping

Early stopping was applied during training.

Why this matters

prevents overfitting,

automatically finds the optimal number of trees,

improves generalization performance.

🔁 K-Fold Cross-Validation

A single validation split can be noisy, so 5-Fold Stratified Cross-Validation was used.

This involved:

training five models,

validating on different subsets,

averaging predictions.

Result:
Reliable OOF ROC-AUC ≈ 0.728

🔀 Model Blending

Predictions from:

the best single LightGBM model, and

the K-Fold averaged LightGBM model

were blended.

Why blending works

Different models make different errors.
Averaging reduces noise and improves ranking consistency, often adding 0.01–0.02 ROC-AUC.

🧪 Test Data Handling

The test dataset was:

never used for training,

never used for tuning,

used only for final inference.

Why this discipline matters

Using test data early causes data leakage, leading to misleading performance.

📤 Final Output

For each patient, the model outputs:

diagnosed_diabetes → probability between 0 and 1

This format aligns exactly with Kaggle’s evaluation and real-world deployment needs.

🏁 Final Outcome

Built a production-style ML pipeline

Improved ROC-AUC from 0.68 → ~0.73+

Applied best practices: validation, early stopping, CV, blending

Delivered a clean, reproducible, and explainable solution

🔑 Key Takeaway

This project demonstrates how raw healthcare data can be transformed into a reliable diabetes risk prediction system through careful data handling, appropriate modeling choices, and strong validation practices.
