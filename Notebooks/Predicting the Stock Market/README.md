---

# S&P 500 Market Direction Prediction — Machine Learning Analysis

[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/Predicting%20the%20Stock%20Market/PLACEHOLDER)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

### Executive Summary

This project investigates whether the S&P 500’s short term market direction can be predicted using machine learning models trained on historical price data and engineered technical indicators. The analysis evaluates both 1 day and 5 day prediction horizons using Random Forest and XGBoost classifiers.

This project demonstrates the limits of short term predictability and highlights how extending the horizon improves signal quality.

---

### Project Overview

Project Overview
| Author | Nicholas Rodriguez | 
|------------------|--------|
| Language | Python (Jupyter Notebook) | 
| Data Source | Yahoo Finance (yfinance) | 
| Goal | Predict S&P 500 market direction using Machine Learning models and engineered features | 
| Design | Transparency, reproducability, no look ahead, and iterative model improvement | 

---

### Dataset Used — S&P 500 Historical Data
| Source | Yahoo Finance (^GSPC) | 
|------------------|--------|
| Content | Open, High, Low, and Close prices, volume and daily returns | 
| Transformations | Missing value removal, feature engineering, lag creation, and normalization | 
| Time Span | Historical dataset to May, 13 2026 | 
| Predictions Targets | 1-day, 5-day, both Up/Down | 

---

### Engineered Features

|Feature|Definition|Purpose|
|------------------|--------|-----|
|  Return   |   Daily percent change  |  Short term momentum   |				
|   Rolling Returns  | n-day cumulative returns  |   Trend persistence  |	
|  Moving Averages (MA)  |   Price smoothing   |  Trned regime detection   |		
|   Close/MA Rations  |  Price relative to MA   |  Trned strength  |				
|   Volatility20  |   20 day standard deviation  |  Market uncertainty   |			
|   Momentum  |  Price difference over n-days   |  Quant factor   |		
|   RSI  |  Relative Strength Index   |  Overbought / Undersold  |				
|   Lagged Returns  |  Prior day returns  |  Autoregressive structure  |		
|   MACD / Signal  |   Trend-following indicators  |  Momentum Shift   |			
		
---		
		
## Methods and Techniques

### Data Preparation Steps

- Removed missing values
- Ensured no look ahead bias
- Created engineered features
- Applied 80/20 train test split

---

## Modeling Approach

| Model | Horizon | Description | 
|------------------|--------|-----|
| Model 1 | 1-day | Baseline Random Forest | 
| Model 2 | 1-day | Tuned Random Forest | 
| Model 3 | 1-day | XGBoost classifier | 
| Model 4 | 5-day | XGBoost calssifier | 

### Evaluation Metrics

- Accuracy
- Precision, Recall, F1‑Score
- Confusion Matrix
- ROC‑AUC
- Feature Importance

---

## Results Summary

1 Day Models (Models 1–3)
- Accuracy: 0.49–0.53
- ROC AUC: ≈ 0.50
- Bias toward predicting up days due to class imbalance
- Feature importance inconsistent across models

Interpretation:
Daily market direction is effectively unpredictable. Even nonlinear models cannot extract meaningful signal from 1 day returns.

5 Day Model (Model 4)
- Accuracy: 0.5638
- Up Day Recall: 0.80
- Weighted F1: 0.53
- ROC AUC: 0.4898

Key Features:
- Rolling10
- Rolling20
- MA20
- Momentum

Interpretation:
Trend persistence becomes detectable at multi day horizons, improving directional accuracy even when probability calibration remains weak.

### Cross Model Summary

- 1 day prediction ≈ random
- Accuracy can improve without improving ROC AUC
- 5 day horizon reveals meaningful structure
- Feature importance aligns with financial intuition (trend following)

---

# Repository Structure
Nicholas-Rodriguez-Showcase/

├── Data

├── Images

├── Notebooks/

│   └── Predicting the Stock Market/

│       ├── Predicting the Stock Market.ipynb

│       └── README.md  ← Here

---

## How to Run the Notebook

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Install Required Packages

pip install pandas numpy matplotlib seaborn yfinance scikit-learn xgboost 

### Execution

Run all cells sequentially to reproduce:
- Data download via yfinance
- Feature engineering
- Model training (RF + XGBoost)
- 1 day and 5 day predictions
- Confusion matrices
- ROC curves
- Feature importance visualizations
