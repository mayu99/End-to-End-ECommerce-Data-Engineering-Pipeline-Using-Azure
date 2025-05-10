
# 🛒 E-Commerce Data Engineering Project in Azure

## 🚀 Objective
To build a scalable, modular data pipeline that ingests structured and semi-structured data from multiple sources, processes and enriches it using distributed systems (Databricks & PySpark), and enables analytical insights via SQL querying (Azure Synapse) and dashboarding (Tableau).

---

## 🔁 1. Data Sources

### 📂 a. Kaggle E-Commerce Dataset
- Contains 7 CSV tables: orders, customers, products, payments, etc.
- Static batch files used for historical analysis.

### 🌐 b. Website Data (MySQL)
- Real-time operational data stored in a MySQL database.
- Frequently updated to reflect ongoing user activity.

---

## ☁️ 2. Data Ingestion Layer (Bronze) – Azure Data Factory (ADF)

### ✅ Activities Implemented

**a. Kaggle Data Ingestion**
- **Lookup activity** to dynamically fetch table names.
- **ForEach activity** to iterate over each of the 7 tables.
- **Copy Data activity** to ingest each dataset into ADLS Gen2 Bronze layer.

**b. Website Data (MySQL)**
- Uses ADF’s **Copy Data activity** to ingest from MySQL to ADLS Gen2.
- MySQL data is transferred to the Bronze zone in ADLS Gen2.

📁 **Target Storage:** Azure Data Lake Storage Gen2 (ADLS Gen2)

---

## 🧪 3. Processing & Transformation Layer (Silver) – Azure Databricks

### 🔐 a. Secure Access
- Enabled using **Azure App Registration** and Service Principal Authentication to connect Databricks with ADLS Gen2.

### 🛠 b. Transformations with PySpark
- **Cleaning:** Handle nulls, fix schema mismatches.
- **Preprocessing:** Type casting, deduplication, filtering.
- **Joining:** Combine tables to create enriched datasets.
- **NoSQL Integration:** Additional enrichment from Cosmos DB/MongoDB.
- Output is saved to the **Silver layer** in ADLS Gen2.

---

## 🧠 4. Analytical Layer (Gold) – Azure Synapse Analytics

### 🔍 a. Synapse Querying
- Uses **SQL Serverless or Dedicated Pools**.
- Connects to Silver layer data using **external tables or OpenRowSet**.

### 🧮 b. Data Analysis
- Conducts advanced analysis (customer segmentation, revenue trends).
- Results are saved back to the **Gold layer** using **CETAS** (Create External Table As Select).

---

## 📊 5. Visualization Layer – Tableau

- Tableau connects to Gold layer using:
  - Azure Synapse SQL connector, or
  - Direct connection to ADLS Gen2 using SAS.
- Dashboards created include:
  - Sales trends
  - Customer behavior
  - Regional performance
  - Product-category insights

---

## 🗂️ Medallion Architecture Summary

| Layer   | Purpose                            | Tools Used              |
|---------|------------------------------------|--------------------------|
| Bronze  | Raw data ingestion (as-is)         | ADF → ADLS Gen2         |
| Silver  | Cleaned, joined, enriched datasets | Azure Databricks (PySpark) |
| Gold    | Aggregated insights for analytics  | Azure Synapse SQL, Tableau |

---

## 🔧 Key Azure Services Used
- **Azure Data Lake Gen2**: Centralized storage.
- **Azure Data Factory (ADF)**: Orchestration and ingestion engine.
- **Azure Databricks**: Data transformation and enrichment.
- **Azure Synapse Analytics**: SQL-based analysis and modeling.
- **Tableau**: Interactive data visualization.

---

## ✅ Strengths of the Project
- Real-world demonstration of modern ETL and big data architecture.
- Secure integration using Azure Active Directory and Service Principal.
- Medallion architecture promotes scalability and modularity.
- Combines structured (MySQL, CSV) and semi-structured (NoSQL) data sources.
- Fully cloud-native, using best-in-class Azure tools.

---

## 📬 Contact
For any queries or contributions, please contact [Mayuresh Pandey](https://github.com/mayu99).
