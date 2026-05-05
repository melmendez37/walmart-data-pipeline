# Walmart Holiday Sales Data Pipeline (Python + Pandas)

## Overview
Walmart is the largest retail store in the United States, with a significant portion of its revenue coming from its growing e-commerce segment. One of the key factors influencing sales is public holidays such as the Super Bowl, Labor Day, Thanksgiving, and Christmas.

This project focuses on building a simple data pipeline to clean, merge, and analyze Walmart sales data in relation to holiday and economic factors.

---

## Objective
The goal of this project is to:
- Build a data pipeline using Python and Pandas
- Merge sales and external economic datasets
- Clean and transform raw data into an analysis-ready format
- Perform exploratory analysis on monthly sales trends
- Export cleaned and aggregated datasets for reporting

---

## Datasets

### 1. grocery_sales (PostgreSQL table)
Contains weekly sales data per store.

**Columns:**
- `index` – unique row ID
- `Store_ID` – store number
- `Date` – week of sales
- `Weekly_Sales` – sales for the given store

---

### 2. extra_data.parquet
Contains external factors affecting sales.

**Columns:**
- `IsHoliday` – 1 if holiday week, 0 otherwise
- `Temperature` – regional temperature
- `Fuel_Price` – fuel cost
- `CPI` – consumer price index
- `Unemployment` – unemployment rate
- `MarkDown1–4` – promotional markdowns
- `Dept` – department number
- `Size` – store size
- `Type` – store type

---

## Data Pipeline Steps

### 1. Data Extraction
- Load `grocery_sales` table from PostgreSQL
- Load `extra_data.parquet` using Pandas

### 2. Data Merging
- Merge both datasets on relevant keys (Store_ID, Date/Week alignment)

### 3. Data Cleaning & Transformation
Create a cleaned dataset (`clean_data`) containing:

- `Store_ID`
- `Month` (extracted from Date)
- `Dept`
- `IsHoliday`
- `Weekly_Sales`
- `CPI`
- `Unemployment`

Handle:
- missing values
- incorrect data types
- column formatting

---

### 4. Aggregation Analysis
Compute monthly sales trends:

`agg_data` output:

| Month | Weekly_Sales |
|-------|-------------|
| 1.0   | 33174.18    |
| 2.0   | 34333.33    |
| ...   | ...         |

---

### 5. Export Results
Save final outputs as CSV files:
- `clean_data.csv`
- `agg_data.csv`

---

## Tools Used
- Python
- Pandas
- PostgreSQL
- Parquet file handling

---

## Key Skills Demonstrated
- Data pipeline development
- Data merging from multiple sources
- Feature engineering (date → month extraction)
- Data cleaning and transformation
- Groupby aggregation analysis
- Exporting structured datasets

---

## Output Files
- `clean_data.csv` – cleaned, analysis-ready dataset
- `agg_data.csv` – monthly aggregated sales report

---

## Business Insight Goal
This analysis helps understand how:
- holidays affect retail demand
- external economic factors influence sales
- monthly trends can guide inventory and supply planning
