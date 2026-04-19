# 📖 Data Dictionary

This document provides a detailed description of the tables and columns within the **Gold Layer** (Sales Data Mart). This layer is the final, cleaned, and business-ready version of the data.

---

## 🏗️ Schema: Gold Layer

### 1. Table: `gold.fact_sales`
This is the central fact table containing all transactional sales records.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `order_number` | NVARCHAR | The unique business identifier for each sales order. |
| `product_key` | INT | Foreign Key (FK) linking to `gold.dim_product`. |
| `customer_key` | INT | Foreign Key (FK) linking to `gold.dim_customer`. |
| `order_date` | DATE | The date when the order was placed. |
| `shipping_date` | DATE | The date when the order was shipped to the customer. |
| `due_date` | DATE | The expected date for payment or delivery completion. |
| `sales_amount` | DECIMAL | The total monetary value of the sale (Price * Quantity). |
| `quantity` | INT | The number of units sold in the transaction. |
| `price` | DECIMAL | The unit price of the product at the time of sale. |

---

### 2. Table: `gold.dim_customer`
This dimension table contains unified and cleaned customer information from CRM and ERP systems.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `customer_key` | INT (PK) | Surrogate Key (Primary Key) for the customer. |
| `customer_id` | INT | The original ID from the source CRM system (`cst_id`). |
| `customer_number`| NVARCHAR | Unique business number assigned to the customer. |
| `first_name` | NVARCHAR | Customer's first name. |
| `last_name` | NVARCHAR | Customer's last name. |
| `martial_status` | NVARCHAR | Marital status of the customer (e.g., Single, Married). |
| `gender` | NVARCHAR | Gender of the customer (Male/Female). |
| `birthdate` | DATE | Customer's date of birth (Enriched from ERP system). |
| `country` | NVARCHAR | The country of residence (Enriched from ERP location data). |

---

### 3. Table: `gold.dim_product`
This dimension table contains enriched product details and categorizations.

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `product_key` | INT (PK) | Surrogate Key (Primary Key) for the product. |
| `product_id` | INT | The original ID from the source CRM system (`prd_key`). |
| `product_number` | NVARCHAR | Unique business code for the product. |
| `product_name` | NVARCHAR | The official name of the product. |
| `category_id` | NVARCHAR | Category identifier (Linked from ERP category data). |
| `subcategory` | NVARCHAR | Sub-classification of the product. |
| `maintenance_cost`| DECIMAL | The cost associated with maintaining the product. |
| `cost` | DECIMAL | The manufacturing or acquisition cost of the product. |
| `product_line` | NVARCHAR | The specific business line the product belongs to. |
| `start_date` | DATE | The date the product was introduced or became active. |

---

## 🔑 Key Definitions
* **Surrogate Key:** A unique identifier (`_key`) generated internally for the Data Warehouse to handle historical changes and system integrations.
* **Business Key:** The original ID (`_id` or `_number`) used in the source systems (CRM/ERP).
* **Fact Table:** Contains the measurable, quantitative data about a business process.
* **Dimension Table:** Contains descriptive attributes (context) about the facts.

---
*Last Updated: April 2026*
