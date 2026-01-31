# 🏦 Home Credit Default Risk Prediction

![Status](https://img.shields.io/badge/Status-Completed-success)
![Python](https://img.shields.io/badge/Python-3.7%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit--Learn%20|%20XGBoost%20|%20Pandas-orange)

## 📌 Business Overview
In the financial industry, **Credit Risk** is the possibility of a loss resulting from a borrower's failure to repay a loan or meet contractual obligations. Home Credit Indonesia strives to provide financial inclusion for the unbanked population by providing a safe and positive borrowing experience.

**Goal:**  
Use historical loan application data to predict whether an applicant will be able to repay a loan. This creates a solution to ensure that clients capable of repayment are not rejected and that loans are given with a principal, maturity, and repayment calendar that will empower their clients to be successful.

## 📊 Data Understanding
The dataset contains **122 columns** (features) including:
*   **Target:** `1` (Client with payment difficulties), `0` (All other cases).
*   **Features:** Financial status, family status, education, external scoring sources, etc.
*   **Key Issue:** Highly imbalanced dataset (Target 1 is ~8% of total data).

## 🛠️ Project Workflow
1.  **Data Cleaning:** Handling anomalies (e.g., `DAYS_EMPLOYED` > 1000 years), converting data types, and checking duplicates.
2.  **EDA (Exploratory Data Analysis):**
    *   Univariate analysis for distribution.
    *   Bivariate analysis to find correlations with the Target.
    *   Customer Profiling (Who is the risky customer?).
3.  **Feature Engineering:**
    *   Creating domain knowledge features: `CREDIT_TO_INCOME_RATIO`, `ANNUITY_TO_INCOME`, etc.
    *   Encoding categorical variables (Label & One-Hot Encoding).
    *   Feature Selection (Top 30 features based on correlation).
4.  **Modeling:**
    *   Baseline: Logistic Regression (Balanced Class Weight).
    *   Advanced: Decision Tree (Tuned) & XGBoost.
    *   Metric Focus: **Recall** (To minimize False Negatives / missed risky applicants).

## 💡 Key Insights (EDA)
Based on the analysis, here are the characteristics of **High-Risk Applicants**:
1.  **Age Factor:** Younger applicants (< 30 years old) have a higher probability of default compared to older ones.
2.  **External Scores:** `EXT_SOURCE_1`, `2`, and `3` are the strongest predictors. A lower score indicates a higher risk.
3.  **Employment:** Applicants with shorter employment history (`DAYS_EMPLOYED`) tend to default more often.
4.  **Credit Load:** A higher Credit-to-Income ratio increases default risk.

## 🤖 Modeling Results
We compared several models focusing on **Recall** (ability to detect defaulters) and **ROC-AUC**.

| Model | Recall (Class 1) | ROC-AUC Score |
|-------|------------------|---------------|
| Logistic Regression | ~68% | 0.72 |
| **Decision Tree (Tuned)** | **~65%** | **0.74** |
| XGBoost | ~55% | 0.75 |

*> Note: The Decision Tree / XGBoost (choose your winner) was selected as the final model due to its balance between Recall and generalizability.*

## 📈 Business Recommendation
1.  **Risk-Based Pricing:** Do not reject all high-risk predictions. Instead, offer them lower credit limits or higher interest rates.
2.  **Strict Verification for Young Applicants:** Since the `<30` age group is risky, implement stricter document verification or require a guarantor for this segment.
3.  **Focus on External Score:** Integrate `EXT_SOURCE` validation early in the application process to filter out high-risk candidates quickly.

## 📂 File Structure
- `Home_Credit_Risk_Model.ipynb`: The complete notebook containing code from data loading to prediction.
- `requirements.txt`: List of libraries used.

---
*Created by [Fani_Dwi] - 2026*
