
# Data Warehouse and Analytics Project

Welcome to the **Data Warehouse and Analytics Project** repository! 🚀  
This project demonstrates a comprehensive data warehousing and analytics solution, from building a data warehouse to generating actionable insights. Designed as a portfolio project, it highlights industry best practices in data engineering and analytics.

---
## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:
![Data Architecture](docs/data_architecture.png)

1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV Files into SQL Server Database.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.

---
## 📖 Project Overview

This project involves:

1. **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture **Bronze**, **Silver**, and **Gold** layers.
2. **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.
3. **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.
4. **Analytics & Reporting**: Creating SQL-based reports and dashboards for actionable insights.

🎯 This repository is an excellent resource for professionals and students looking to showcase expertise in:
- SQL Development
- Data Architect
- Data Engineering  
- ETL Pipeline Developer  
- Data Modeling  
- Data Analytics  

---

## 📂 Project Structure & Documentation

To make it easy to navigate the project, I have organized the repository into clear sections. You can explore the technical details, code, and visualizations through the links below:

### 1. 📖 [Documentation](./docs/)
This folder contains the complete technical breakdown of the project:
* **[Data Pipeline](./docs/data_pipeline.md)**: Detailed explanation of the Medallion Architecture (Bronze ➡️ Silver ➡️ Gold).
* **[Data Modeling](./docs/data_modeling.md)**: Insights into the Star Schema design and entity relationships.
* **[Data Dictionary](./docs/data_dictionary.md)**: Full reference for all tables and columns in the Gold layer.

### 2. 📜 [SQL Scripts](./script/)
Direct access to the T-SQL scripts used for data transformation:
* **[Bronze Layer](./script/bronze/)**: Raw data ingestion scripts.
* **[Silver Layer](./script/silver/)**: Data cleansing and standardization logic.
* **[Gold Layer](./script/gold/)**: Business logic, aggregations, and Star Schema creation.

### 3. 🖼️ [Project Visualizations](./Images/)
A collection of diagrams and screenshots showcasing the project's technical depth:
* **Architecture Diagrams**: High-level system flow and Medallion layers.
* **Data Models**: Entity Relationship Diagrams (ERD) and Star Schema.
* **Data Integration**: Visual mapping between CRM and ERP systems.

### 4. 🧪 [Testing & Validation](./tests/)
* Scripts and queries used to ensure data integrity and validate that the numbers in the Gold layer match the business requirements.

### 📊 [Datasets](datasets/)
* The raw source files (CSV) from CRM and ERP systems used in this project.

---

## 🚀 Project Requirements

### Building the Data Warehouse (Data Engineering)

#### Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

#### Specifications
- **Data Sources**: Import data from two source systems (ERP and CRM) provided as CSV files.
- **Data Quality**: Cleanse and resolve data quality issues prior to analysis.
- **Integration**: Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Scope**: Focus on the latest dataset only; historization of data is not required.
- **Documentation**: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

---

### BI: Analytics & Reporting (Data Analysis)

#### Objective
Develop SQL-based analytics to deliver detailed insights into:
- **Customer Behavior**
- **Product Performance**
- **Sales Trends**

These insights empower stakeholders with key business metrics, enabling strategic decision-making.  


## 📂 Repository Structure

```text
SQL-data-warehouse-project/
│
├── 📊 data sets/           # Raw source files from CRM and ERP systems (CSV)
│   ├── CRM/                # Customer Relationship Management datasets
│   └── ERP/                # Enterprise Resource Planning datasets
│
├── 📑 docs/                # Full Technical Documentation & Analysis
│   ├── data_pipeline.md    # Detailed Medallion Architecture flow
│   ├── data_modeling.md    # Star Schema design & relationships
│   └── data_dictionary.md  # Detailed field descriptions and metadata
│
├── 🖼️ images/              # Project diagrams and architecture visuals
│   ├── etl.drawio          # ETL techniques and methods diagram
│   ├── data_flow.png       # Visual flow from Source to Gold layer
│   └── data_models.png     # Star Schema & ERD visualizations
│
├── 📜 script/              # T-SQL scripts for ETL & transformations
│   ├── bronze/             # Ingestion: Raw data loading scripts
│   ├── silver/             # Transformation: Cleaning & standardization
│   └── gold/               # Analytics: Final Star Schema & views creation
│
├── 🧪 tests/               # SQL scripts for data quality and validation
│
└── 📋 README.md            # Project overview, tools, and navigation guide

```
