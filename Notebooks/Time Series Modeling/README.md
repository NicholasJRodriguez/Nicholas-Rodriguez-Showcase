# U.S. Retail Sales Forecasting — Time Series Modeling with SARIMA

[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)]([https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/The%20Patterns%20and%20Correlates%20of%20Automobile%20Accidents/The%20Patterns%20and%20Correlates%20of%20Automobile%20Accidents.ipynb](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/Time%20Series%20Modeling/Time%20Series%20Modeling.ipynb))
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Dataset Sample

https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Data/Time%20Series%20Modeling%20Data%20(us_retail_sales.xls)

## Executive Summary

This project analyzes U.S. monthly retail sales from 1992 to 2021 and builds a SARIMA time‑series forecasting model to predict short‑term retail sales. The workflow includes:
- Data reshaping and cleaning
- Visualization of long‑term retail trends
- Identification of major macroeconomic disruptions
- Train/test split for out‑of‑sample evaluation
- SARIMA(1,1,1)(1,1,1,12) modeling
- 6‑month and 12‑month forecasts
- RMSE evaluation on the 2020–2021 test period
The analysis demonstrates how classical time‑series models behave when confronted with stable long‑term patterns and extreme shocks such as the 2008 financial crisis and COVID‑19.

---

## Dataset Overview

The dataset contains:
- YEAR (1992–2021)
- Monthly retail sales columns (JAN–DEC)
- Sales values in millions of USD
The data is reshaped from wide to long format and converted into a proper monthly time series.

---

## Data Preparation

1. Reshaping to Long Format
The dataset is melted into:

| YEAR | MONTH | SALES | DATE | 


A DATE column is created using:
pd.to_datetime(df_long["YEAR"].astype(str) + df_long["MONTH"], format="%Y%b")

2. Sorting and Frequency Alignment
- Sorted chronologically
- Reindexed to ensure no missing months
- Missing months (none found) would be filled with NaN

---

## Exploratory Visualization

A line chart of U.S. Monthly Retail Sales (1992–2021) reveals:
1992–2008: Steady Growth
Retail sales increased consistently during this period.
2008–2012: Financial Crisis Decline
A sharp drop occurs during the 2008 housing and credit crisis, with recovery taking several years.
2012–2020: Strong Expansion
Sales rise steadily with no major disruptions.
2020–2021: COVID‑19 Shock
A dramatic collapse occurs in early 2020, followed by:
- A rapid rebound
- A surge to historically high levels
- A shift toward digital commerce
These macroeconomic events provide essential context for forecasting.

---

## Train/Test Split

To evaluate forecasting performance:
- Training period: Jan 1992 → Jun 2020
- Test period: Jul 2020 → Jun 2021 (12 months)
This isolates the volatile COVID‑19 period for out‑of‑sample testing.

---

## SARIMA Modeling

A SARIMA(1,1,1)(1,1,1,12) model was fit to the training data.

Model Summary Highlights
- Seasonal AR and MA terms are highly significant
- Strong annual seasonality (12‑month cycle)
- Residual diagnostics show non‑normality and heteroskedasticity
- Model still captures major seasonal structure

---

## Forecasting

6‑Month Forecast (Jul–Dec 2021)
A zoomed plot from 2019 onward shows:
- Smooth continuation from the training series
- Forecast uncertainty widening over time
- Seasonal pattern preserved
- Confidence intervals capturing expected volatility

12‑Month Forecast (Jul 2021–Jun 2022)
The extended forecast shows:
- Continued upward trend
- Seasonal peaks and troughs
- Increasing uncertainty as horizon lengthens

---

## Model Evaluation

RMSE was computed on the 12‑month test set:
RMSE: 59819.07


### Interpretation
- RMSE ≈ $60 billion
- Indicates the model struggles with the extreme volatility introduced by COVID‑19
- Classical SARIMA models assume stable patterns, which were disrupted in 2020–2021
- Still provides meaningful structure and seasonal insight

---

## Insights & Interpretation

1. SARIMA captures long‑term seasonality well
Retail sales follow strong annual cycles.
2. COVID‑19 introduces unprecedented volatility
No classical model can fully anticipate the shock magnitude.
3. Forecasts remain directionally reasonable
Despite high RMSE, the model:
- Tracks the upward trend
- Preserves seasonal structure
- Produces interpretable confidence intervals
4. Improvement opportunities
Future work could include:
- SARIMAX with exogenous variables (CPI, unemployment, consumer sentiment)
- Prophet or LSTM models for nonlinear patterns
- Regime‑switching models for crisis periods

---

## How to Run the Notebook

Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

---

## Install Required Packages
pip install pandas matplotlib statsmodels scikit-learn jupyter

---

## Execution

Launch Jupyter
jupyter notebook


Open the notebook and run all cells sequentially to reproduce:
- Data reshaping
- Visualization
- Train/test split
- SARIMA modeling
- Forecasting
- RMSE evaluation
