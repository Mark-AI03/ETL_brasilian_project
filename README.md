# 🛒 Brazilian E-Commerce ETL Pipeline Project

Welcome to the **Brazilian E-Commerce ETL Pipeline**, a full-stack data engineering project where we ingest, transform, and load real-world e-commerce data into a structured **MySQL** database. This pipeline was developed using:

- **SSIS (SQL Server Integration Services)**
- **SSMS (SQL Server Management Studio)**
- **MySQL**

This project simulates a real-world ETL process typically used in data-driven companies to prepare data for business intelligence, analytics, and reporting.

---

## 📊 Project Workflow

### 📦 About the Dataset

The dataset comes from the [Olist Brazilian E-Commerce Public Dataset on Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), featuring detailed transaction data from a Brazilian marketplace.

**Included files:**
- `orders.csv` – Order lifecycle
- `order_items.csv` – Items included in orders
- `products.csv` – Product metadata
- `customers.csv` – Customer demographics
- `sellers.csv` – Seller data
- `order_payments.csv` – Payment details
- `order_reviews.csv` – Customer reviews
- `geolocation.csv` – Zip code-level location data
- `product_category_name_translation.csv` – English translations

---

### 🔍 1. Extract
- Pulled raw `.csv` files from Kaggle.
- Connected Flat File Sources in SSIS to each dataset.
- Loaded data into **staging tables** in SQL Server (SSMS).

### 🧹 2. Transform
- Handled missing/invalid values.
- Standardized column names and formats.
- Applied data type conversions and relationships.
- Performed joins across tables to prepare dimensional modeling.

### 📥 3. Load
- Loaded clean and structured data into a **MySQL** database.
- Created **normalized schema** with primary/foreign key constraints.
- Ensured optimized indexing and query readiness.

---

## 🏗️ Data Warehouse Design

The final output of the ETL pipeline is a fully functional **data warehouse**, optimized for analytical workloads.

### 🌟 Star Schema Components

| Table Type      | Tables Included |
|------------------|----------------|
| **Fact Tables**  | `fact_orders`, `fact_payments`, `fact_reviews` |
| **Dimension Tables** | `dim_customers`, `dim_products`, `dim_sellers`, `dim_geolocation` |

### 🔧 Features of the Data Warehouse
- Designed using **star schema modeling** to support slice-and-dice operations.
- Built to handle high-volume queries like sales reporting, customer analysis, and delivery performance.
- Easy integration with BI tools like **Power BI**, **Tableau**, or **Metabase**.
- Designed with scalability and modularity in mind.


## 🧰 Tools & Technologies Used

| Tool           | Purpose                                      |
|----------------|----------------------------------------------|
| **SSIS**       | Designed ETL workflows with data flow logic  |
| **SSMS**       | SQL Server staging, data profiling           |
| **MySQL**      | Final structured database                    |
| **Kaggle**     | Source of the raw CSV dataset                |
| **CSV Tools**  | Pre-processing and quick exploration         |

---

## 🔄 Detailed ETL Steps

Here’s a breakdown of each step followed during the ETL process:

### 🔸 Extract Phase
1. **Download Data**: Obtained the Olist dataset from Kaggle in CSV format.
2. **Data Validation**: Opened files to check delimiter issues, header formats, and encoding.
3. **Import into SSIS**: Set up Flat File Connections in SSIS for each CSV.
4. **Staging Load**: Loaded raw files into staging tables in SQL Server via SSIS.

### 🔸 Transform Phase
1. **Clean & Format**:
   - Replaced nulls with defaults.
   - Cleaned special characters.
   - Unified date formats (`YYYY-MM-DD`).
2. **Data Type Conversion**:
   - Converted `price`, `freight_value` to `DECIMAL`.
   - Parsed timestamps to SQL `DATETIME`.
3. **Remove Duplicates**:
   - Deduplicated `order_items`, `payments`, and `reviews`.
4. **Apply Relationships**:
   - Joined tables like `orders` → `order_items` → `products`.
   - Mapped `product_category_name` to English translations.
5. **Normalization**:
   - Split data into fact and dimension tables.
   - Created surrogate keys for dimensions.
   - Ensured compliance with 3NF (Third Normal Form).

### 🔸 Load Phase
1. **Design Schema in MySQL**:
   - Created tables and constraints based on the new structure.
   - Added indexing on foreign and frequently queried keys.
2. **Load Final Tables**:
   - Transferred transformed data from SSMS to MySQL.
   - Validated referential integrity between all tables.
3. **Final QA**:
   - Ran test queries to validate record counts, data joins, and accuracy.
   - Generated logs for successful loads and tracked row-level errors.

---

## 🔧 ETL Pipeline Architecture

The ETL pipeline is broken into 3 phases: **Extract**, **Transform**, and **Load**.

```mermaid
flowchart TD
    A[CSV files from Kaggle] --> B[SSIS ETL Pipeline]
    B --> C[Staging Tables in SSMS]
    C --> D[Data Cleaning & Transformation]
    D --> E[Normalized Tables in MySQL]
    E --> F[Ready for BI & Analytics]

