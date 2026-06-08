# Retail Sales Analytics Platform

### End-to-End Data Warehouse & Business Intelligence Solution

**SQL Server + Informatica IICS + Power BI**

---

# 📌 Project Overview

This project demonstrates the design and implementation of an end-to-end Retail Sales Analytics Platform built using:

* SQL Server
* Informatica Intelligent Cloud Services (IICS)
* Power BI

The solution follows a modern dimensional modeling approach and simulates a production-grade data warehouse environment.

The platform ingests raw retail sales data from CSV files, processes and validates data through Informatica IICS, loads dimensional and fact tables into SQL Server, and delivers interactive business insights through Power BI dashboards.

---

# 🎯 Business Objectives

The solution helps business users answer questions such as:

* How much revenue is generated?
* Which products perform best?
* Which stores generate the highest sales?
* Which customers contribute most revenue?
* What are the sales trends over time?
* Which categories drive business growth?


## 🛠️ Technology Stack

| Layer                     | Technology Used                               |
| ------------------------- | --------------------------------------------- |
| Source System             | CSV Files                                     |
| ETL Tool                  | Informatica Intelligent Cloud Services (IICS) |
| Staging Layer             | SQL Server (stg schema)                       |
| Data Warehouse            | SQL Server (dw schema)                        |
| Fact Layer                | SQL Server (fact schema)                      |
| Data Modeling             | Star Schema                                   |
| Dimensions                | SCD Type 1 & SCD Type 2                       |
| Database Objects          | Tables, Views, Keys, Constraints              |
| Orchestration             | IICS Taskflows                                |
| Data Quality              | Validation Rules & Reconciliation Checks      |
| Reporting & Visualization | Power BI Desktop                              |
| Analytics                 | DAX Measures                                  |
| Version Control           | GitHub                                        |


---

# 🏗️ Solution Architecture

Retail Source Files (CSV)

⬇

Informatica Intelligent Cloud Services (IICS)

⬇

SQL Server Data Warehouse

⬇

Power BI Analytics Dashboards

---

# 📊 Architecture Components

## Source Layer

Retail CSV Files:

* customers.csv
* products.csv
* stores.csv
* orders.csv
* order_items.csv

---

## Staging Layer (stg)

Purpose:

* Raw data ingestion
* Data standardization
* Initial validations
* Audit tracking

Tables:

* stg_customers
* stg_products
* stg_stores
* stg_orders
* stg_order_items

---

## Data Warehouse Layer (dw)

Dimensional model built using Star Schema principles.

### Dimensions

* dim_date
* dim_customer (SCD Type 2)
* dim_product (SCD Type 1)
* dim_store (SCD Type 1)

### Facts

* fact_orders
* fact_order_items

---

## Reporting Layer

Power BI semantic model built on top of SQL Server Data Warehouse.

Provides:

* Executive Reporting
* Product Analytics
* Customer Analytics
* Store Analytics
* Sales Trend Analysis

---

# 📊 Dimensional Model

## Dimension Tables

### dim_date

Static date dimension used for all time-based analysis.

### dim_customer

Slowly Changing Dimension Type 2.

Tracks historical customer changes.

Examples:

* Email changes
* Phone changes
* Address changes

Maintains:

* start_dt
* end_dt
* current_flag

---

### dim_product

Slowly Changing Dimension Type 1.

Updates overwrite existing values.

Examples:

* Product description correction
* Category updates
* Brand updates

---

### dim_store

Slowly Changing Dimension Type 1.

Stores latest store information.

---

# 🧱 Fact Tables

## fact_orders

### Grain

One row per order.

### Measures

* total_amount

### Linked Dimensions

* dim_date
* dim_customer
* dim_store

---

## fact_order_items

### Grain

One row per product per order.

### Measures

* quantity
* unit_price
* line_total

### Linked Dimensions

* dim_date
* dim_customer
* dim_product
* dim_store

---

# ❓ Why Two Fact Tables?

Separating order-level and product-level facts provides:

* Better performance
* Flexible reporting
* Reduced duplication
* Accurate aggregations

Supports:

* Sales analysis
* Product analysis
* Customer analysis
* Store performance analysis

---

# 🔄 ETL Design Using Informatica IICS

The ETL solution is organized into three layers:

## 1. Staging Layer

Loads raw CSV files.

Features:

* File validation
* Data type standardization
* Audit tracking
* Error handling

---

## 2. Dimension Layer

Loads dimensional tables.

Features:

* Surrogate key generation
* SCD Type 1 processing
* SCD Type 2 processing
* Change detection logic

---

## 3. Fact Layer

Loads fact tables.

Features:

* Dimension lookups
* Surrogate key resolution
* Referential integrity validation
* Measure calculations

---

# 🔁 Taskflow Orchestration

The project uses dependency-driven taskflows.

## Stage Layer

Parallel execution:

* stg_customers
* stg_products
* stg_stores
* stg_orders
* stg_order_items

---

## Dimension Layer

Sequential execution:

1. dim_date
2. dim_customer
3. dim_product
4. dim_store

---

## Fact Layer

Sequential execution:

1. fact_orders
2. fact_order_items

---

# ♻️ Incremental Load Strategy

Features:

* Batch-based processing
* Restartability
* Data lineage tracking
* Auditability

Batch ID format:

YYYYMMDD_HHMMSS

---

# 🕒 Audit Columns

Implemented across staging, dimensions, and facts.

* batch_id
* insert_dt
* update_dt
* load_user
* file_name
* file_row_number

---

# 🚦 Error Handling

The solution includes:

* Mandatory field validation
* Duplicate detection
* Reject handling
* Missing key validation
* Taskflow restart capability

---

# ✅ Data Validation Checks

Implemented validations:

* Row count reconciliation
* Null checks
* Duplicate checks
* Surrogate key validation
* Fact-to-dimension integrity checks

---

# 📈 Power BI Dashboards

The reporting layer contains multiple interactive dashboards.

## 1. Executive Overview Dashboard

KPIs:

* Total Revenue
* Total Orders
* Total Customers
* Average Order Value
* Total Quantity Sold

Visuals:

* Monthly Revenue Trend
* Revenue by Category
* Revenue by Store
* Payment Method Analysis
* Top Products

---

## 2. Customer Analysis Dashboard

KPIs:

* Total Customers
* Revenue Per Customer
* Average Orders Per Customer
* Highest Customer Revenue

Visuals:

* Top Customers
* Revenue by State
* Revenue by City
* Customer Distribution

---

## 3. Product Performance Dashboard

KPIs:

* Total Products
* Top Product Revenue
* Revenue Per Product
* Total Quantity Sold

Visuals:

* Revenue by Category
* Top Products by Revenue
* Top Products by Quantity
* Product Performance Table

---

## 4. Store Performance Dashboard

KPIs:

* Total Stores
* Top Store Revenue
* Revenue Per Store
* Total Quantity Sold

Visuals:

* Top Stores
* Revenue by State
* Revenue by City
* Store Performance Table

---

## 5. Navigation, Tooltips & Drillthrough

Implemented:

* Dashboard navigation buttons
* Home page navigation
* Product tooltips
* Store tooltips
* Product drillthrough pages
* Store drillthrough pages

---

# 📊 Sample Business KPIs

Implemented DAX measures include:

* Total Revenue
* Total Orders
* Total Customers
* Total Quantity Sold
* Average Order Value
* Revenue Per Customer
* Revenue Per Product
* Revenue Per Store

---

# 🚀 Skills Demonstrated

### Data Warehousing

* Star Schema Design
* Fact & Dimension Modeling
* Surrogate Keys
* Fact Grain Design

### ETL Development

* Informatica IICS
* Mapping Design
* Taskflows
* Incremental Loading
* Error Handling

### SQL Development

* Analytical Queries
* Data Validation
* Data Quality Checks
* Performance-Oriented Design

### Business Intelligence

* Power BI
* DAX Measures
* Drillthrough Reports
* Tooltips
* Interactive Dashboards

---

# 📈 Business Value

This platform enables business users to:

* Monitor revenue performance
* Analyze customer behavior
* Identify top-performing products
* Evaluate store performance
* Track operational KPIs
* Support data-driven decision making

---

# 👤 Author

**Raghukumar Kasthuri**

Data Engineer | ETL Developer | Power BI Developer

End-to-End Retail Analytics Platform using SQL Server, Informatica IICS, and Power BI.
