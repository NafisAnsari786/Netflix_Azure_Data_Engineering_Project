# Netflix_Azure_Data_Engineering_Project

# 🎬 Netflix Data Engineering Project

## 📌 Project Overview
This project is an end-to-end **Azure Data Engineering pipeline** built using **Azure Data Factory (ADF), Azure Data Lake Storage Gen2 (ADLS), Azure Databricks, PySpark, and Delta Lake**.

The pipeline ingests the Netflix Movies and TV Shows dataset from GitHub, validates file availability, lands the raw data into ADLS, and processes it through a **Bronze → Silver → Gold** architecture for analytics-ready outputs.

---

## 🚀 Tech Stack
- **Azure Data Factory (ADF)**
- **Azure Data Lake Storage Gen2 (ADLS)**
- **Azure Databricks**
- **PySpark**
- **Delta Lake**
- **SQL**
- **GitHub**

---

## 🏗️ Architecture
### Data Flow:
GitHub Raw CSV → ADF Validation → ADF Copy Activity → ADLS Raw Layer → Databricks Bronze → Silver → Gold

---

## 📂 Project Structure
```bash
Netflix-Data-Engineering-Project/
│
├── notebooks/
│   ├── 01_bronze_ingestion.py
│   ├── 02_silver_transformation.py
│   ├── 03_gold_analytics.py
│
├── adf/
│   ├── pipeline_screenshots/
│   ├── linked_services/
│   └── datasets/
│
├── architecture/
│   ├── architecture.png
│   └── pipeline_flow.png
│
├── screenshots/
│   ├── adf_pipeline_success.png
│   ├── adls_containers.png
│   ├── databricks_bronze.png
│   ├── databricks_silver.png
│   ├── databricks_gold.png
│   ├── spark_transformations.png
│   └── final_output.png
│
├── data/
│   └── sample_netflix_titles.csv
│
├── sql/
│   └── validation_queries.sql
│
└── README.md
```

---

## 🥉 Bronze Layer
### Objective:
Ingest raw Netflix dataset into Databricks and store it as a raw Delta layer.

### Tasks:
- Read raw CSV from ADLS
- Preserve raw schema
- Store data in Bronze layer

---

## 🥈 Silver Layer
### Objective:
Clean and transform raw data into structured, analytics-friendly datasets.

### Transformations Performed:
- Null handling
- Date standardization
- Duplicate removal
- Splitting multi-value columns (`cast`, `country`, `listed_in`)
- Data normalization

---

## 🥇 Gold Layer
### Objective:
Create business-ready analytical datasets.

### Gold Outputs:
- Content count by type
- Top genres
- Titles by country
- Yearly content growth
- Top actors/directors

---

## 📊 Key Engineering Concepts Demonstrated
- ETL / ELT pipeline design
- Azure Data Factory orchestration
- Data Lake ingestion patterns
- Databricks notebook-based transformations
- Delta Lake implementation
- Medallion Architecture
- Data cleaning and normalization
- Aggregations and analytics

---

## 📸 Proof of Execution
This repository includes:
- ADF pipeline screenshots
- ADLS container screenshots
- Databricks notebook screenshots
- Architecture diagram
- Gold layer outputs

---

## 💼 Business Value
This project simulates a real-world cloud data engineering workflow where raw data is ingested, validated, transformed, and prepared for downstream reporting and analytics.

---

## 🔮 Future Enhancements
- Incremental load implementation
- Parameterized pipelines
- Unity Catalog integration
- Power BI dashboard on Gold layer
- CI/CD deployment for ADF and Databricks notebooks

---

## 👨‍💻 Author
**Nafis Ansari**  
Data Analyst / Aspiring Data Engineer  

🔗 [LinkedIn](https://www.linkedin.com/)  
🔗 [GitHub](https://github.com/)
