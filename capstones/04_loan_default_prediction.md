# Capstone 4: Loan Default Prediction

> See [00_common_guidelines.md](00_common_guidelines.md) for tools, deliverables, and evaluation criteria shared across all 4 capstones.

**Domain:** Banking / Fintech | **ML Task:** Classification | **Difficulty:** Easy–Intermediate | **Duration:** 10 Days

---

## 1. Business Context

A bank wants to check whether a loan applicant is likely to be approved/repaid based on their
income, credit history, and loan amount, to speed up manual review.

## 2. Problem Statement

Predict `Loan_Status` (approved or not) using applicant income, credit history, and loan details.

## 3. Dataset

- **Name:** Loan Prediction Problem Dataset
- **Link:** https://www.kaggle.com/datasets/altruistdelhite04/loan-prediction-problem-dataset
- **Target:** `Loan_Status` (Y/N)
- **Key columns:** `Gender`, `Married`, `Education`, `ApplicantIncome`, `LoanAmount`, `Credit_History`, `Property_Area`, `Loan_Status`

## 4. SQL Questions (5, including one subquery)

1. Count of `Loan_Status` grouped by `Education`.
2. Average `ApplicantIncome` grouped by `Loan_Status`.
3. Count of loans grouped by `Property_Area`.
4. Approval rate grouped by `Credit_History` (GROUP BY, simple ratio).
5. List applicants whose `ApplicantIncome` is above the overall average using a subquery: `WHERE ApplicantIncome > (SELECT AVG(ApplicantIncome) FROM loans)`.

## 5. EDA with Seaborn (6–7 charts)

1. `countplot` of `Loan_Status`
2. `countplot` of `Loan_Status` by `Credit_History` (`hue`)
3. `boxplot` of `ApplicantIncome` by `Loan_Status`
4. `histplot` of `LoanAmount`
5. Correlation `heatmap` of numeric columns
6. `barplot` of approval rate by `Property_Area`
7. (Optional) `scatterplot` of `ApplicantIncome` vs `LoanAmount`, colored by `Loan_Status`

Write 1–2 lines of observation under each chart.

## 6. Feature Engineering

- Handle missing values (`Credit_History`, `LoanAmount`, etc. often have gaps).
- Encode `Loan_Status`, `Gender`, `Married` as 0/1.
- One-hot encode `Property_Area`, `Education`.
- **Derived feature:** create `TotalIncome = ApplicantIncome + CoapplicantIncome` and a `LoanToIncomeRatio = LoanAmount / (TotalIncome + 1)`.

## 7. Models (3)

1. **Logistic Regression** (baseline)
2. **Decision Tree Classifier**
3. **Random Forest Classifier**

**Metrics:** Accuracy, Precision, Recall, F1-score, Confusion Matrix.

## 8. Business Insights

1. Does `Credit_History` strongly affect approval? (usually the strongest signal)
2. Does income level relate to approval chances?
3. One simple recommendation for the bank's loan review process.

## 9. Prototype

Write a Python function `predict_loan_status(total_income, loan_amount, credit_history, property_area)`
that returns "Approved" or "Not Approved" plus a probability, using the best of the 3 models. A small
Streamlit loan-eligibility form is encouraged but optional.

## 10. Optional Add-ons (only if time allows)

- Feature importance chart from the Random Forest model.
- Ask an LLM to draft a short explanation of why credit history matters, for a loan officer.
