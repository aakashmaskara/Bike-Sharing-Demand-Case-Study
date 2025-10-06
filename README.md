# Bike Sharing Demand (Linear Regression)

Exploratory Data Analysis (EDA) and regression modeling to predict daily **bike rental counts** and explain the main drivers (seasonality, weather, and calendar effects).

## Introduction

This case study applies **EDA + linear regression** to a bike-sharing demand dataset.  
We analyze daily usage to uncover patterns by **season, weather, temperature, humidity, and calendar variables**, then build transparent models that estimate total rentals with explainable drivers.

When forecasting demand, two risks exist:
1. **Under-forecasting** → stockouts / lost rides
2. **Over-forecasting** → excess capacity / cost

Data-driven planning helps strike the right balance.

## Business Understanding

Operators need accurate, explainable forecasts for **inventory allocation**, **maintenance scheduling**, and **pricing**.  
Using EDA, we assess how **seasonality**, **working days/holidays**, and **weather** influence total demand (`cnt`), and quantify their contributions.

## Business Objectives

- Predict **total rentals** (`cnt`) per day  
- Identify **key drivers** of demand (and directionality)  
- Provide a **robust, auditable pipeline** with sound diagnostics and generalization

## Analytical Approach

1. **Data Understanding**
   - Inspect schema, missingness, outliers; align feature semantics (units, categories).

2. **Feature Engineering**
   - Derive calendar flags (e.g., weekend), transform skewed numerics (log of `cnt` if needed), create interaction terms (e.g., temp × season).

3. **Modeling**
   - Baseline: **Ordinary Least Squares**  
   - Regularized: **Ridge / Lasso / ElasticNet** for stability and variable selection  
   - Use `ColumnTransformer`/pipelines; **cross-validation** and grid search for hyperparameters.

4. **Diagnostics & Evaluation**
   - Residual analysis (patterns/heteroscedasticity), **MAE**, **RMSE**, **R²** (CV + holdout)  
   - Feature importance: coefficients (scaled), permutation importance (optional)

## Tools & Libraries

- **Python** (Jupyter Notebook)  
- **pandas**, **numpy**, **scikit-learn**, **matplotlib**, **seaborn**

## Data

The `day.csv` file contains daily records with fields such as **season (1–4), year (0/1), month (1–12), holiday, weekday, workingday, weather situation (1–4), temp, atemp, hum, windspeed, casual, registered, cnt** (total rentals). :contentReference[oaicite:0]{index=0}

## Key Insights

This workflow typically surfaces:
- Strong **seasonality** (higher demand in summer/fall vs winter)  
- **Temperature** (and “feels-like” temperature) positively associated with demand  
- **Humidity** and **poor weather** (weathersit 3–4) negatively associated  
- **Working day / holiday** effects and weekday patterns (commute-driven spikes)

*(Exact coefficients/metrics appear in the notebook.)*

## Conclusion & Business Impact

A regularized, explainable regression stack provides:
- **Accurate demand forecasts** for fleet allocation and staffing  
- Visibility into **demand drivers** to guide promotions and pricing  
- Stable performance across seasons and weather regimes

## Files in this Repository

| File Name | Description |
|-----------|-------------|
| `Linear_Regression_Bike_Sharing_Assignment.ipynb` | Full workflow (EDA → feature engineering → modeling → diagnostics) |
| `day.csv` | Daily bike-sharing dataset |
| `Data dictionary.pdf` | Data dictionary / field descriptions |

---

## Citation

If you use this dataset, please cite **Fanaee-T & Gama (2013)** as recommended in the dataset README.

---

## Author

**Aakash Maskara**  
*M.S. Robotics & Autonomy, Drexel University*  
Data Science | Machine Learning | Quantitative Finance  

[LinkedIn](https://linkedin.com/in/aakashmaskara) • [GitHub](https://github.com/AakashMaskara)
