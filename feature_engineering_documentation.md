# ============================================================
# CELL 72: FEATURE ENGINEERING DOCUMENTATION
# ============================================================

feature_engineering_report = f"""# Feature Engineering Documentation

## Week 10 — Customer Churn Prediction

## 1. Purpose

Feature engineering was performed to create additional variables that may provide useful business information for predicting customer churn.

---

## 2. Original Dataset

Dataset:

`customer_churn.csv`

Original number of features:

**{len(df.columns)}**

---

## 3. Engineered Features

The following features were created:

{chr(10).join("- **" + feature + "**" for feature in created_features)}

---

## 4. Feature Descriptions

"""

feature_descriptions = {
    "Customer_Lifetime_Value":
        "Estimated customer value calculated using monthly charges and customer tenure.",

    "Average_Monthly_Value":
        "Represents the customer's monthly charge value.",

    "Tenure_Group":
        "Groups customers according to their tenure into New, Developing, Established, and Loyal segments.",

    "Charge_Per_Tenure_Month":
        "Measures monthly charges relative to customer tenure.",

    "Total_Charges_Per_Month":
        "Calculates total charges relative to customer tenure.",

    "Payment_Efficiency":
        "Represents the relationship between a payment-related numerical feature and monthly charges."
}

for feature in created_features:

    description = feature_descriptions.get(
        feature,
        "Business-oriented engineered feature."
    )

    feature_engineering_report += (
        f"### {feature}\n\n"
        f"{description}\n\n"
    )

feature_engineering_report += f"""
---

## 5. Business Value

Feature engineering allows raw customer information to be transformed into variables that can better represent customer behavior.

These engineered variables can help with:

- Customer segmentation
- Churn prediction
- Retention analysis
- Customer value estimation
- Risk identification

---

## 6. Validation

The engineered dataset was checked for:

- Correct row count
- Expected feature creation
- Missing values
- Numerical data types
- Output generation

---

## 7. Output

The engineered dataset is stored at:

`outputs/processed_data/engineered_customer_churn.csv`

Feature documentation is stored at:

`outputs/results/feature_engineering_summary.csv`

---

## 8. Conclusion

Feature engineering successfully transformed the original customer dataset into a richer dataset containing additional business-oriented variables for machine learning analysis.
"""

with open(
    "feature_engineering_documentation.md",
    "w",
    encoding="utf-8"
) as file:
    file.write(feature_engineering_report)

print(
    "✅ feature_engineering_documentation.md created successfully."
)