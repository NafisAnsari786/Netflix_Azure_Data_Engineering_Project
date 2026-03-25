# 🎬 End-to-End Netflix Data Pipeline: Azure Databricks & Delta Live Tables

<img width="940" height="513" alt="image" src="https://github.com/user-attachments/assets/0ee4b030-d8b1-4d4f-b524-648d6bd306e3" />

## 📌 Project Overview
This project showcases a fully automated, scalable data engineering pipeline built on the Microsoft Azure ecosystem. The objective was to design a robust ETL process that ingests raw Netflix catalog data, cleanses and transforms it using the Medallion Architecture, and prepares it for enterprise-level business intelligence.

While the primary focus is on backend data engineering, orchestration, and data quality, the pipeline's output is fully optimized and structurally ready for downstream BI tools via Databricks Partner Connect.

## 🛠️ Technology Stack
- Cloud Infrastructure: Microsoft Azure (Resource Groups, IAM)

- Data Orchestration: Azure Data Factory (ADF), Databricks Workflows

- Data Storage: Azure Data Lake Storage Gen2 (ADLS)

- Data Processing: Azure Databricks, PySpark

- Data Quality & Governance: Delta Live Tables (DLT)

- Downstream Integration: Power BI (via Databricks Partner Connect)

## 🏗️ Architecture & Data Flow
The pipeline is structured into distinct, logically separated storage containers within ADLS (raw, bronze, silver, gold, metastore, $logs) to enforce strict data governance.

1. Data Ingestion (Azure Data Factory)
- Configured an ADF pipeline to dynamically pull raw JSON/CSV files from a GitHub API.
- Utilized ForEach loops and dynamic variable assignments to iterate through multiple files, handling metadata validation before landing the data into the ADLS raw container.

2. The Medallion Architecture (Azure Databricks)
Data is processed incrementally through three distinct layers to ensure a "single source of truth":

**🥉 Bronze Layer (Raw Ingestion):** Implemented Databricks Auto Loader to incrementally stream newly landed files from the raw container.

- Preserved the exact state of the source data while appending metadata for traceability.

**🥈 Silver Layer (Cleansed & Standardized):** Handled missing values, standardized schema formats, and removed duplicates using PySpark.

Created clean master lookup tables, ready for complex joins.

**🥇 Gold Layer (Business-Ready Aggregates):** Leveraged Delta Live Tables (DLT) to build a directed acyclic graph (DAG) of streaming tables.

Generated highly optimized, use-case-specific tables: gold_netflixcast, gold_netflixcategory, gold_netflixcountries, gold_netflixdirectors, and gold_netflixtitles.

3. Data Quality & Reliability
Enforced strict data quality constraints at the Gold layer using DLT expectations (e.g., @dlt.expect_or_drop("valid_id", "show_id IS NOT NULL")).

The pipeline automatically drops invalid records and logs the metrics, ensuring only pristine data reaches the BI layer.

4. Advanced Orchestration & Scheduling
Designed a custom Databricks Workflow/Job schedule to automate the entire pipeline.

Implemented Conditional Logic (IfWeekDay) within the DAG to route job execution differently based on the day of the week (e.g., running specific master lookups only on weekdays vs. weekends), demonstrating control flow mastery.

📈 Downstream Integration & Future Scope
Current State: The Gold layer tables are successfully linked to Power BI via Databricks Partner Connect. The .pbi connection file has been generated and tested.

Future Scope: Development of an interactive Power BI dashboard to visualize content trends, geographical distribution of productions, and director-to-genre mappings.

📂 Repository Structure
/notebooks: Contains all PySpark and DLT code (Autoloader, Silver transformations, Gold DLT expectations).

/images: Visual proof of pipeline execution, ADF triggers, DLT graphs, and ADLS container structure.

/data: Sample metadata and lookup structures (if applicable).

---

## 👨‍💻 Author
**Nafis Ansari**  
Data Analyst / Data Engineer  

🔗 [LinkedIn](https://www.linkedin.com/)  
🔗 [GitHub](https://github.com/)
