# White House WAVES Access Records Analysis (2023)

[![Jupyter Notebook](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/Understanding%20the%20Electric%20Vehicle%20Landscape%20in%20the%20State%20of%20Washington/code.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Executive Summary

The White House publishes WAVES (Workers and Visitors Entry System) Access Records as part of its transparency initiative. While the raw data is extensive, meaningful insights require 
structured cleaning, aggregation, and visualization.

This project analyzes 12 months of WAVES Access Records from 2023, representing the most complete and recent year available. The analysis focuses on:
- Visitor volume and patterns
- Recurring vs. one‑time visitors
- Meeting locations
- Temporal trends (daily, monthly, cumulative)
- Identification of high‑frequency visitors
  
The result is a clear, data‑driven narrative about visitor behavior at the White House and associated executive buildings.

---

## Dataset Overview

### Source Files
The dataset consists of 12 CSV files, one for each month of 2023:
2023.01_WAVES-ACCESS-RECORDS.csv
2023.02_WAVES-ACCESS-RECORDS.csv
...
2023.12_WAVES-ACCESS-RECORDS.csv

### Rows Loaded
- 843,216 total records
- 99,352 unique visitors (UIN)
- 95,646 recurring visitors
  
This means 96% of all visitors in 2023 visited more than once, indicating a highly operational, staff‑heavy dataset rather than public tours.

---

### Data Preparation & Cleaning

1. File Loading
All 12 monthly files were loaded using pathlib and concatenated into a single DataFrame.
2. Datetime Conversion
The following columns were parsed into proper datetime objects:
- Appointment Made Date
- Appointment Start Date
- Appointment End Date
3. Temporal Features
Extracted:
- year
- month (as a Period object)
4. Recurring Visitor Identification
Visitors were grouped by UIN:

visit_counts = full.groupby("UIN").size()
full["visit_count"] = visit_counts
full["is_recurring"] = full["visit_count"] > 1


5. Subset for Recurring Visitors
A dedicated recurring DataFrame was created for deeper analysis.

---

### Visualizations & Insights

1. Top 10 Recurring Visitors (Bar Chart)

A bar chart highlights the individuals with the highest number of visits in 2023.

Insight:
A small number of individuals appear extremely frequently, consistent with staff, contractors, or operational personnel.

3. One‑Time vs. Recurring Visitors (Column Chart)

A comparison of unique visitors:
- Recurring: 95,646
- One‑time: 3,706
  
Insight:
The overwhelming majority of visitors are recurring, suggesting the dataset reflects daily operations, not public access.

3. Monthly Recurring Visits by Meeting Location (Stacked Bar Chart)

Meeting locations were mapped from acronyms:

| Acronym | Full Name | 
| OEOB | Old Executive Office Building | 
| EEOB | Eisenhower Executive Office Building | 
| WH | White House | 
| ITR | In-Town Residence | 
| VPR | Vice President's Residence | 
| NEOB | New Executive Office Building | 


Insight:
- OEOB and EEOB dominate visit volume.
- The White House itself has fewer recurring visits, consistent with higher security and more selective access.

4. Daily Recurring Visits by Location (Scatterplot Grid)

A FacetGrid scatterplot shows daily visit counts for each location.

Insight:
- Strong weekday patterns
- Some locations show periodic spikes, likely tied to recurring meetings or operational cycles

5. Monthly Volume of Recurring Visits (Line Chart)

A line chart of total recurring visits per month.

Insight:
- Clear monthly fluctuations
- Some months show elevated activity, possibly tied to legislative cycles, budget deadlines, or seasonal operations

6. Cumulative Distinct Recurring Visitors (Step Chart)

A step chart showing the cumulative count of new recurring visitors over time.

Insight:
- Steady onboarding of new recurring visitors throughout the year
- No abrupt jumps, suggesting consistent operational staffing patterns

---

## Interpretation & Narrative
This analysis reveals a White House visitor ecosystem dominated by recurring operational personnel, not one‑time guests. The data suggests:
- Executive Office Buildings (OEOB, EEOB) handle the bulk of recurring activity
- The White House itself sees fewer recurring visitors, consistent with its role
- Daily and monthly patterns reflect structured government operations
- Cumulative visitor growth is steady and predictable
These insights help transform raw transparency data into a meaningful operational picture of White House activity.

---

## Assumptions
- UIN uniquely identifies a visitor
- Missing or malformed dates were safely coerced to NaT
- Meeting location acronyms were mapped correctly
- Recurring visitors are defined strictly as visit_count > 1
- The dataset reflects all WAVES entries for 2023

---

## How to Run the Notebook

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Install Required Packages
pip install pandas numpy matplotlib seaborn jupyter

### Execution
jupyter notebook

### Run all cells sequentially to reproduce:
- File loading
- Cleaning
- Recurring visitor identification
- Visualizations
- Interpretations



