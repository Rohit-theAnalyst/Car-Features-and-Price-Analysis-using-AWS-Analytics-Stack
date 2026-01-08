# 🚗 Used Car Price Analysis | AWS Athena & Cloud Analytics

## Project Overview
This project presents an end-to-end data analysis workflow built entirely on AWS to analyze used car pricing patterns.  
The goal is to understand how **usage, technical specifications, and ownership attributes** impact resale prices using SQL-based analytics and cloud-native services.

The project follows a structured data lifecycle:
**Ingestion → Cleaning → Feature Engineering → Analysis → Visualization**

---

## Architecture Overview

### AWS Services Used
- **Amazon S3** – Raw and cleaned data storage
- **AWS Glue** – Data cataloging and schema discovery
- **AWS Athena** – SQL-based querying, transformation, and analytics
- **QuickSight** – Visualization connected to Athena

###  Architecture Flow
1. Raw car price dataset stored in Amazon S3
2. AWS Glue crawler scans data and creates metadata tables
3. AWS Athena queries raw data and creates cleaned, analytics-ready tables
4. Feature engineering performed using SQL (bucketing & aggregations)
5. Final insights visualized using an Athena-connected dashboard

---

##  Data Modeling & SQL Processing

### Raw Data
Raw data is stored in S3 and queried directly using Athena.

### Cleaned Data (CTAS)
A cleaned table is created using **CTAS (Create Table As Select)**:
- Removed nulls
- Standardized column types
- Stored in optimized **Parquet format**

### Feature Engineering (SQL)
Analytical buckets were created using SQL:
- Kilometers Driven Buckets
- Mileage (KMPL) Buckets
- Engine Power (BHP) Buckets

These buckets help reduce noise and improve interpretability in analysis.


## Dashboard Overview

The dashboard is divided into **three analytical layers**, each serving a distinct business purpose.

---

## Page 1 – Executive Overview

### Key Insights Shown
- Total number of cars listed
- Average car price
- Average kilometers driven
- Average mileage (KMPL)
- Fuel type distribution
- Brand-wise average price
- Overall price distribution

---

## Page 2 – Price Drivers Analysis

### Key Insights Shown
- Average price by fuel type
- Average price by transmission type
- Impact of seating capacity on price
- Ownership history vs resale price

This page answers **why prices differ** across listings.

---

## Page 3 – Usage & Depreciation Analysis

### Key Insights Shown
- Average price by kilometers driven buckets
- Average price by mileage (KMPL) buckets
- Average price by engine power (BHP) buckets
- Price trends across model years (market perspective)

Since actual car age was not available, **kilometers driven** was used as the primary proxy for usage-based depreciation.

---

## Key Business Insights
- Cars with lower usage (fewer kilometers driven) retain higher resale value
- Mid to high mileage-efficient cars (15–25 kmpl) show stronger pricing
- Higher engine power increases price, but with diminishing returns
- First-owner vehicles command a clear resale premium
- Model year reflects market pricing preference rather than physical wear

---
