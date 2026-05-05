
# Dodgers 2022 Promotions Attendance Analysis — Statistical Testing & OLS Modeling

[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](Notebooks/Understanding%20the%20Electric%20Vehicle%20Landscape%20in%20the%20State%20of%20Washington%20Code.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)


---

## Executive Summary

This project analyzes Los Angeles Dodgers 2022 home game attendance to determine which promotional events—Fireworks, Bobblehead giveaways, Shirts, and Caps—meaningfully increase turnout.

Using:
- Independent samples t‑tests
- OLS regression modeling
- Binary promotion indicators
- Cleaned and standardized attendance data

The analysis identifies which promotions truly drive attendance and provides actionable recommendations for Dodgers management.

---

## Dataset Overview

The dataset includes:
- Game date (month/day mapped to 2022 calendar)
- Attendance (attend)
- Promotions:
  - fireworks
  - bobblehead
  - shirt
  - cap
 
### Data Cleaning Steps
- Standardized column names
- Stripped whitespace
- Converted YES/NO to binary (1 = YES, 0 = NO)
- Created a proper date column using month/day mappings
This ensures the dataset is ready for statistical testing and regression modeling.

---

## Promotion Impact Analysis (t‑Tests)

Independent samples t‑tests compare mean attendance on promotion days vs. non‑promotion days.

### Fireworks Promotion
- Mean difference: +45 attendees
- p‑value: 0.98
- Interpretation: No statistical impact
- Recommendation: Reevaluate cost‑effectiveness

### Bobblehead Promotion
- Mean difference: +14,006 attendees
- p‑value: 0.00
- Interpretation: Extremely strong attendance driver
- Recommendation: Expand bobblehead nights, especially on low‑attendance days

### Shirt Promotion
- Mean difference: +5,819 attendees
- p‑value: 0.19
- Interpretation: Moderate increase, not statistically significant
- Recommendation: Pair shirts with other promotions (e.g., fireworks)

### Cap Promotion
- Mean difference: –2,922 attendees
- p‑value: 0.62
- Interpretation: No positive effect; may even reduce turnout
- Recommendation: Discontinue or pair with stronger promotions

---

## OLS Regression Modeling

To quantify the individual impact of each promotion while controlling for the others, an OLS model was fit:

### Model Performance
- R‑squared: 0.387
- Promotions explain 39% of attendance variation
- F‑statistic p‑value: 1.29e‑07
- Model is statistically significant overall

### Promotion Coefficients
| Promotion | Coefficient | p-value | Interpretation | 
| --- | --- | --- | --- | 
| Fireworks | +2,977 | 0.157 | Small effect | 
| Bobblehead | +14,940 | 0.000 | High effect | 
| Shirt | +8,443 | 0.036 | Moderate effect | 
| Cap | -12 | 0.998 | No effect | 


### Interpretation
- Bobbleheads dominate — nearly +15,000 attendees per game
- Shirts matter — meaningful and statistically significant
- Fireworks are weak — small, unreliable effect
- Caps do nothing — statistically indistinguishable from zero

---

## Management‑Ready Recommendations
1. Expand Bobblehead Promotions
They are the single strongest driver of attendance.
2. Increase Shirt Giveaway Nights
Shirts produce a meaningful, statistically significant boost.
3. Reevaluate Fireworks Nights
They show a small increase but lack statistical reliability.
4. Discontinue or Redesign Cap Promotions
Caps do not attract attendees and may even reduce turnout.
5. Combine Weak Promotions
Pairing fireworks or caps with shirts or bobbleheads may improve performance.

---

## Assumptions
- Attendance is influenced by promotions independently of opponent, weather, or day of week
- YES/NO promotion indicators accurately reflect giveaway nights
- Attendance is measured consistently across all games
- Promotions are assumed to be the primary variable of interest
These assumptions were necessary due to the dataset’s structure.

---

## Conclusion
This analysis reveals that:
- Bobblehead giveaways are the most effective promotion, increasing attendance by nearly 15,000 fans.
- Shirt promotions also significantly boost turnout.
- Fireworks and caps do not meaningfully influence attendance.
- A simple four‑variable model explains 39% of attendance variation, giving management a strong starting point for optimizing promotional strategy.

Actionable takeaway:
More bobbleheads and shirts. Rethink fireworks. Don't utilize caps.

---

## How to Run the Notebook

Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

## Install Required Packages
pip install pandas scipy statsmodels jupyter

## Execution
Launch Jupyter
jupyter notebook

### Run all cells sequentially to reproduce:
- Data cleaning
- Promotion impact t‑tests
- OLS regression modeling
- Interpretation and recommendations
