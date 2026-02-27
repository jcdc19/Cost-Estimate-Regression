# Space Systems Cost Estimating Relationship (CER) Analysis

This repository contains a technical analysis of historical satellite program data to establish Cost Estimating Relationships (CER). The project utilizes statistical regression and machine learning to predict satellite development costs based on physical and mission parameters.

## 🚀 Overview
Cost estimation in the aerospace industry is critical for mission planning and budget allocation. This project automates the derivation of CERs from a historical dataset, accounting for complex variables like dry mass, power requirements, and mission longevity.

## 📊 Methodology

### 1. Data Foundation
The analysis processes a comprehensive dataset (`complete_satellite_costs.xlsx`) covering:
* **Satellite Programs:** Mission types (Communications, Science, etc.) and orbit classes (GEO, LEO).
* **Technical Parameters:** Dry mass (kg), Beginning-of-Life (BOL) power (W), and design life (years).
* **Cost Data:** Historical development and production costs adjusted to FY2020 USD.

### 2. Statistical Analysis
* **Heteroscedasticity Testing:** Utilizes the Breusch-Pagan test to identify non-constant variance in cost data. 
* **Log-Log Transformations:** Applied to stabilize variance and satisfy OLS regression assumptions, confirming a power-law relationship ($Cost = C \cdot Mass^a \cdot Power^b \cdot Life^c$).
* **Segmented Regression:** Separate models are generated for different mission types (e.g., GEO vs. LEO) to increase predictive accuracy.

### 3. Machine Learning Integration
* **XGBoost Regressor:** Implements gradient boosting to capture non-linear dependencies that traditional OLS might overlook.
* **Hyperparameter Tuning:** Employs `GridSearchCV` for model optimization.

## 🛠️ Technical Stack
* **Language:** Python 3.x
* **Libraries:** * Data Manipulation: `pandas`, `numpy`
    * Modeling: `scikit-learn`, `statsmodels`, `xgboost`
    * Visualization: `matplotlib`

## 📈 Key Findings
* **Mass as a Driver:** Analysis confirms that satellite dry mass remains the strongest predictor of development cost.
* **Complexity Factors:** Incorporating BOL power and design life significantly improves $R^2$ values.
* **Statistical Rigor:** Log-transformation proved essential in handling the heteroscedastic nature of high-cost aerospace hardware.

## 📋 How to Use
1. Ensure the dataset `complete_satellite_costs.xlsx` is in the working directory.
2. Run the `space_systems_CER_2.ipynb` notebook.
3. Use the `predict_development_cost()` function within the notebook to estimate costs for new satellite configurations.

---
*Developed as part of a technical portfolio in space systems and financial analysis.*
