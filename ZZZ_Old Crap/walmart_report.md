
# Walmart Weekly Sales Prediction – Final Report

## 1. Project Overview
The goal of this project is to build machine-learning models capable of predicting Walmart weekly sales using historical and economic variables. The project follows four major steps:
1. Exploratory Data Analysis (EDA)
2. Data cleaning and preprocessing
3. Baseline Linear Regression model
4. Regularized models (Ridge and Lasso)

The dataset originates from a modified version of a Kaggle competition dataset and contains store-level weekly sales data.

---

## 2. Data Cleaning & Feature Engineering

### 2.1 Initial Cleaning
- Removed all rows with missing target (`Weekly_Sales`).
- Converted the `Date` column to datetime.
- Extracted temporal features: `Year`, `Month`, `Day`, `DayOfWeek`.
- Removed the original `Date` column.

### 2.2 Outlier Removal
Applied a 3σ rule on:
- `Temperature`
- `Fuel_Price`
- `CPI`
- `Unemployment`

Rows falling outside `[mean - 3σ, mean + 3σ]` were removed.

### 2.3 Remaining NaNs
A small number of rows still had missing values (mostly due to missing dates).  
These rows were dropped to ensure compatibility with `LinearRegression` and `Ridge/Lasso`.

### 2.4 Saved Clean Dataset
Final cleaned dataset saved at:

```
data/processed/walmart_clean.csv
```

---

## 3. Exploratory Data Analysis (EDA)

### 3.1 Variable Distributions
Visual inspection showed:
- Normal retail right-skew in Weekly Sales.
- Predictors with moderate spread and seasonal behavior.

### 3.2 Pairplots
Revealed no strong linear relationships between single features and Weekly Sales.

### 3.3 Correlation Heatmap
Key observations:
- Weekly_Sales correlations with economic features were all near 0.
- Strong correlations appeared mostly between economic variables themselves.
- Conclusion: sales depend on **multiple factors combined**, not individually.

---

## 4. Baseline Model – Linear Regression

### 4.1 Preprocessing Pipeline
Using a `ColumnTransformer`:
- Numerical features → `StandardScaler`
- Categorical features → `OneHotEncoder`

### 4.2 Baseline Performance

| Metric | Train | Test |
|--------|--------|--------|
| **RMSE** | ~83,129 | ~141,158 |
| **R²** | 0.986 | 0.939 |

### 4.3 Interpretation
- The model explains **94% of sales variance** on unseen data.
- Small generalization gap.
- Excellent performance for a small dataset.

---

## 5. Regularized Models

### 5.1 Ridge Regression
GridSearch across multiple alphas.

**Test performance:**
- RMSE ≈ 230,548  
- R² ≈ 0.837  

Interpretation: Ridge underfits heavily due to excessive shrinkage.

---

### 5.2 Lasso Regression

**Test performance:**
- RMSE ≈ 163,973  
- R² ≈ 0.917  

Better than Ridge, but still under baseline.

---

## 6. Final Comparison

| Model | RMSE ↓ | R² ↑ | Interpretation |
|--------|-------------|------------|----------------|
| **Linear Regression** | **141,158** | **0.939** | Best model |
| Lasso | 163,973 | 0.917 | Mild underfitting |
| Ridge | 230,548 | 0.837 | Strong underfitting |

**Winner:**  
### **Linear Regression baseline**  
It offers the best accuracy, stability, and interpretability.

---

## 7. Conclusions
- Regularization did **not** improve predictive performance.
- Baseline Linear Regression remains optimal.
- Dataset size limits the effect of advanced models.
- Most value comes from proper preprocessing and feature engineering.

---

## 8. Future Improvements
- Add lagged sales and moving averages.
- Add promotional or holiday-specific features.
- Use tree-based models (e.g., Gradient Boosting).
- Apply time-series cross-validation.

---

End of Report.
