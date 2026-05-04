# Pokémon Data Transformation & Integration — Technical‑Guide Analysis
Jupyter Notebook

License: MIT

Executive Summary
This project demonstrates a complete, multi‑source data engineering workflow using Pokémon as a pop‑culture dataset. The analysis integrates three independent data sources:
- A CSV dataset containing Pokémon attributes
- A web‑scraped dataset from Serebii.net containing Generation 1 base stats
- A live API dataset from PokeAPI containing names, types, and stats
Across these sources, the notebook performs:
- Data cleaning
- Schema standardization
- HTML parsing
- API extraction
- Normalization
- Outlier detection
- Type‑based aggregation
- Visualization
- SQLite database creation
The result is a unified, analysis‑ready dataset suitable for statistical exploration, visualization, and machine learning workflows.

Project Overview
|  |  | 
|  |  | 
|  |  | 
|  |  | 
|  |  | 
|  |  | 



Datasets Used
1. CSV Dataset (pokemon.csv)
|  |  | 
|  |  | 
|  |  | 
|  |  | 



2. HTML‑Scraped Dataset (Serebii.net)
|  |  | 
|  |  | 
|  |  | 
|  |  | 
|  |  | 



3. PokeAPI Dataset
|  |  | 
|  |  | 
|  |  | 
|  |  | 



Methods & Techniques
Data Cleaning & Preprocessing
- Standardized column names across datasets
- Removed unnecessary fields (abilities, classification, japanesename)
- Filled missing values (numeric → 0, string → "Unknown")
- Normalized stat values using Min‑Max scaling
- Converted Pokémon numbers from "#0001" → 1

HTML Scraping & Parsing
- Identified stat tables using BeautifulSoup
- Extracted HP, Attack, Defense, Special Attack, Special Defense, Speed
- Filtered out irrelevant image‑only tables
- Constructed a clean DataFrame with Pokémon numbers and stats
- Calculated Combined Stat and Normalized Combined Stat

API Integration
- Queried PokeAPI for Pokémon #1–151
- Extracted:
- Name
- Primary and secondary types
- Base stats
- Normalized all stats across the full Generation 1 distribution
- Grouped Pokémon by type(s)
- Calculated average stats per type

Outlier Detection
Using Z‑scores (threshold: Z > 3):
- HP Outliers: Chansey, Snorlax
- Defense Outliers: Cloyster, Onix
- Special Attack Outlier: Mewtwo
- Speed Outlier: Electrode
Each outlier is flagged in the final dataset.

Visualization
Two major visualizations were produced:
|  |  |  | 
|  |  |  | 
|  |  |  | 



Key Findings
- Stat distributions vary widely — HP, Defense, and Speed show extreme outliers.
- Type patterns emerge clearly — Fire and Flying types trend toward higher Speed and Attack.
- Normalization reveals relative strengths — Mewtwo dominates Special Attack; Chansey dominates HP.
- HTML scraping and API data align — Cross‑validation confirms stat accuracy.
- Unified dataset enables deeper analysis — Type clustering, stat correlations, and ML modeling become possible.

Skills Demonstrated
- Data Wrangling — Cleaning, merging, and normalizing multi‑source datasets
- Web Scraping — Extracting structured data from HTML tables
- API Consumption — Parsing JSON from REST endpoints
- Statistical Analysis — Outlier detection, aggregation, normalization
- Data Visualization — Matplotlib bar charts and annotated plots
- Database Engineering — Creating and preparing SQLite tables
- Schema Design — Aligning inconsistent data sources into a unified structure
- Analytical Transparency — Clear documentation of each transformation step

Repository Structure
Nicholas-Rodriguez-Showcase/
├── Data/
│   └── pokemon.csv
├── Notebooks/
│   └── Pop Culture Data Transformation Analysis/
│       ├── Pop Culture Data Transformation Analysis.ipynb
│       └── README.md  ← Here
├── Images/
├── docs/
└── pokemon.db  ← SQLite database created from all three datasets



How to Run the Notebook
Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab
Install Required Packages
pip install pandas numpy matplotlib requests beautifulsoup4 sqlite3


Execution
cd "Notebooks/Pop Culture Data Transformation Analysis"
jupyter notebook


Run all cells sequentially to reproduce:
- CSV cleaning
- HTML scraping
- API extraction
- Normalization
- Outlier detection
- Visualizations
- SQLite database creation
