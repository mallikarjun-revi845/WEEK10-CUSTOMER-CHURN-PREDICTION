# ============================================================
# CELL 71: CREATE PREPROCESSING REPORT
# ============================================================

preprocessing_report = f"""# Week 10 — Customer Churn Prediction
# Data Preprocessing & Feature Engineering Report

## 1. Project Overview

This project demonstrates a complete data preprocessing and feature engineering workflow for customer churn prediction.

The objective is to prepare customer data for machine learning by applying categorical encoding, feature scaling, outlier detection, feature engineering, feature selection, and a complete preprocessing pipeline.

---

## 2. Dataset

**Dataset:** customer_churn.csv

**Rows:** {len(df)}

**Original Columns:** {len(df.columns)}

**Target Variable:** {target_column}

---

## 3. Data Quality

### Missing Values

Total missing values detected:

**{df.isnull().sum().sum()}**

### Duplicate Rows

Duplicate rows detected:

**{df.duplicated().sum()}**

The dataset was inspected before preprocessing.

---

## 4. Categorical Encoding

Three encoding techniques were demonstrated:

### Label Encoding

Categorical values were converted into integer labels.

### One-Hot Encoding

Categorical variables were transformed into binary indicator columns.

### Ordinal Encoding

Categorical values were converted into ordered numerical representations.

---

## 5. Feature Scaling

Two scaling techniques were implemented.

### Standard Scaling

StandardScaler transforms numerical features toward:

- Mean = 0
- Standard deviation = 1

### Min-Max Scaling

MinMaxScaler transforms numerical values approximately into the range:

**0 to 1**

Both methods were compared during preprocessing.

---

## 6. Outlier Detection

Two methods were used.

### IQR Method

Outliers were identified using:

**Q1 − 1.5 × IQR**

and

**Q3 + 1.5 × IQR**

### Z-Score Method

Observations with:

**|Z| > 3**

were considered potential outliers.

Outliers were detected and documented rather than automatically removed because extreme customer values may represent genuine business cases.

---

## 7. Feature Engineering

The project created the following engineered features:

{chr(10).join("- " + feature for feature in created_features)}

These features were created to provide additional business-oriented information for churn analysis.

---

## 8. Feature Selection

Feature selection was performed using the ANOVA F-test.

The method ranked processed features according to their relationship with the churn target.

The selected features were used for analysis and saved in:

`outputs/results/feature_selection_scores.csv`

---

## 9. Preprocessing Pipeline

A Scikit-learn ColumnTransformer pipeline was created.

### Numerical Pipeline

1. Median imputation
2. Standard scaling

### Categorical Pipeline

1. Most-frequent imputation
2. One-hot encoding

This approach ensures that preprocessing is applied consistently.

---

## 10. Train-Test Split

The dataset was divided into:

**80% Training Data**

**20% Testing Data**

Stratified splitting was used to preserve the churn class distribution.

---

## 11. Machine Learning Model

A Random Forest Classifier was trained using the preprocessing pipeline.

The model was configured with:

- 200 trees
- Maximum depth = 8
- Random state = 42
- Balanced class weights

---

## 12. Model Performance

| Metric | Score |
|---|---:|
| Accuracy | {accuracy:.4f} |
| Precision | {precision:.4f} |
| Recall | {recall:.4f} |
| F1 Score | {f1:.4f} |
| ROC-AUC | {roc_auc:.4f} |

---

## 13. Feature Importance

Random Forest feature importance was used to identify influential processed features.

The most important feature was:

**{top_feature}**

with an importance score of:

**{top_feature_importance:.4f}**

---

## 14. Churn Risk Analysis

Customers were classified into:

- Low Risk
- Medium Risk
- High Risk

based on predicted churn probability.

The high-risk customer count in the test dataset was:

**{len(high_risk_customers)}**

High-risk percentage:

**{high_risk_percentage:.2f}%**

---

## 15. Business Insights

The model can support businesses by identifying customers who may be at higher risk of churn.

Potential applications include:

- Customer retention campaigns
- Targeted offers
- Customer support prioritization
- Churn monitoring
- Customer segmentation
- Retention strategy planning

---

## 16. Outputs

Important outputs include:

- Encoded datasets
- Scaled datasets
- Engineered dataset
- Outlier analysis
- Feature selection results
- Model performance
- Feature importance
- Churn predictions
- High-risk customer list
- Business insights
- Visualization charts

---

## 17. Conclusion

The project successfully demonstrates a complete preprocessing and feature engineering workflow for customer churn prediction.

The workflow transforms raw customer data into a structured dataset suitable for machine learning while documenting each preprocessing decision.

**Week 10 Customer Churn Prediction — COMPLETED**
"""

with open(
    "preprocessing_report.md",
    "w",
    encoding="utf-8"
) as file:
    file.write(preprocessing_report)

print("✅ preprocessing_report.md created successfully.")