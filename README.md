# 📊 Project Deliverable 2: Regression Modeling and Performance Evaluation

## 📂 Dataset Summary

The dataset contains economic indicators from the World Bank for various countries spanning **2010 to 2025**.  
Key attributes include:

- **GDP (Current USD)**
- **GDP per Capita (Current USD)**
- **Inflation (CPI %)**
- **Unemployment Rate (%)**
- **Interest Rate (Real, %)**
- **Government Expense (% of GDP)**
- **Tax Revenue (% of GDP)**
- **Public Debt (% of GDP)**

The **target variable** for prediction is **GDP per Capita (Current USD)** — a crucial indicator of economic prosperity.

The cleaned dataset consists of:  
- **2,777 training samples**  
- **695 test samples**

---

## ⚙️ Modeling Process

### Feature Engineering

Several new features were created to capture economic dynamics:

- **Log_GDP:** Logarithmic transformation of GDP to handle skewness  
- **GDP_per_Capita_Growth:** Year-over-year growth rate  
- **Inflation_Diff:** Difference between CPI and GDP deflator inflation  
- **Govt_Efficiency:** Tax revenue to government expenditure ratio  
- **Economic_Health:** Composite index combining GDP growth, unemployment, and inflation  

### Model Selection

We evaluated four regression models:

| Model               | Description                                    |
|---------------------|------------------------------------------------|
| Linear Regression   | Baseline linear model                           |
| Ridge Regression    | L2 regularization to prevent overfitting      |
| Lasso Regression    | L1 regularization for feature selection        |
| Random Forest       | Ensemble tree-based model for complex relationships |

---

## 📈 Evaluation Methodology

Models were evaluated using:

- **R² (R-squared):** Proportion of variance explained  
- **RMSE (Root Mean Squared Error):** Dollar error in GDP per capita predictions  
- **5-Fold Cross-Validation:** Robustness assessment  
- **Feature Importance Analysis:** Identification of key drivers  

---

## 🏆 Results and Performance

### Model Comparison

| Model            | R²     | RMSE ($)  | CV R² Mean | CV R² Std |
|------------------|---------|-----------|------------|-----------|
| Random Forest    | 0.8248  | 9,547.48  | 0.8395     | 0.0172    |
| Linear Regression| 0.2155  | 20,202.55 | 0.2550     | 0.0212    |
| Lasso Regression | 0.2155  | 20,202.70 | 0.2550     | 0.0212    |
| Ridge Regression | 0.2134  | 20,230.62 | 0.2541     | 0.0219    |

### Key Insights

- **Random Forest Dominance:**  
  - Explained 82.5% of variance, vastly outperforming linear models  
  - Lowest prediction error (RMSE ≈ $9,547 vs $20,200+ for linear)  
  - Most robust with highest cross-validation score (0.8395 ± 0.0172)  

- **Top Predictive Features:**  
  - **Log_GDP (30.6% importance):** Economic scale (log-transformed)  
  - **Current Account Balance (19.7%):** National savings-investment gap  
  - **Unemployment Rate (17.8%):** Labor market health  
  - **Inflation (CPI %) (7.6%):** Price stability indicator  
  - **Tax Revenue (% GDP) (6.2%):** Fiscal capacity  

- **Economic Relationships:**  
  - Economic scale (GDP) dominates per-capita wealth prediction  
  - External balance indicators more predictive than fiscal metrics  
  - Labor market conditions outweigh price stability in forecasting  

- **Modeling Observations:**  
  - Tree-based models effectively capture non-linear economic relationships  
  - Linear models performed similarly regardless of regularization technique  
  - Feature engineering (Log_GDP) was critical for model performance  

---

## 🚧 Challenges and Solutions

**High Variance in Target Variable**  
GDP per capita values vary a lot—from just a few hundred dollars to tens of thousands—which made it tough for some models to predict accurately. To handle this, we used tree-based models like Random Forest that are better at dealing with such wide ranges and can manage this kind of variability more effectively.

**Feature Skewness**  
Many of the economic indicators, including GDP, were heavily skewed, meaning their values weren’t evenly spread out. This can throw off models and lead to bias. To fix this, we transformed some features using logarithms (like Log_GDP), which helped normalize their distribution and made the models more stable.

**Multicollinearity**  
Some economic indicators were strongly related to each other, which can confuse models—especially linear ones—and make it harder to interpret results. We tackled this by applying regularization techniques like Ridge and Lasso regression, which help reduce the impact of correlated features. We also looked at feature importance to better understand which factors really mattered.

**Model Interpretability**  
Balancing strong predictive power with clear, understandable economic insights is tricky, especially when using complex models. To address this, we combined the power of Random Forests with SHAP value analysis, which breaks down how each feature influences predictions, making the results easier to interpret and trust.

---

## 🧾 Conclusion

The **Random Forest** model demonstrated superior predictive capability for GDP per capita, achieving an **R² score of 0.8248** (explaining 82.5% of variance) with a remarkably low error (**RMSE: $9,547.48**). This analysis uncovered three fundamental economic insights:

### 📌 Wealth Scales with Economic Size
Log-transformed GDP emerged as the **most important predictor** (30.6% importance), confirming that **national prosperity is fundamentally linked to the size of the economy**.

### 🌍 External Balances Trump Domestic Policy
**Current Account Balance** (19.7% importance) outperformed traditional fiscal metrics, indicating that **capital inflows and outflows are more predictive of wealth** than government efficiency or spending levels.

### 👥 Jobs Matter More Than Prices
**Unemployment Rate** (17.8%) had more than double the predictive impact of **Inflation** (7.6%), showing that **labor market health plays a greater role in prosperity** than price stability alone.

---

The stark performance difference between tree-based and linear models (**R²: 0.82 vs. 0.21**) reinforces the idea that **economic relationships are highly non-linear**, which traditional econometric models struggle to capture.

This research offers policymakers:

- ✅ **Quantifiable evidence** of key economic drivers  
- ✅ **A robust and accurate predictive framework**  
- ✅ **Clear priorities** for effective economic development strategies  

---
