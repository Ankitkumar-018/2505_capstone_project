# Capstone 3: Superstore Sales & Profit Analytics

> See [00_common_guidelines.md](00_common_guidelines.md) for tools, deliverables, and evaluation criteria shared across all 4 capstones.

**Domain:** Retail | **ML Task:** Regression | **Difficulty:** Easy–Intermediate | **Duration:** 10 Days

---

## 1. Business Context

A retail chain wants to understand which orders make money and which lose money, so they can adjust
discounting.

## 2. Problem Statement

Predict the `Profit` of an order using `Sales`, `Discount`, `Category`, and `Region`.

## 3. Dataset

- **Name:** Superstore Sales Dataset
- **Link:** https://www.kaggle.com/datasets/vivek468/superstore-dataset-final
- **Target:** `Profit` (continuous)
- **Key columns:** `Sales`, `Quantity`, `Discount`, `Profit`, `Category`, `Sub-Category`, `Region`, `Segment`

## 4. SQL Questions (5, including one subquery)

1. Total `Sales` and `Profit` grouped by `Region`.
2. Total `Profit` grouped by `Category`.
3. Sub-categories where average `Profit` is negative (GROUP BY + HAVING).
4. Average `Discount` grouped by `Category`.
5. List all orders with `Profit` below the overall average `Profit` using a subquery: `WHERE Profit < (SELECT AVG(Profit) FROM orders)`.

## 5. EDA with Seaborn (6–7 charts)

1. `histplot` of `Profit`
2. `boxplot` of `Profit` by `Category`
3. `scatterplot` of `Discount` vs `Profit`
4. `countplot` of `Region`
5. Correlation `heatmap` of `Sales`, `Quantity`, `Discount`, `Profit`
6. `regplot` of `Discount` vs `Profit`
7. (Optional) faceted `boxplot` of `Profit` by `Category`, `col=Region`

Write 1–2 lines of observation under each chart.

## 6. Feature Engineering

- Handle missing values.
- One-hot encode `Category`, `Region`, `Segment`.
- Scale numeric columns if using Linear Regression.
- **Derived feature:** create `ProfitMargin = Profit / Sales` — a normalized measure of profitability that's often more informative than raw `Profit`.

## 7. Models (3)

1. **Linear Regression** (baseline)
2. **Decision Tree Regressor**
3. **Random Forest Regressor**

**Metrics:** R², MAE, RMSE. Plot predicted vs. actual for the best model.

## 8. Business Insights

1. Which category is least profitable?
2. Does a high discount usually mean low or negative profit?
3. One simple recommendation on discounting policy.

## 9. Prototype

Write a Python function `predict_profit(sales, discount, category, region)` that returns an
estimated profit using the best of the 3 models. A small Streamlit "discount simulator" is
encouraged but optional.

## 10. Optional Add-ons (only if time allows)

- Build a simple dashboard of this data in Google Sheets or Tableau.
- Feature importance chart from the Random Forest model.
- Ask an LLM to write a 3-sentence summary of the discount-vs-profit finding.
