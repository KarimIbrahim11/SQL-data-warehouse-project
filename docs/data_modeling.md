# 📉 Data Modeling Documentation (Sales Data Mart)

This document explains the design and implementation of the **Sales Data Mart** in the **Gold Layer**. The model is built using a **Star Schema** to provide a high-performance environment for business intelligence and analytical reporting.

---

## 🏗️ Schema Design: Star Schema
The final data model is organized into a central **Fact Table** surrounded by **Dimension Tables**. This design optimizes query performance and simplifies data exploration in tools like Power BI.

### 1. Fact Table: `gold.fact_sales`
The core of the data mart, containing quantitative transactional data.
- **Grain:** Individual Transaction Level (One row per product per order).
- **Key Metrics:** - `sales_amount`: The total value of the transaction.
    - `quantity`: Number of units sold.
    - `price`: Unit price of the product.
- **Keys:** - `order_number`: The business identifier for the sale.
    - `product_key` & `customer_key`: Surrogate keys linking to dimensions.

### 2. Dimension Tables
#### 👤 `gold.dim_customer` (Unified Customer Profile)
Integrates customer data from both **CRM** and **ERP** systems.
- **Attributes:** `first_name`, `last_name`, `gender`, `birthdate`, `country`.
- **Purpose:** Allows analysis of sales by customer demographics and geography.

#### 📦 `gold.dim_product` (Enriched Product Catalog)
Combines product details with categories and cost information.
- **Attributes:** `product_name`, `category_id`, `subcategory`, `maintenance_cost`, `product_line`.
- **Purpose:** Enables performance tracking across different product lines and categories.

---

## 🧠 Advanced Modeling Decisions

### 🗝️ 1. Surrogate Keys Implementation
We utilized **Surrogate Keys** (`customer_key`, `product_key`) as Primary Keys in the Gold layer.
- **Why?** To decouple the Data Warehouse from source system changes (Business Keys) and to handle any potential ID overlaps between the CRM and ERP systems.

### 🔗 2. Data Integration (CRM + ERP Merging)
The project successfully bridges two isolated data sources:
- **Challenge:** Customer identity was in CRM, while additional attributes like "Birthdate" and "Location" were in ERP.
- **Solution:** We performed a data merging strategy during the transformation process, linking `crm_cust_info` with `erp_cust_az12` and `erp_loc_a101` to create a **360-degree view** of the customer.

### 📏 3. Data Integrity & Relationships
- **Cardinality:** **One-to-Many (1:N)** relationships between Dimensions and the Fact table.
- **Referential Integrity:** Enforced using **Primary Keys (PK)** and **Foreign Keys (FK)** constraints in SQL Server to ensure data consistency.

---

## 🛠️ Tools & Methodology
- **Design:** Created using **DrawIO** for ERD visualization.
- **Logic:** Transformation scripts written in **T-SQL** using Stored Procedures.
- **Architecture:** Following the **Medallion Architecture** (Bronze ➡️ Silver ➡️ Gold).

---

*Note: This data model is designed to be "Consumer-Ready", meaning it is optimized for direct connection to Power BI for building interactive dashboards.*
