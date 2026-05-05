# Understanding the Electric Vehicle Landscape in Washington State

[![Jupyter Notebook](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/Understanding%20the%20Electric%20Vehicle%20Landscape%20in%20the%20State%20of%20Washington/code.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## Executive Summary

This project delivers a comprehensive, data-driven analysis of the electric vehicle (EV) population registered in Washington State using public data from the Washington State Department of Licensing. Through data cleaning, exploratory data analysis, and supervised and unsupervised machine learning, the analysis uncovers trends in EV adoption, pricing, and range capabilities across Battery Electric Vehicles (BEVs) and Plug-in Hybrid Electric Vehicles (PHEVs). The findings provide actionable insights for policymakers, automobile manufacturer analysts, and sustainability researchers seeking to understand the rapidly evolving EV market at the state level.

---

## Project Overview

| Item        | Detail(s) |
|------------------|--------|
| **Author**       | Nicholas Rodriguez |
| **Date**         | April 2025 |
| **Language**     | Python (Jupyter Notebook) |
| **Data Source**   | Washington State Department of Licensing — Electric Vehicle Population Data |
| **Primary Goal** | Analyze Washington State's registered EV population to identify patterns, EV range distributions, EV pricing relationships, and market segments using EDA and machine learning |

---

## Dataset Description

| Feature | Description |
|---------|-------------|
| **File** | `Electric_Vehicle_Population_Data.csv` |
| **Source** | Washington State Department of Licensing |
| **Granularity** | One row per registered electric vehicle |

### Variables Selected for Analysis

| Variable | Description |
|----------|-------------|
| `County` | County of vehicle registration |
| `City` | City of vehicle registration |
| `Model Year` | Model year of the vehicle |
| `Make` | Vehicle manufacturer |
| `Model` | Vehicle model name |
| `Electric Vehicle Type` | BEV (Battery Electric Vehicle) or PHEV (Plug-in Hybrid Electric Vehicle) |
| `Clean Alternative Fuel Vehicle (CAFV) Eligibility` | Eligibility status for clean fuel incentives |
| `Electric Range` | EPA-rated electric-only range (miles) |
| `Base MSRP` | Manufacturer's suggested retail price (USD) |

---

## Methods & Techniques

### Data Cleaning & Preprocessing
- **Missing value removal** — Dropped rows with null values in `Model Year`, `Electric Range`, `Base MSRP`, and `Electric Vehicle Type`
- **Label standardization** — Mapped EV type labels to concise codes (`"Battery Electric Vehicle (BEV)"` → `"BEV"`, `"Plug-in Hybrid Electric Vehicle (PHEV)"` → `"PHEV"`)
- **Type casting** — Converted categorical variables to string type for consistent encoding
- **Zero-range filtering** — Identified and removed records with an electric range of zero, which represented missing and/or erroneous data
- **Outlier removal** — Detected and removed a single extreme outlier (Porsche 918 Spyder, MSRP ≈ $845,000) that compressed scatterplot visualizations and distorted regression fits

### Exploratory Data Analysis
- Distribution of Electric Range (histogram with KDE overlay)
- MSRP vs. Electric Range (scatterplot, pre- and post-outlier removal)
- Electric Range by Model Year (box plots showing temporal trends)
- BEV vs. PHEV comparative range analysis

### Machine Learning Pipeline
All models were built using `scikit-learn` with standardized preprocessing via `ColumnTransformer` and `Pipeline`:

| Technique | Category | Purpose |
|-----------|----------|---------|
| **Logistic Regression** | Classification | Classify vehicles by EV type (BEV vs. PHEV) |
| **Decision Tree Classifier** | Classification | Interpretable classification of EV type |
| **Random Forest Classifier** | Ensemble Classification | Robust, high-accuracy EV type prediction |
| **Linear Regression** | Regression | Model the relationship between vehicle features and electric range |
| **K-Means Clustering** | Unsupervised Learning | Discover natural market segments within the EV population |

**Preprocessing components:** `OneHotEncoder` (categorical features), `StandardScaler` (numerical features), `train_test_split` (80/20 stratified split)

**Evaluation metrics:** `classification_report` (precision, recall, F1), `mean_squared_error`, `r2_score`

---

## Key Findings

1. **Data quality matters** — Records with an electric range of zero did not represent real-world vehicle capabilities; removing them eliminated significant distributional distortion and improved model reliability.
2. **Outlier impact** — A single vehicle (Porsche 918 Spyder, ~$845K MSRP) compressed the visual and statistical scale of the entire dataset, demonstrating the importance of outlier-aware preprocessing.
3. **BEV vs. PHEV separation** — Battery Electric Vehicles consistently exhibited higher electric ranges than Plug-in Hybrids, with clear separation visible in distribution plots and confirmed by classification models.
4. **Range improvement over time** — Box plots of electric range by model year revealed a steady upward trend, reflecting advancements in battery technology and manufacturer investment in longer-range EVs.
5. **Natural market segments** — K-Means clustering identified distinct groupings within the EV population, suggesting natural market tiers based on range, pricing, and vehicle type.

---

## Skills Demonstrated

- **Data Wrangling** — Cleaning, transforming, and preparing real-world government data for analysis
- **Exploratory Data Analysis** — Statistical summarization and multi-dimensional visualization
- **Data Visualization** — Publication-quality plots using Matplotlib and Seaborn (histograms, KDE, scatterplots, box plots)
- **Machine Learning** — End-to-end supervised classification and regression pipelines with scikit-learn
- **Unsupervised Learning** — K-Means clustering for market segmentation
- **Feature Engineering** — Encoding, scaling, and pipeline construction with `ColumnTransformer`
- **Outlier Detection & Handling** — Statistical identification and principled removal of anomalous records
- **Critical Thinking** — Iterative analysis with data quality checks at each stage

---

## Repository Structure

Nicholas-Rodriguez-Showcase/
├── Data/

│   └── Sample of Electric_Vehicle_Population_Data.csv

├── Images

├── Notebooks/

│   ├── Understanding the Electric Vehicle Landscape in the State of Washington Code /

│       └── README.md ← You are here

│       └── code.ipynb

├── docs

---

## How to Run the Notebook

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Installation

# Clone the repository
git clone https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase.git
cd Nicholas-Rodriguez-Showcase

# Install required packages
pip install pandas numpy seaborn matplotlib scikit-learn jupyter

# Launch Jupyter and open the notebook
jupyter notebook "Notebooks/Understanding the Electric Vehicle Landscape in the State of Washington Code.ipynb"

Then runs all cells sequentially (Cell → Run All) to reproduce the analysis, visualizations and model outputs.
