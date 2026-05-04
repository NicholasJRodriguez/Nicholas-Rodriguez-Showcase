
---

# Honda Consumer Review Sentiment Prediction — Technical Guide

[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)]([Notebooks/National%20Database%20of%20Childcare%20Prices%20Analysis.ipynb](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/Satisfaction%20Prediction%20through%20Text%20Analysis%20of%20Automobile%20Manufacturer%20Reviews/Satisfaction%20Prediction%20through%20Text%20Analysis%20of%20Automobile%20Manufacturer%20Reviews.ipynb))
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## Executive Summary
Automotive manufacturers increasingly rely on consumer reviews to understand satisfaction, identify reliability concerns, and strengthen brand loyalty. This project demonstrates how text regression can be used to predict a reviewer’s satisfaction rating based solely on the language used in their written review.
Using a dataset of Honda vehicle reviews sourced from Kaggle, this analysis applies:
- Text cleaning
- Exploratory data analysis
- Feature engineering
- TF‑IDF vectorization
- PCA dimensionality reduction
- Ridge Regression
The result is a predictive model that explains 40% of the variance in satisfaction ratings and predicts ratings within ±0.7 points on a 1–5 scale.
This workflow provides Honda (or any manufacturer) with a scalable method for extracting actionable insights from large volumes of unstructured consumer feedback.

---

## Project Overview
| Item | Details | 
|------------------|--------|
| Author | Nicholas Rodriguez | 
| Dataset Source | Kaggle - Edmunds Consumer Car Ratings and Reviews | 
| Subset USed | Scrapped_Car_Reviews_Honda.csv | 
| Goal | Predict satisfaction ratings from review text | 
| Modeling Approach | TF-IDF + PCA + Ridge Regression | 
| Business Value | Early detection of dissatifaction, reliability concerns, and shifts in loyalty | 

---

## Dataset Description
The Honda subset contains:
- Review_Date
- Author_Name
- Vehicle_Title
- Review_Title
- Review
- Rating
- Index column
  
The target variable is Rating, a continuous value from 1.0 to 5.0 representing overall satisfaction.

Initial inspection revealed:
- 14,213 total entries
- Missing values across several metadata fields
- 12,384 usable reviews after cleaning

---

## Exploratory Data Analysis (EDA)

### Rating Distribution
A histogram of satisfaction ratings shows:
- A strong skew toward 5.0
- A dense cluster between 4.0–5.0
- A meaningful presence of lower ratings (1.0–3.0)
  
Insight: Honda enjoys strong brand loyalty, but lower ratings still contain valuable signals about dissatisfaction and reliability issues.

### Trim‑Level Satisfaction
Trim levels (LX, EX, SC) were extracted from Vehicle_Title.
Average ratings revealed:
- SC trim has the highest satisfaction
- EX follows
- LX trails
  
Insight: Certain configurations deliver a more satisfying ownership experience. Honda could use this to refine trim offerings or marketing strategies.

### Sentiment Polarity vs. Rating
Using TextBlob, sentiment polarity was compared to satisfaction ratings.
Findings:
- Higher polarity → higher rating
- Dense clustering around polarity 0.2–1.0 and ratings 4.0–5.0
- Significant scatter indicates polarity alone is insufficient
  
Insight: Emotional tone correlates with satisfaction, but deeper linguistic features are needed for accurate prediction.

### Word Cloud of Low‑Rated Reviews
A word cloud of reviews rated ≤ 3.0 highlighted terms such as:
- transmission, warranty, noise, system, replacement, Accord
  
Insight: These terms point to reliability concerns and ownership frustrations — critical areas for Honda to address.

### Graphical Insights Summary
Across all visualizations:
- Ratings skew high, but low ratings reveal meaningful dissatisfaction themes.
- SC trim appears most satisfying.
- Sentiment polarity correlates with satisfaction.
- Low‑rated reviews highlight reliability and performance issues.
  
These insights justify building a predictive model to quantify how review language influences satisfaction.

---

## Data Cleaning
The following columns were removed:
- Review_Date
- Author_Name
- Review_Title
- Vehicle_Title
- Unnamed: 0
- Trim
  
Rationale: These fields do not contribute to text‑based prediction and may introduce noise.

The Review column was cleaned by:
- Lowercasing
- Removing punctuation
- Normalizing whitespace
- Stripping non‑alphabetic tokens
  
The Rating column was filtered to valid values (1.0–5.0).

---

## Feature Engineering
Several interpretable features were engineered:
| Feature | Description | 
|------------------|--------|
| word_count | Number of words in the review | 
| char_count | Total characters | 
| avg_word_length | Average word length | 
| polarity | Sentiment polarity | 
| subjectivity | Degree of subjectivity | 
| mentions_keyword | Flags for terms like transmission, warranty and engine | 
| flesch_reading_ease | Readability score | 

All engineered features had 0 missing values.

Insight: These features enrich the model and provide interpretability beyond TF‑IDF.

---

## Model Preparation

### Token Cleaning
Non‑alphabetic tokens were removed to improve TF‑IDF clarity.

### TF‑IDF Vectorization
Parameters:
- stop_words='english'
- max_df=0.95
- min_df=2
- max_features=1000
  
### Train/Test Split
- 80% training
- 20% testing
  
### PCA Dimensionality Reduction
- Retained 95% variance
- Reduced sparsity
- Improved Ridge interpretability

## Model Training — Ridge Regression

Ridge Regression (alpha=0.1) was used due to its:
- Stability in high‑dimensional spaces
- Smooth coefficient shrinkage
- Interpretability

## Model Evaluation
| Metric | Result | Interpretation | 
|------|------|--------------|
| MSR | 0.48 | Predictions deviate by approximately ±0.7 on a 1–5 scale | 
| R² | 0.40 | The model explains 40% of rating variance | 


Insight: This is strong performance for subjective human‑written reviews.

---

## Interpreting Influential Words
Top words from PCA components reveal meaningful themes:
Component 1 — Positive Experience
- great, fun, love, comfortable, excellent
Component 2 — Longevity & Reliability
- miles, bought, years, maintenance, reliable
Component 3 — Fuel Economy
- mpg, gas, mileage, highway, hybrid
Insight: The model captures distinct dimensions of satisfaction — enjoyment, reliability, and efficiency.

---

## Conclusion
This project demonstrates that:
- Consumer language contains strong predictive signals
- Text regression can meaningfully estimate satisfaction
- PCA improves interpretability of TF‑IDF‑based models
- Honda can use this approach to identify dissatisfaction early, track reliability concerns, and strengthen brand loyalty
Future enhancements could include:
- Transformer‑based models (BERT, DistilBERT)
- Hybrid models combining text + vehicle metadata
- Topic modeling for deeper thematic insights
This workflow provides a scalable, interpretable foundation for text‑driven customer satisfaction analysis.


# Repository Structure
Nicholas-Rodriguez-Showcase/

Data

Images

Notebooks/

├── Satisfaction Prediction through Test Analysis of Automobile Manufacturer Reviews /

  │   └── README.md             # Technical guide (this file)

  │   └──  Satisfaction Prediction through Test Analysis of Automobile Manufacturer Reviews.ipynb              # Main demonstration notebook

# How to Run the Notebook
## Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab
## Install Required Packages
pip install ipython-sql sqlalchemy pandas jupyter
pip install numpy seaborn matplotlib textblob scikit-learn wordcloud textstat

# Execution
## Launch Jupyter
jupyter notebook

Then open the analysis notebook and run the cells sequentially from top to bottom.

This will:
- Load and clean the Honda review dataset
- Perform exploratory data analysis
- Engineer linguistic and structural features
- Vectorize text using TF‑IDF
- Apply PCA dimensionality reduction
- Train and evaluate the Ridge Regression model
- Extract interpretable insights from PCA components
