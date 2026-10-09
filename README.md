# Customer Churn Analysis

This project analyzes customer churn using a subscription dataset and a Jupyter notebook workflow. It combines customer, subscription, and support data to identify churn drivers, calculate key retention metrics, and explore churn behavior by plan and geography.

## Project Overview

The analysis is implemented in the notebook:

- `churn_analysis.ipynb`

The project also includes:

- `customer_churn.db` - SQLite database with the raw tables used for the analysis
- `exported_churn_data.csv` - final merged dataset exported after preprocessing and feature engineering
- `Data Analytics Project -Churn Analysis Report.pdf` - report summary (if available in the workspace)

## Objectives

- Measure overall churn and retention rates
- Explore churn by plan type and contract type
- Understand customer behavior by state and region
- Review complaint/support activity and customer satisfaction trends
- Prepare a merged customer-level dataset for business analysis

## Data Sources

The notebook loads multiple tables from the SQLite database and merges them into a single analytical dataset.

Key fields in the final data include:

- `customerid`
- `subscription_start_date`
- `renewal_date`
- `plan_type`
- `contract_type`
- `cancellation_date`
- `cancellation_reason`
- `monthly_charges`
- `cltv`
- `churn_score`
- `churn_flag`
- `customer_name`
- `country`
- `state`
- `gender`
- `dob`
- `complaint_date`
- `escalations`
- `csat_score`
- `complaint_count`

## Workflow

The notebook performs the following steps:

1. Connects to the SQLite database and reads the tables
2. Inspects table schemas and columns
3. Cleans customer data:
   - renames fields
   - drops low-value columns
   - standardizes gender labels
   - fills missing country values based on state mapping
   - converts date fields to datetime
4. Prepares support data:
   - converts complaint dates
   - removes unnecessary columns
   - creates complaint counts per customer
5. Creates a `churn_flag` based on whether a cancellation date exists
6. Merges customer, subscription, and support tables into one dataset
7. Exports the merged dataset to `exported_churn_data.csv`
8. Calculates churn and retention KPIs
9. Analyzes churn by plan and state

## How to Run

### Option 1: Jupyter Notebook

1. Open the project folder in VS Code or your preferred Python environment.
2. Start Jupyter:

```bash
jupyter notebook
```

3. Open `churn_analysis.ipynb`.
4. Run all cells from top to bottom.

### Option 2: VS Code Notebook

- Open the `.ipynb` file in VS Code.
- Use the built-in Python/Jupyter support to run the notebook cells sequentially.

## Required Python Libraries

The notebook uses:

```bash
pandas
numpy
matplotlib
seaborn
sqlite3
```

If needed, install them using:

```bash
pip install pandas numpy matplotlib seaborn
```

## Notes

- The dataset is already bundled in the workspace, so no external download is required.
- The notebook creates a final merged file for analysis and can be rerun to regenerate the CSV export.
- The churn logic is driven by the `cancellation_date` field, where a non-null value indicates churn.

## Expected Analysis Output

The notebook focuses on business metrics such as:

- Churn rate
- Retention rate
- Churn rate by plan type
- Churn rate by state
- Complaint impact and support-related behavior

## Repository Structure

```text
Churn_data_analysis_project/
├── churn_analysis.ipynb
├── customer_churn.db
├── exported_churn_data.csv
├── Data Analytics Project -Churn Analysis Report.pdf
├── README.md
└── .gitignore
```

## Summary

This project is a practical churn analysis workflow that blends SQL data extraction, Python data cleaning, feature engineering, and business reporting. It is suitable for learning customer retention analysis and exploratory data analysis in a subscription business context.
