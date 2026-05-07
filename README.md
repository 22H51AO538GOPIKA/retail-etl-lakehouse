# retail-etl-lakehouse

## Project Overview

This project is a complete end-to-end Retail ETL Lakehouse solution developed using Databricks, SQL, and AWS S3 by following the Medallion Architecture approach.

The main goal of this project is to take raw retail data files, process them step by step through different data layers, clean and validate the data, and finally prepare analytics-ready tables that can be used for reporting and business insights.

The project simulates a real-world retail data engineering workflow where data arrives continuously from different sources and is processed in a structured and scalable manner.

---

# Architecture Used

This project follows the Medallion Architecture pattern.

```text
Raw Data
   ↓
Archive Layer
   ↓
Bronze Layer
   ↓
Silver Layer
   ↓
Gold Layer
```

Each layer has a specific responsibility in the pipeline.

---

# Technologies Used

* Databricks
* SQL
* AWS S3
* Delta Lake
* GitHub
* PySpark
* Medallion Architecture

---

# Project Folder Structure

```text
retail-etl-lakehouse/

├── archived/
│   └── archived_layer

├── bronze/
│   └── bronze_layer

├── silver/
│   ├── silver_layer
│   └── validation_layer

├── gold/
│   └── gold_layer

└── README.md
```

---

# Data Source Files

The project processes the following retail source datasets:

* customers data
* products data
* stores data
* sales transactions data

These files are initially stored in the RAW layer inside AWS S3 storage.

---

# Archive Layer

The Archive Layer is responsible for maintaining historical raw files.

### Main Responsibilities

* Keeps only the latest files in the raw location
* Moves older files into archive folders
* Prevents duplicate processing
* Maintains historical backup data
* Supports auditing and recovery

### Implemented Features

* Filename timestamp extraction
* Latest file identification
* Automatic archival process
* Timestamp-based archive folders

---

# Bronze Layer

The Bronze Layer acts as the ingestion layer of the project.

Raw CSV files are loaded directly into bronze tables without major transformations.

### Main Responsibilities

* Read raw CSV files
* Create structured bronze tables
* Preserve original source data
* Enable querying using SQL

### Bronze Tables

* customers_raw
* products_raw
* stores_raw
* sales_raw

### Implemented Features

* Schema inference
* CSV ingestion
* Raw data preservation
* Table creation using Databricks SQL

---

# Silver Layer

The Silver Layer is the data cleansing and transformation layer.

In this layer, raw data is cleaned, standardized, validated, and transformed into high-quality datasets.

### Main Responsibilities

* Remove invalid records
* Trim unnecessary spaces
* Standardize text values
* Validate business rules
* Improve data quality
* Create clean dimensional models

### Implemented Features

* Email normalization
* Proper case formatting
* Duplicate handling
* Null validations
* Data quality checks
* SCD Type 2 implementation
* Referential integrity validation

### Silver Tables

* DimCustomer
* DimProduct
* DimStore
* FactSales

---

# Gold Layer

The Gold Layer contains analytics-ready business tables.

This layer is designed for reporting, dashboards, and business intelligence purposes.

### Main Responsibilities

* Create business-ready datasets
* Generate analytical outputs
* Support KPI reporting
* Enable decision-making analysis

### Implemented Features

* Revenue analysis
* Product performance analysis
* Customer analytics
* Store-wise sales analysis
* Regional performance tracking
* Monthly sales trend analysis
* Top customer identification
* Top selling products analysis

---

# Data Quality Validation

Several validation checks were implemented across the Silver Layer to ensure data accuracy and consistency.

### Validation Areas

* Duplicate detection
* Null value checks
* SCD Type 2 validation
* Amount calculation validation
* Surrogate key validation
* Date format validation
* Referential integrity checks

---

# Key Concepts Demonstrated

This project demonstrates important real-world Data Engineering concepts such as:

* ETL Pipeline Development
* Data Lakehouse Architecture
* Medallion Architecture
* Slowly Changing Dimensions (SCD Type 2)
* Fact and Dimension Modeling
* Data Validation Techniques
* Incremental Data Handling
* Data Cleaning and Standardization
* Layer-based Data Processing
* Data Warehousing Concepts

---

# Business Use Case

The project represents a retail company data warehouse system where customer, product, store, and sales data are continuously processed to support analytics and reporting requirements.

The final processed data can be used by business teams for:

* Sales reporting
* Customer behavior analysis
* Product performance tracking
* Revenue analysis
* Regional sales comparison
* Business decision making

---

# Conclusion

This project provides a complete understanding of how modern retail ETL pipelines are designed using Medallion Architecture in a Lakehouse environment.

It covers the full lifecycle of data processing starting from raw file ingestion to cleaned analytical datasets while maintaining scalability, data quality, and historical tracking.
