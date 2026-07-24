# Capstone 1: House Price Prediction

> See [00_common_guidelines.md](00_common_guidelines.md) for tools, deliverables, and evaluation criteria shared across all 4 capstones.

**Domain:** Real Estate | **ML Task:** Regression | **Difficulty:** Easy–Intermediate | **Duration:** 10 Days

---

## 1. Business Context

A real estate agency wants a quick way to estimate a fair asking price for a home based on its
basic features, instead of guessing from memory of similar sales.

## 2. Problem Statement

Predict a house's sale price using simple features like area, number of bedrooms/bathrooms, and
overall quality.

## 3. Dataset

- **Name:** House Prices Dataset (simple version — Kaggle "House Price Prediction")
- **Link:** https://www.kaggle.com/datasets/shree1992/housedata
- **Target:** `price` (continuous)
- **Key columns:** `price`, `sqft_living`, `bedrooms`, `bathrooms`, `floors`, `condition`, `yr_built`, `city`

## 4. SQL Questions (5, including one subquery)

1. Average `price` grouped by `city`.
2. Cities where average `price` is above the overall average `price` (GROUP BY + HAVING).
3. Count of houses grouped by `bedrooms`.
4. Average `price` for houses with `bathrooms` > 2 vs. `bathrooms` <= 2 (simple WHERE + GROUP BY).
5. List all houses priced above the overall average `price` using a subquery: `WHERE price > (SELECT AVG(price) FROM houses)`.

## 5. EDA with Seaborn (6–7 charts)

1. `histplot` of `price`
2. `countplot` of `bedrooms`
3. `boxplot` of `price` by `bedrooms`
4. `scatterplot` of `sqft_living` vs `price`
5. Correlation `heatmap` of numeric columns
6. `regplot` of `sqft_living` vs `price` with a trend line
7. (Optional) `pairplot` of `price`, `sqft_living`, `bedrooms`, `bathrooms`

Write 1–2 lines of observation under each chart.

## 6. Feature Engineering

- Drop unneeded columns (e.g., `date`, `id` if present).
- Handle missing values.
- One-hot encode `city`.
- Scale numeric columns (needed for Linear Regression).
- **Derived feature:** create `house_age = current_year - yr_built` (or `yr_renovated` if present) — a simple, interpretable feature that usually helps the model.

## 7. Models (3)

1. **Linear Regression** (baseline)
2. **Decision Tree Regressor**
3. **Random Forest Regressor**

**Metrics:** R², MAE, RMSE. Plot predicted vs. actual for the best model.

## 8. Business Insights

1. Which feature affects price the most (area, bedrooms, or condition)?
2. Do bigger houses always cost more, or are there exceptions?
3. One simple recommendation for the agency (e.g., "focus on sqft_living when pricing").

## 9. Prototype

Write a Python function `predict_price(sqft_living, bedrooms, bathrooms, condition, house_age)` that
returns an estimated price using the best of the 3 models. A small Streamlit app wrapping this
function is encouraged but optional.

## 10. Optional Add-ons (only if time allows)

- Feature importance chart from the Random Forest model.
- Ask an LLM to turn your findings into a 3-sentence summary for a non-technical agent.
- A Tableau/Google Sheets view of average price by city.
