# 🛒 Brazilian E-Commerce ETL Pipeline Project

Welcome to the **Brazilian E-Commerce ETL Pipeline**, a full-stack data engineering project where we ingest, transform, and load real-world e-commerce data into a structured MySQL database. This pipeline was developed using **SSIS (SQL Server Integration Services)**, **MySQL**, and **SSMS (SQL Server Management Studio)**.

The project aims to simulate a real-world ETL process typically used in data-driven companies for analytics and business intelligence purposes.

---

## 📦 About the Dataset

The data used comes from the [Olist Brazilian E-Commerce Public Dataset on Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), which contains information about customer orders from a multi-category marketplace in Brazil.

**Key files include:**
- `orders.csv` – Purchase lifecycle data
- `order_items.csv` – Items per order
- `products.csv` – Product details
- `customers.csv` – Customer location data
- `sellers.csv` – Marketplace seller data
- `order_payments.csv` – Payment details per order
- `order_reviews.csv` – Customer reviews and ratings
- `product_category_name_translation.csv` – Translations of product category names
- `geolocation.csv` – Zip code-level location data

---

## 🧰 Tools & Technologies Used

| Tool / Tech | Description |
|-------------|-------------|
| **SSIS** | Microsoft’s data integration tool for ETL workflows |
| **SSMS** | SQL Server Management Studio – used for writing and testing SQL |
| **MySQL** | Open-source RDBMS – final storage and schema hosting |
| **Kaggle** | Source of the e-commerce dataset |
| **Excel / CSV Tools** | Used to preview and prepare CSV data before ingestion |

---

## 🔧 ETL Pipeline Architecture

The entire project was divided into **three key stages**: Extract, Transform, and Load.

```mermaid
flowchart TD
    A[CSV files from Kaggle] --> B[SSIS ETL Pipeline]
    B --> C[Staging Tables in SSMS]
    C --> D[Data Transformation & Cleaning]
    D --> E[Load into MySQL Final Tables]
    E --> F[Structured DB Ready for Analytics]

## 📊 Project Workflow

### 🔍 1. Extract
- Downloaded raw `.csv` files from Kaggle
- Imported data into SSIS using Flat File Source
- Loaded raw data into staging tables

### 🧹 2. Transform
- Cleaned missing/invalid values
- Standardized column names and formats
- Applied data type conversions and relationships
- Performed joins to prepare dimensional modeling

### 📥 3. Load
- Loaded clean and structured data into a **MySQL** database
- Created **normalized schema** with primary/foreign key constraints
- Ensured optimized indexing and query readiness.
