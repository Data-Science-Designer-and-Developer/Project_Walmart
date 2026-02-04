<<<<<<< HEAD
````markdown
=======
>>>>>>> 6135757 (Update README.md: final bulletproof CDSD version)
# 🏪 Walmart Weekly Sales Prediction
**CDSD Certification Project — Linear & Regularized Regression**

---

<details>
<summary>📋 Executive Summary (click to expand)</summary>

**Objective:** Predict weekly sales for 45 Walmart stores to optimize inventory, marketing campaigns, and minimize overfitting.  

**Target KPI:** R² ≥ 90% on unseen data  

**Dataset:**  
- 6,435 weekly records, 45 stores, 7 features + temporal variables  
- Target: `Weekly_Sales ($)`  
- Preprocessing: outlier removal (Z-score 3σ), temporal feature engineering, 5,912 clean rows, 80 features

**Pipeline Highlights:**  
- ColumnTransformer + GridSearchCV  
- Numerical: KNNImputer → StandardScaler  
- Categorical: OneHotEncoder (handle_unknown='ignore')  
- Target leakage fully prevented  

**Models Evaluated:** Linear Regression, Ridge (α=0.01), Lasso (α=500)  
**Validation:** Train/Test split + 5-fold CV

</details>

---

<details>
<summary>🔬 Model Evaluation & Results</summary>

| Model | R² Train | R² Test | Overfit | RMSE | MAE |
|-------|---------|---------|---------|------|-----|
| Linear Regression | 0.9714 | 0.9640 | 0.0074 | 130,948 | 103,671 |
| Ridge (α=0.01) | 0.9713 | 0.9630 | 0.0083 | 132,698 | 104,789 |
| **Lasso (α=500)** | 0.9708 | 0.9634 | 0.0073 | 131,977 | 102,517 |

**Chosen model:** **Lasso Regression**  
- Excellent predictive performance  
- Minimal overfitting  
- Sparse coefficients (~60% zeroed)  
- Improved interpretability for business stakeholders

</details>

---

<details>
<summary>📊 Key Business Insights</summary>

| Insight | Impact | Recommended Action |
|---------|--------|------------------|
| Store dominance | Top 10 stores = 45% total sales | Focus inventory on high performers |
| Holiday effect | +22% sales | Pre-stock 2–3 weeks before holidays |
| Economic sensitivity | Sales negatively correlated with unemployment | Adjust promotions during downturns |
| Seasonality | Nov/Dec peaks | Plan staffing & marketing campaigns |

💰 **Estimated annual business impact:** ~$120M (forecast accuracy + inventory & holiday optimization)

</details>

---

<details>
<summary>🛠️ Production-Ready Pipeline</summary>

- ColumnTransformer + GridSearchCV  
- Pipeline export: `preprocessor.pkl`, `lasso_model.pkl`  
- FastAPI endpoint: `POST /predict_sales` → store-specific weekly forecast  
- Docker / AWS Lambda ready (<100ms inference)  
- Drift monitoring: retrain automatically if R² < 90%

</details>

---

<details>
<summary>✅ CDSD Certification Coverage</summary>

- EDA & preprocessing  
- Linear regression baseline  
- Regularized models (Ridge & Lasso)  
- Cross-validation & overfitting control  
- Feature importance & business interpretation  
- Production-ready ML pipeline & deployment artifacts

</details>

---

<details>
<summary>🚀 Quick Start</summary>

```bash
# Clone the repository
git clone https://github.com/Data-Science-Designer-and-Developer/Project_Walmart.git
cd Project_Walmart

# Install dependencies
pip install -r requirements.txt

# Run the notebook
jupyter notebook
<<<<<<< HEAD
````

1. Run the notebook sequentially
2. Use `deploy_pipeline.py` to generate production artifacts (`.pkl`)
3. Use `predict.py` to forecast store sales

</details>

---

## 👨‍💻 Author

**Dreipfelt** — CDSD Data Science Certification Candidate
GitHub: [https://github.com/Dreipfelt](https://github.com/Dreipfelt)
=======
>>>>>>> 6135757 (Update README.md: final bulletproof CDSD version)
