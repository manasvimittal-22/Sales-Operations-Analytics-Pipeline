# Olist E-Commerce Analytics Pipeline
### End-to-End Data Analytics Pipeline | Python · SQL · PySpark · Prophet

---

## Project Overview

This project builds a fully automated, end-to-end data analytics pipeline on the **Olist Brazilian E-Commerce dataset** — a real-world dataset containing 100,000+ orders across 9 relational tables covering orders, payments, products, sellers, customers, and reviews.

The pipeline covers the full lifecycle of enterprise data analytics: ingestion, validation, transformation, KPI reporting, anomaly detection, and forecasting — mirroring the responsibilities of a data analyst working within a finance, supply chain, or operations domain.

---

## Problem Statement

E-commerce businesses generate massive volumes of operational data across orders, payments, deliveries, and sellers — but this data often sits in siloed files with no unified view. Decision-makers lack:

- A consistent KPI framework to track business health across finance and operations
- Automated data validation to catch quality issues before they corrupt reports
- A way to detect anomalies in sales and delivery patterns before they become costly
- Forward-looking insights to support operational and financial planning

---

## Solution

An automated analytics pipeline built in Python that:

1. Ingests and validates raw multi-table data with automated quality checks
2. Transforms and joins tables using SQL and Pandas into a unified analytical dataset
3. Engineers business features like delivery delay, freight ratio, and review sentiment
4. Computes a 12-KPI framework across Finance, Operations, and Customer Satisfaction
5. Detects statistical anomalies in daily revenue and delivery performance
6. Forecasts 90-day revenue using Facebook Prophet with confidence intervals

---

## Dataset

**Brazilian E-Commerce Public Dataset by Olist**
Source: [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

The dataset contains 9 relational CSV files:

| File | Description |
|---|---|
| olist_orders_dataset.csv | Core order lifecycle data |
| olist_customers_dataset.csv | Customer location data |
| olist_order_items_dataset.csv | Items, prices, and freight per order |
| olist_order_payments_dataset.csv | Payment methods and values |
| olist_order_reviews_dataset.csv | Customer review scores and comments |
| olist_products_dataset.csv | Product dimensions and categories |
| olist_sellers_dataset.csv | Seller location data |
| olist_geolocation_dataset.csv | Zip code coordinate mapping |
| product_category_name_translation.csv | Portuguese to English category names |

> Download the dataset from Kaggle and place all CSV files in the root directory before running the notebook.

---

## Project Structure

```
olist-data-analytics-pipeline/
│
├── olist_analytics_pipeline.ipynb   # Main notebook (run this)
├── README.md                        # Project documentation
└── data/
    └── README.md                    # Instructions to download dataset from Kaggle
```

---

## Pipeline Sections

### Section 1 — Data Ingestion & Validation
- Load all 9 CSV files into Pandas DataFrames
- Automated data quality checks: null values, duplicate rows, incorrect data types
- Referential integrity checks across all relational keys (order_id, product_id, seller_id, customer_id)

### Section 2 — Data Transformation & Feature Engineering
- Fix data types: convert string columns to datetime and numeric
- Clean data: handle nulls, remove duplicates, standardize text
- Build unified master analytical dataset using SQL joins via pandasql
- Engineer 11 new business features including:
  - `delivery_delay_days` — actual vs estimated delivery
  - `is_on_time` — binary on-time delivery flag
  - `freight_pct` — freight as a percentage of order value
  - `review_sentiment` — bucketed positive / neutral / negative
- PySpark transformations for delivery performance and revenue by category

### Section 3 — KPI Framework & EDA
12 KPIs across three business domains:

**Finance**
- Total Revenue
- Average Order Value (AOV)
- Monthly Revenue Trend
- Revenue by Product Category

**Operations**
- On-Time Delivery Rate
- Average Delivery Delay
- Delivery Delay Distribution
- Late Delivery Rate by State

**Customer Satisfaction**
- Review Score Distribution
- Sentiment Breakdown
- Monthly Order Volume Trend
- Orders by Day of Week

### Section 4 — Anomaly Detection
- Z-Score and IQR based anomaly detection on daily revenue
- Z-Score and IQR based anomaly detection on daily late delivery rate
- Combined flagging method (both methods must agree) to reduce false positives
- Consolidated anomaly summary report with direction (spike vs drop)

### Section 5 — Forecasting
- Facebook Prophet time-series model trained on historical daily revenue
- 90-day forward revenue forecast with 95% confidence intervals
- Trend and weekly/yearly seasonality component breakdown
- Monthly forecast rollup with business interpretation

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| Pandas | Data manipulation and transformation |
| PySpark | Distributed data transformation |
| pandasql | SQL queries on DataFrames |
| Plotly | Interactive visualizations |
| Facebook Prophet | Time-series forecasting |
| Google Colab | Development environment |

---

## Key Results

- Validated 100,000+ orders across 9 relational tables with automated quality checks
- Built a unified master dataset by joining all tables using SQL
- Computed 12 KPIs across Finance, Operations, and Customer Satisfaction domains
- Detected statistically anomalous days in both revenue and delivery performance
- Generated a 90-day revenue forecast with trend and seasonality breakdown

---

## How to Run

1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
2. Open `Sales_&_Operations_Analytics_Pipeline.ipynb` in [Google Colab](https://colab.research.google.com/)
3. Upload all 9 CSV files to the Colab session using the file browser
4. Run all cells in order from top to bottom

---

## Disclaimer

This project is made public for portfolio and educational purposes only.

**Do not plagiarize.** If you are using this project as a reference or inspiration, please credit the original author. Submitting this work — in whole or in part — as your own for job applications, assessments, academic assignments, or any other purpose without proper attribution is plagiarism.

The author (Manasvi Mittal) is not responsible for any consequences arising from the misuse of this publicly available work. By accessing this repository you agree to use it ethically and responsibly.

---

## Author

**Manasvi Mittal**

