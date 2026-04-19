# 🚀 Data Pipeline Documentation (Medallion Architecture)

This document details the technical implementation of the data pipeline for the **SQL Data Warehouse Project**. The pipeline follows the **Medallion Architecture**, automating the flow from raw CSV files to a business-ready **Star Schema**.

---

## 🏗️ High-Level Architecture
The system architecture consists of three main stages hosted on **SQL Server**:

1. **Source:** Flat files (CSV) from CRM and ERP systems.
2. **Data Warehouse (SQL Server):** Organized into Bronze, Silver, and Gold layers using **Stored Procedures**.
3. **Consume:** Final data is consumed via Power BI (Reporting), Ad-hoc SQL queries, and potentially Machine Learning models.

---

## 📥 1. Bronze Layer (Raw Data)
- **Objective:** Ingest raw data from source folders into SQL tables without any modification.
- **Process:** Automated via **Stored Procedures** using `Truncate & Insert` logic to ensure a fresh full load.
- **Tables:**
    * `crm_sales_details`, `crm_cust_info`, `crm_prd_info`
    * `erp_cust_az12`, `erb_loc_a101`, `erb_px_cat_g1v2`
- **Data Model:** None (As-is from source).

---

## 🧹 2. Silver Layer (Cleaned & Standardized)
- **Objective:** Transform raw data into high-quality, normalized tables.
- **Transformations Applied:**
    * **Data Cleansing:** Handling null values and removing duplicates.
    * **Standardization:** Unifying date formats and currency symbols.
    * **Data Enrichment:** Deriving new columns to add more context.
    * **Data Normalization:** Preparing tables for the final Star Schema.
- **Automation:** Driven by **Stored Procedures** to ensure consistency in every run.

---

## 🏆 3. Gold Layer (Business-Ready / Data Mart)
- **Objective:** Deliver curated data for analytics using a **Star Schema** design.
- **Data Model (Sales Data Mart):**
    * **Fact Table:** `gold.fact_sales` (Contains transactional data like quantity, price, and sales amount).
    * **Dimension Tables:** * `gold.dim_customer` (Unified customer data from CRM & ERP).
        * `gold.dim_product` (Combined product categories and details).
- **Techniques:**
    * **Data Integration:** Merging CRM and ERP records (e.g., combining customer info with location and birthdates).
    * **Aggregations:** Business logic and KPIs pre-calculated for reporting.
    * **Modeling:** Designed for high performance using **Primary Keys (PK)** and **Foreign Keys (FK)**.

---

## 🔗 Data Integration Logic
The pipeline successfully bridges the gap between two isolated systems:
- **Customer Integration:** Links `crm_cust_info` (cst_id) with `erp_cust_az12` (cid) and `erp_loc_a101` to build a 360-view of the customer.
- **Product Integration:** Links `crm_prd_info` (prd_key) with `erp_px_cat_g1v2` (id) to enrich product details with categories.

---

## 🛠️ Technical Stack
- **Database Engine:** SQL Server Express.
- **ETL Logic:** T-SQL Stored Procedures.
- **Design Tools:** DrawIO (Architecture & ERD).
- **Data Source:** CSV Files.
