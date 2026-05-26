---

# S&P 500 Market Direction Prediction — Machine Learning Analysis

[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/Pop%20Culture%20Data%20Transformation%20Analysis./Pop%20Culture%20Data%20Transformation%20Analysis.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)


Executive Summary
This project investigates whether the S&P 500’s short term market direction can be predicted using machine learning models trained on historical price data and engineered technical indicators. The analysis evaluates both 1 day and 5 day prediction horizons using Random Forest and XGBoost classifiers.

The findings show:
•	1 day predictions are effectively random, with accuracy near 50% and ROC AUC ≈ 0.50.
•	5 day predictions reveal modest structure, achieving ~56% accuracy and meaningful feature importance patterns.
•	Trend based features (Rolling Returns, Moving Averages, Momentum) become more predictive at multi day horizons.

This project demonstrates the limits of short term predictability and highlights how extending the horizon improves signal quality.

Project Overview

Objective
To determine whether machine learning models can reliably predict up or down movement in the S&P 500 using historical data and engineered technical indicators.

Key Questions
•	Can ML models outperform randomness in predicting daily market direction?
•	Does extending the prediction horizon improve accuracy?
•	Which features contribute most to predictive performance?
•	What are the practical and ethical implications of such models?
Dataset
Source
Historical S&P 500 index data retrieved via the yfinance Python library.

Variables Included
•	OHLC (Open, High, Low, Close)
•	Volume
•	Daily Returns
•	Engineered Technical Indicators:
•	Moving Averages (5, 20, 50)
•	Rolling Returns (5, 10, 20)
•	Volatility (20 day)
•	RSI
•	MACD & Signal Line
•	Momentum
•	Lagged Returns

Data Preparation Steps
•	Removed missing values
•	Ensured no look ahead bias
•	Created engineered features
•	Applied 80/20 train test split
Data Dictionary
		
|Feature|Definition|Puporse|		
|     |     |     |				
|     |     |     |		
|     |     |     |		
|     |     |     |				
|     |     |     |			
|     |     |     |		
|     |     |     |				
|     |     |     |		
		
		
		
		
Methods & Models

Modeling Approach
Four models were developed:
1.	Baseline Random Forest (1 day)
2.	Tuned Random Forest (1 day)
3.	XGBoost (1 day)
4.	XGBoost (5 day)
5.	
Evaluation Metrics
•	Accuracy
•	Precision, Recall, F1 Score
•	Confusion Matrix
•	ROC AUC
•	Feature Importance

Figures
•	Figures 1–4: Confusion Matrices (Models 1–4)
•	Figures 5–7: ROC Curves (Models 1–3)
•	Figure 8: Feature Importance (Model 4)
•	Figure 9: Model 4 Performance Summary'

Results
1 Day Models (Models 1–3)
•	Accuracy: 0.49–0.53
•	ROC AUC: ≈ 0.50
•	Bias toward predicting up days due to class imbalance
•	Feature importance inconsistent across models

Interpretation:
Daily market direction is effectively unpredictable. Even nonlinear models cannot extract meaningful signal from 1 day returns.

5 Day Model (Model 4)
•	Accuracy: 0.5638
•	Up Day Recall: 0.80
•	Weighted F1: 0.53
•	ROC AUC: 0.4898
Key Features:
•	Rolling10
•	Rolling20
•	MA20
•	Momentum

Interpretation:
Trend persistence becomes detectable at multi day horizons, improving directional accuracy even when probability calibration remains weak.

Cross Model Summary
•	1 day prediction ≈ random
•	Accuracy can improve without improving ROC AUC
•	5 day horizon reveals meaningful structure
•	Feature importance aligns with financial intuition (trend following)

Synopsis
Short term (1 day) market prediction is extremely limited due to noise and volatility.
However, extending the horizon to 5 days reveals modest but meaningful predictive structure. Machine learning can support decision making at broader horizons but should not be used as a standalone forecasting tool for daily predictions.

Assumptions
•	Statistical relationships remain stable over time
•	Historical data is representative of future behavior
•	No look ahead bias in feature construction

Challenges & Issues
•	High noise in daily returns
•	Class imbalance (more up days than down days)
•	Overfitting risk, especially for 1 day models
•	Low ROC AUC despite improved accuracy
•	Regime dependence (market behavior varies by volatility regime)
•	Feature instability across market conditions
Ethically, there is risk of users misinterpreting accuracy as predictive power.
All results must be contextualized to avoid overstating model capabilities.

Future Work
1. Multi Horizon Modeling
Explore 10 day, 20 day, and monthly horizons.
2. Regime Detection
Use volatility percentiles, MA crossovers, or clustering to segment market regimes.
3. Expanded Feature Sets

Incorporate:
•	Macroeconomic indicators
•	Sentiment analysis
•	Options based signals
•	Sector rotation metrics

Recommendations
•	Use models as decision support tools, not standalone predictors
•	Expand features gradually to avoid overfitting
•	Focus on multi day horizons where signal is stronger
•	Maintain transparency to prevent misinterpretation

Ethical Assessment
•	All data is publicly available (Yahoo Finance)
•	No personal or sensitive information used
•	All models, successful or not, were included
•	Full transparency in feature engineering and modeling
•	Care taken to avoid implying investment advice

References
Yahoo! Finance. (2026). S&P 500 (^GSPC).
Aroussi, R. (2026). yfinance. PyPI.
Just tell me what style you want.

