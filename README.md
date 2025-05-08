🛒 Brazilian E-Commerce ETL Pipeline Project
Welcome to the Brazilian E-Commerce ETL Pipeline project!
This project focuses on building a scalable and clean ETL (Extract, Transform, Load) pipeline using real-world data from Olist's Brazilian E-Commerce dataset. The aim is to process and store data efficiently in a relational database for analysis and reporting.

📦 Dataset Overview
The dataset is provided by Olist, one of Brazil’s leading e-commerce marketplaces. It contains:

Orders, items, customers, reviews

Geolocation data

Payments and sellers

Product category translation

Over 100,000+ rows of e-commerce data, ideal for data engineering practice.

graph TD;
  A[Kaggle CSV Files] --> B[Staging in SSIS]
  B --> C[Data Cleansing & Transformation]
  C --> D[MySQL Database (Normalized)]
  D --> E[Querying & Reporting]
