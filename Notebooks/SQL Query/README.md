---

# SQLite Employee Database — Technical-Guide Demonstration

[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://github.com/NicholasJRodriguez/Nicholas-Rodriguez-Showcase/blob/main/Notebooks/SQL%20Query/Demonstrated%20SQL%20Query.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
---

## Executive Summary

This project provides a clear, instructional demonstration of how to use IPython SQL Magic to create, populate, and query a SQLite database directly inside a Jupyter Notebook. The notebook walks through initializing a database, defining a relational schema, inserting records, resolving common SQL errors, and returning query results as Pandas DataFrames. The workflow is intentionally minimal, transparent, and reproducible—ideal for learners or analysts integrating SQL into Python-based environments.
Project Overview

---

## Project Overview

| Item        | Details |
|------------------|--------|
| **Author**       | Nicholas Rodriguez |
| **Language**     | Python (Jupyter Notebook) |
| **Data Source**   | SQLite (employees.db) |
| **Primary Goal** | Demonstrate SQL table creation, data insertion, and querying using IPython SQL Magic|
| **Design** | Clarity, transparency, reproducibility, and step-by-step instructional flow |

## Dataset Description

| Feature  | Description  | 
|------------------|--------|
| Table | employees | 
| Source | Created in notebook using SQL Magic | 
| Purpose | Store sample employee records for demontrations of queries | 
| Granularity | One row per employee | 


## Schema

| Column | Type | Description | 
|------------------|--------|--------|
| id | INTEGER PRIMARY KEY | Auto incrementing unique identifier | 
| name | TEXT | Employee name | 
| career | TEXT | Job title | 
| salary | INETGER | Annual salary | 



# Methods & Techniques
## SQL Magic Initialization
- Loaded the %sql extension to enable SQL execution inside notebook cells.
- Connected to a local SQLite database using:
%sql sqlite:///employees.db


## Table Creation
- Dropped any existing employees table to ensure a clean environment.
- Created a new table with four columns: id, name, career, salary.
  
## Data Insertion
- Demonstrated a common SQL error:
“3 values for 4 columns”
caused by specifying the id column without providing a value.
- Corrected the insertion by allowing SQLite to auto-generate the primary key:
INSERT INTO employees (name, career, salary) VALUES (...);


## Query Execution
- Queried employees with salaries above $50,000.
- Returned results as a Pandas DataFrame using:
%config SqlMagic.autopandas = True



## Key Findings
- **SQL Magic enables seamless SQL execution** inside Jupyter without external database tools.
- **SQLite auto-increment behavior** simplifies table population when primary keys are omitted.
- **Operational errors are instructive**—the notebook demonstrates how column/value mismatches occur and how to resolve them.
- **Query results integrate cleanly with Pandas**, enabling downstream analysis or visualization.
- **The workflow is fully reproducible**, allowing the database to be recreated from scratch by running all cells.

## Skills Demonstrated
- SQL schema design and table creation
- Data insertion and constraint handling
- Query construction and filtering
- Debugging SQL operational errors
- Python–SQL interoperability
- Notebook-based instructional documentation
- Reproducible analytical workflow design

# Repository Structure
Nicholas-Rodriguez-Showcase/

Notebooks/

├── SQL Query/

│   └── Demonstrated SQL QUery.ipynb          # Main demonstration notebook
│   └──  README.md             # Technical guide (this file)

# How to Run the Notebook
## Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab
## Install Required Packages
pip install ipython-sql sqlalchemy pandas jupyter


# Execution
## Launch Jupyter
jupyter notebook


Open notebook.ipynb and run all cells sequentially (Cell → Run All) to recreate the database, insert records, and execute SQL queries.
