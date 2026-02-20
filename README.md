# 📊 Customer Churn Prediction with LightGBM & SHAP

## 📌 1. Project Overview

This project builds a high-performance **binary classification model** to predict customer churn and applies **SHAP (SHapley Additive exPlanations)** to interpret model predictions.

The objective was not only to achieve strong predictive performance (**AUC > 0.80**), but also to:

- Understand why the model makes certain predictions
- Explain both global and local model behavior
- Compare traditional feature importance with SHAP-based importance
- Extract actionable business insights

### ✅ Final Model Performance

- **ROC-AUC: 0.84**

This project demonstrates how to move beyond black-box models into **explainable AI systems**.

---

# 🎯 2. Problem Statement

Customer churn is a major challenge in subscription-based industries. Losing customers directly affects revenue and increases acquisition costs.

### Project Goals:

- Predict whether a customer will churn (Yes/No)
- Use SHAP to interpret model decisions
- Translate technical insights into business strategies

---

# 📊 3. Dataset Description

Dataset used: **Telco Customer Churn Dataset**

### Dataset Characteristics:

- ~7,000 customers
- Mix of numerical and categorical features
- Target variable: `Churn (Yes/No)`

---

## 🔹 Feature Categories

### 1️⃣ Demographic Features
- Gender
- SeniorCitizen
- Partner
- Dependents

### 2️⃣ Account Information
- Tenure
- Contract Type
- Payment Method
- MonthlyCharges
- TotalCharges

### 3️⃣ Service Information
- InternetService
- OnlineSecurity
- StreamingTV
- TechSupport
- etc.

---

# 🧪 4. Methodology

The project followed a structured ML workflow:

1. Data Cleaning  
2. Feature Encoding  
3. Model Training  
4. Hyperparameter Tuning  
5. Performance Evaluation  
6. SHAP-Based Interpretability  
7. Business Insight Extraction  

---

# 🧹 5. Data Preprocessing

Steps performed:

- Removed non-informative ID column
- Converted `TotalCharges` to numeric
- Imputed missing values with median
- Encoded target variable (Yes → 1, No → 0)
- One-hot encoded categorical features
- Stratified 80/20 train-test split
- Used fixed `random_state` for reproducibility

Stratified split ensured churn ratio preservation.

---

# 🤖 6. Model Development

### Baseline Model:
LightGBM classifier with default parameters.

- **Baseline ROC-AUC: 0.83**

---

# ⚙️ 7. Hyperparameter Tuning

Used:

- `RandomizedSearchCV`
- 3-fold cross-validation
- ROC-AUC as scoring metric

### Tuned Parameters:

- n_estimators
- learning_rate
- max_depth
- num_leaves
- subsample
- colsample_bytree

### Optimized Performance:

- **ROC-AUC: 0.84**

The tuned model improved generalization stability.

---

# 📈 8. Model Evaluation

### Final Metrics:

- **ROC-AUC: 0.84**
- Classification Report
- Confusion Matrix

The model shows strong separation between churn and non-churn customers.

Since interpretability is most valuable for accurate models, the AUC > 0.80 threshold was successfully achieved.

---

# 🔍 9. SHAP Interpretability Analysis

SHAP was used to explain model behavior at three levels:

- Global Interpretability
- Local Interpretability
- Feature Interaction Analysis

`TreeExplainer` was used since LightGBM is a tree-based model.

---

# 🌍 10. Global Interpretability

### SHAP Summary (Beeswarm) Plot Findings:

- Contract type strongly impacts churn
- MonthlyCharges positively correlates with churn
- Tenure negatively correlates with churn

### Interpretation:

- High monthly charges increase churn risk
- Long tenure reduces churn risk
- Month-to-month contracts drive churn probability

### SHAP Bar Plot Insights:

- Mean absolute SHAP values ranked features by importance
- Compared with LightGBM native importance

**Why SHAP is better:**

- Provides directional insights
- Captures interaction effects
- Reveals different ranking than native feature importance

---

# 👤 11. Local Interpretability

Two individual cases were analyzed:

## ✅ Correct Prediction

SHAP force and waterfall plots showed:

- High monthly charges → push toward churn
- Short tenure → increases churn probability
- Contract type → strong contributor

Prediction matched actual outcome.

---

## ❌ Incorrect Prediction

Analysis revealed:

- Conflicting feature contributions
- Some features pushed toward churn
- Others pushed toward non-churn

This demonstrates how SHAP helps diagnose borderline decisions.

---

# 🔗 12. Feature Interaction Analysis

SHAP dependence plots for:

- MonthlyCharges
- Tenure

### Findings:

- Non-linear relationship between charges and churn
- Strong drop in churn probability as tenure increases
- Interaction between contract type and charges

---

# 💡 13. Business Insights

## 1️⃣ Month-to-Month Contracts Drive Churn

**Action:**  
Offer incentives for long-term contracts.

---

## 2️⃣ High Monthly Charges Increase Risk

**Action:**  
- Provide bundled discounts  
- Offer targeted retention promotions  

---

## 3️⃣ Early Tenure Customers Are Vulnerable

**Action:**  
- Focus retention during first 6 months  
- Implement onboarding engagement programs  

---

## 4️⃣ Long-Term Customers Are Stable

**Action:**  
Create loyalty reward programs.

---

# 🏗 14. Project Structure


.
├── data/
│ └── Telco-Customer-Churn.csv
├── models/
│ └── final_model.pkl
├── notebook.ipynb
├── requirements.txt
└── README.md


---

# ⚙️ 15. Environment Setup

## Create Virtual Environment
python -m venv venv
Activate Environment

Windows

venv\Scripts\activate

Mac/Linux

source venv/bin/activate
Install Dependencies
pip install -r requirements.txt
▶️ 16. How to Run

Place dataset inside data/

Activate environment

Run:

jupyter notebook

Open notebook.ipynb

Run all cells

🏆 17. Key Achievements

Built LightGBM model with ROC-AUC 0.84

Performed systematic hyperparameter tuning

Implemented SHAP TreeExplainer

Generated summary, bar, force, waterfall, and dependence plots

Diagnosed correct and incorrect predictions

Translated technical findings into business actions

Delivered reproducible environment setup

🚀 18. Future Improvements

Use Optuna for advanced tuning

Try XGBoost or CatBoost

Add model calibration

Deploy as API

Add SHAP dashboard visualization

📌 Final Conclusion

This project demonstrates how machine learning can move beyond predictive accuracy into interpretable, trustworthy AI systems.

By combining:

High-performance LightGBM modeling

Robust cross-validation

SHAP-based interpretability

Business-oriented analysis

We created a fully explainable churn prediction system capable of generating actionable insights.

🎥 Video Walkthrough

https://youtu.be/uNEyQugwaWQ
