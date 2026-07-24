# Capstone 2: Employee Attrition Prediction

> See [00_common_guidelines.md](00_common_guidelines.md) for tools, deliverables, and evaluation criteria shared across all 4 capstones.

**Domain:** HR Analytics | **ML Task:** Classification | **Difficulty:** Easy–Intermediate | **Duration:** 10 Days

---

## 1. Business Context

An HR team wants to know in advance which employees might leave the company, so managers can check
in with them before it's too late.

## 2. Problem Statement

Predict whether an employee will leave the company (`Attrition`: Yes/No) based on their job and
satisfaction details.

## 3. Dataset

- **Name:** IBM HR Analytics Employee Attrition Dataset
- **Link:** https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset
- **Target:** `Attrition` (Yes/No)
- **Key columns:** `Age`, `Department`, `JobRole`, `MonthlyIncome`, `JobSatisfaction`, `OverTime`, `YearsAtCompany`, `Attrition`

## 4. SQL Questions (5, including one subquery)

1. Count of employees grouped by `Department`.
2. Attrition count (`Yes` vs `No`) grouped by `Department`.
3. Average `MonthlyIncome` grouped by `Attrition`.
4. Departments where the count of `Attrition = Yes` is above a chosen threshold (GROUP BY + HAVING).
5. List employees whose `MonthlyIncome` is below the company-wide average using a subquery: `WHERE MonthlyIncome < (SELECT AVG(MonthlyIncome) FROM employees)`.

## 5. EDA with Seaborn (6–7 charts)

1. `countplot` of `Attrition`
2. `countplot` of `Attrition` by `Department` (`hue`)
3. `boxplot` of `MonthlyIncome` by `Attrition`
4. `histplot` of `Age` split by `hue=Attrition`
5. Correlation `heatmap` of numeric columns
6. `barplot` of attrition rate by `OverTime`
7. (Optional) faceted `boxplot` of `MonthlyIncome` by `Attrition`, `col=Department`

Write 1–2 lines of observation under each chart.

## 6. Feature Engineering

- Drop constant columns (`EmployeeCount`, `Over18`, `StandardHours` if present).
- Encode `Attrition` and `OverTime` as 0/1.
- One-hot encode `Department` and `JobRole`.
- **Derived feature:** create `TenureRatio = YearsAtCompany / (TotalWorkingYears + 1)` — captures loyalty at this employer relative to total career length.
- Note the class imbalance in `Attrition` (far more "No" than "Yes") and why accuracy alone can be misleading here.

## 7. Models (3)

1. **Logistic Regression** (baseline)
2. **Decision Tree Classifier**
3. **Random Forest Classifier**

**Metrics:** Accuracy, Precision, Recall, F1-score, Confusion Matrix. Prioritize Recall/F1 on the "Yes" class over raw accuracy.

## 8. Business Insights

1. Which department has the highest attrition?
2. Does overtime or low income relate to higher attrition?
3. One simple retention recommendation for HR.

## 9. Prototype

Write a Python function `predict_attrition(age, department, monthly_income, overtime, job_satisfaction, tenure_ratio)`
that returns "Likely to leave" or "Likely to stay" plus a probability, using the best of the 3 models.
A small Streamlit app wrapping this function is encouraged but optional.

## 10. Optional Add-ons (only if time allows)

- A simple risk label: Low / Medium / High based on predicted probability.
- Feature importance chart from the Random Forest model.
- Ask an LLM to summarize the top 2 attrition drivers in plain English for a manager.
