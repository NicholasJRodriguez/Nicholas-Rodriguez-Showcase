
---

# National Database of Childcare Prices — Technical-Guide Analysis

[![Notebook](https://img.shields.io/badge/Notebook-HTML-blue?logo=jupyter)](https://nicholasjrodriguez.github.io/Nicholas-Rodriguez-Showcase/Notebooks/National%20Database%20of%20Childcare%20Prices%20Analysis/National%20Database%20of%20Childcare%20Prices%20Analysis-Copy1.html)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/National%20Database%20of%20Childcare%20Prices%20Analysis/National%20Database%20of%20Childcare%20Prices%20Analysis.ipynb)
---

## Executive Summary

This project presents a clear, accessible analysis of the National Database of Childcare Prices (NDCP), a comprehensive federal dataset capturing childcare cost data across all 50 U.S. states, the District of Columbia, and Puerto Rico. Through data cleaning, descriptive statistics, and carefully designed visualizations grounded in Gestalt design principles, this analysis reveals the financial burden of center-based childcare by age group and tracks cost trends over time. The work is designed to serve the general population's understanding of childcare economics while maintaining transparency.

---

## Project Overview

| Item        | Details |
|------------------|--------|
| **Author**       | Nicholas Rodriguez |
| **Language**     | Python (Jupyter Notebook) |
| **Data Source**   | National Database of Childcare Prices (NDCP), 2022 Release |
| **Primary Goal** | Analyze and visualize center-based childcare costs across the United States by age group and over time, making federal pricing data accessible and interpretable |
| **Design** | Gestalt Principles — consistency, conciseness, clarity, transparency, and trust |

---

## Dataset Description

| Feature | Description |
|---------|-------------|
| **File** | `NDCP2022.xlsx` |
| **Source** | U.S. Department of Labor — National Database of Childcare Prices |
| **Coverage** | All 50 states, District of Columbia, and Puerto Rico (52 unique jurisdictions) |
| **Granularity** | County-level childcare pricing data across multiple study years |

### Key Variables

| Variable | Description |
|----------|-------------|
| `STATE_NAME` | U.S. state or territory name (52 unique values) |
| `STUDYYEAR` | Year of data collection for time series analysis |
| `MCINFANT` | Median weekly price for center-based infant care (ages 0–23 months) |
| `MCTODDLER` | Median weekly price for center-based toddler care (ages 24–35 months) |
| `MCPRESCHOOL` | Median weekly price for center-based preschooler care (ages 36–60 months) |

---

# Methods & Techniques

### Data Cleaning & Preprocessing
- **Column name standardization** — Stripped leading and trailing whitespace from all column headers to prevent silent key mismatches
- **Duplicate removal** — Identified and dropped duplicate rows to ensure analytical integrity
- **String normalization** — Stripped whitespace from all string-type columns for consistent grouping and filtering
- **Empty column removal** — Dropped columns containing no data to streamline the working dataset

### Exploratory Data Analysis
- Descriptive statistics across all pricing variables
- State-level aggregation to compute national averages by age group
- Year-over-year trend analysis using `STUDYYEAR` as the temporal dimension

### Visualization Design (Gestalt Principles)
All visualizations were designed with intentional adherence to Gestalt design principles to maximize clarity and audience trust here are two examples from the analysis:

| Visualization | Type | Purpose |
|---------------|------|---------|
| **National Average Weekly Childcare Costs by Age Group** | Grouped bar chart | Compare the relative cost of infant, toddler, and preschool care at the national level |
| **Childcare Costs Over Time** | Stacked bar chart | Reveal how total weekly childcare cost burden has changed year over year, with each age group's contribution visible |

**Design details:**
- Consistent RGB color encoding (Red = Infant, Green = Toddler, Blue = Preschool) applied across all charts
- Dollar-formatted y-axis labels using `matplotlib.ticker` for immediate interpretability
- Clear axis titles, legends, and annotations to minimize cognitive load

---

## Key Findings

1. **Infant care is the most expensive** — Across all states and years, center-based infant care (ages 0–23 months) consistently carries the highest median weekly price, reflecting the higher staff-to-child ratios and specialized care requirements for this age group.
2. **Costs decrease with age** — A clear cost gradient exists: infant care > toddler care > preschool care, holding across virtually all jurisdictions in the dataset.
3. **Year-over-year cost increases** — The stacked bar chart reveals a steady upward trend in total weekly childcare costs over time, with all three age groups contributing to the rising burden.
4. **Nationwide coverage** — The dataset spans all 50 states, the District of Columbia, and Puerto Rico, enabling truly national-level conclusions about childcare affordability.
5. **Cumulative burden visibility** — The stacked visualization makes the combined weekly cost of multi-child or multi-age-group care immediately apparent, underscoring the financial pressure on working families.

---

## Skills Demonstrated

- **Data Wrangling** — Cleaning and standardizing a federal Excel dataset for analytical use
- **Exploratory Data Analysis** — Descriptive statistics and aggregation across geographic and temporal dimensions
- **Data Visualization** — Purpose-driven chart design using Matplotlib with Gestalt design principles
- **Design Thinking** — Intentional application of consistency, conciseness, clarity, transparency, and trust in all visual outputs
- **Domain Communication** — Translating complex federal data into accessible, audience-appropriate insights
- **Analytical Transparency** — Clear documentation of every cleaning step, design choice, and analytical decision
- **Time Series Analysis** — Tracking and visualizing cost trends across multiple study years

---

## Repository Structure

Nicholas-Rodriguez-Showcase/

├── Data/

│   └── Sample of NDCP2022.xlsx

├── Images

├── Notebooks/

│   ├── National Database of Childcare Prices Analysis/

│       └── README.md ← You are here

│       └── National Database of Childcare Prices Analysis.ipynb

├── docs

---
# How to Run the Notebook

## Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

# How to Run

## Clone the repository
git clone https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase.git
cd Nicholas-Rodriguez-Showcase

## Install required packages
pip install pandas matplotlib openpyxl jupyter

> **Note:** 'openpyxl' may be a needed package to read he '.xlsx' file


# Execution

## Navigate to the project folder and launch Jupyter
cd "Notebooks/National Database of Childcare Prices Analysis"
notebook code is .ipynb

Then run all cells sequentially (Cell → Run All) to reproduce the analysis, visualizations and model outputs.
