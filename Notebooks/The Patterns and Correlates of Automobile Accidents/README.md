# Auto Insurance Claims Analysis — Fraud Detection, Severity Modeling & Risk Profiling
## Dataset Source
This analysis uses the Auto Insurance Claims Data dataset by BuntyShah, available on Kaggle: https://www.kaggle.com/datasets/buntyshah/auto-insurance-claims-data

## Executive Summary

Insurance fraud is a major financial challenge, costing billions annually. This project demonstrates how data cleaning, feature engineering, dimensionality reduction, clustering, and
supervised learning can uncover patterns in auto insurance claims that may indicate fraud or predict incident severity.

Using 1,000 auto insurance claims, this notebook:

- Cleans and standardizes the dataset
- Encodes categorical variables
- Applies PCA for dimensionality reduction
- Uses K‑Means clustering to identify natural claim groupings
- Visualizes claim distributions, fraud frequency, and correlations
- Trains multiple supervised models (Random Forest, XGBoost, Stacking Ensemble)
- Applies SMOTE to address class imbalance
- Creates interaction features to capture hidden relationships
- Generates risk profiles by occupation, education, and hobbies

The result is a comprehensive, end‑to‑end workflow demonstrating how insurers can use machine learning to flag suspicious claims, predict severity, and understand customer risk patterns.

---

## Dataset Overview

The dataset includes:
- Customer demographics
- Policy details
- Incident characteristics
- Vehicle information
- Claim amounts
- Fraud indicator (fraud_reported)

Initial inspection revealed:
- 1,000 rows
- 39 columns
- Missing values primarily in authorities_contacted
- One fully empty column (_c39)

---

## Data Cleaning & Preprocessing

1. Duplicate Removal
All duplicate rows were removed.
2. Column Standardization
Column names were normalized to lowercase snake_case.
3. Missing Value Handling
A conservative strategy was used:

| Column Type | Strategy |
|----------|--------| 
| Fully Empty | Dropped | 
| Categorical | Filled with "Unknown" | 
| Numeric | Filled with median | 

5. One‑Hot Encoding
Categorical variables were encoded using:
pd.get_dummies(df, drop_first=True)


6. Final Dataset
- Shape: (1000, 39)
- Missing values: 0

---

## Exploratory Visualizations

1. Distribution of Total Claim Amount
Shows a right‑skewed distribution with a long tail of high‑value claims.
2. Claim Amount by Incident Severity
Boxplots reveal:
- Total Loss and Major Damage incidents produce the highest claim amounts
- Trivial Damage incidents cluster near the lower end
3. Fraud Frequency by Occupation
Stacked bar charts show:
- Certain occupations exhibit higher fraud proportions
- Others show almost none
4. Correlation Heatmap
Highlights relationships among numeric variables:
- Injury, property, and vehicle claims strongly correlate with total claim amount
- Severity correlates with claim magnitude
5. Fraud by Incident Type
Some incident types show higher fraud frequency than others.

---

## Dimensionality Reduction (PCA)

The encoded dataset contains hundreds of dummy variables. PCA was applied to:
- Reduce dimensionality
- Remove noise
- Improve cluster separation
Components were selected to retain 95% of variance.

---

## K‑Means Clustering

K‑Means was applied to the PCA‑transformed data.

### Cluster Selection

The elbow method identified K = 3 as optimal.

### Cluster Insights

Cluster 1 — Low‑Risk Claims
- Low claim amounts
- Mild severity
- Low fraud reporting
Cluster 2 — High‑Severity, High‑Cost Claims
- Large total claim amounts
- Severe incidents
- Higher fraud likelihood
Cluster 3 — Suspicious Patterns
- Moderate claim amounts
- Unusual incident combinations
- Higher frequency of "Unknown" values
- Elevated fraud reporting

---

## Supervised Modeling — Predicting Incident Severity

Multiple supervised models were trained to predict incident severity.

Model 1 — Random Forest (Occupation + Claim Amount + Tenure)
Accuracy: 0.39
Occupation alone provides limited predictive power.

Model 2 — Random Forest (Auto Make + Claim Amount + Tenure)
Accuracy: 0.40
Auto make adds marginal improvement.

Model 3 — Random Forest (Education Level + Claim Amount + Tenure)
Accuracy: 0.38
Education level does not meaningfully improve prediction.

Model 4 — Balanced Three‑Class Severity Prediction
After combining Minor Damage and Trivial Damage into Low Severity, accuracy improved:
Accuracy: 0.58
Macro F1: 0.58
This demonstrates that class imbalance significantly affects model performance.

---

## Advanced Modeling — Stacking Ensemble with SMOTE

To build a more powerful model:

Steps Taken
1. Combined Minor + Trivial Damage → Low Severity
2. Binned claim amounts into quantile‑based bands
3. Created interaction features:
- incident_collision
- edu_occupation
- hobby_relationship
4. One‑hot encoded all categorical features
5. Removed low‑variance features
6. Applied SMOTE to balance classes
7. Trained a stacking ensemble:
- Base models: Random Forest + XGBoost
- Meta‑model: Logistic Regression
  
### Results
Accuracy: 0.58
Macro Avg F1: 0.58

This is the strongest model in the workflow.

---

## Risk Profiling

Using the stacking model’s predictions, risk profiles were generated for:
- Education level
- Occupation
- Hobbies

Example Insight — Occupation
Some occupations show higher predicted severity:
- Armed Forces → higher proportion of severe claims
- Exec‑Managerial → more moderate severity
- Handlers‑Cleaners → evenly distributed

Example Insight — Hobbies
Certain hobbies correlate with higher predicted severity:
- Hiking, Chess, Cross‑Fit → higher severe‑claim proportions
- Kayaking, Golf → more low‑severity claims

These profiles help insurers understand behavioral patterns across customer segments.

---

## Business Insights

This analysis demonstrates:
- PCA + K‑Means can uncover meaningful structure in claims
- Fraud patterns emerge across occupations, incident types, and severity levels
- Supervised models struggle with imbalanced classes but improve with SMOTE
- Interaction features reveal hidden relationships
- Stacking ensembles outperform single models
- Risk profiles provide actionable insights for underwriting and fraud investigation
Future enhancements could include:
- Gradient boosting fraud classifiers
- Anomaly detection
- Cost‑sensitive learning
- Integration with policyholder history

---

## How to Run the Notebook

Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

Install Required Packages
pip install ipython-sql sqlalchemy pandas jupyter


Additional packages used:
pip install numpy seaborn matplotlib scikit-learn xgboost imbalanced-learn

---

## Execution

Launch Jupyter
jupyter notebook

Run all cells sequentially to reproduce:
- Data cleaning
- Encoding
- PCA
- K‑Means clustering
- Visualizations
- Random Forest models
- Stacking ensemble
- SMOTE balancing
- Risk profiling

