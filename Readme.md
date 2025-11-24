# Netflix Data Pipeline

## Project Overview
The **Netflix Data Pipeline** is an end-to-end Azure data engineering solution designed to ingest, transform, and analyze Netflix datasets. It follows a layered architecture (Bronze, Silver, Gold) to ensure structured, clean, and analytics-ready data. The system uses Azure Data Factory, Databricks, ADLS Gen2, Delta Lake, Synapse Analytics, and Power BI for scalable data processing and reporting.

---

## Architecture & Data Flow

### 1. Data Ingestion (Bronze Layer)
- **Source:** Netflix dataset (CSV) hosted on GitHub.
- **Storage:** Azure Data Lake Storage (ADLS Gen2) in raw and bronze containers.
- **Orchestration:** Azure Data Factory.
- **Process:**
  - ADF uses a **ForEach** loop to iterate through GitHub files.
  - Extracts `file_name` and `folder_name`.
  - Copies files into the **Bronze Layer**, replicating GitHub folder structure.

### 2. Data Processing (Silver Layer)
- **Transformation Engine:** Azure Databricks using PySpark.
- **Storage Format:** Delta Lake for optimized performance.
- **Processing Steps:**
  - Databricks **Auto Loader** handles incremental ingestion when applicable.
  - Other files are read from Bronze, cleaned, and stored in the **Silver Layer**.

### 3. Data Aggregation (Gold Layer)
- **Purpose:** Business-level transformations and aggregations.
- **Execution:** Databricks with Delta Live Tables (DLT).
- **Output:** Clean, analytics-ready data stored in the **Gold Layer** and Synapse Analytics.

### 4. Analytics & Reporting
- **Query Execution:** Azure Synapse SQL pools.
- **Reporting:** Power BI dashboards built on top of Synapse datasets.

---

## Technologies Used
- Azure Data Lake Storage (ADLS Gen2)
- Azure Data Factory (ADF)
- Azure Databricks (PySpark)
- Unity Catalog for secure data access
- Delta Lake
- Azure Synapse Analytics
- Power BI

---

## Implementation Steps
1. Configure ADLS Gen2 storage containers (raw, bronze, silver, gold).
2. Build ADF pipelines to ingest GitHub data using dynamic parameters and ForEach loops.
3. Set up Unity Catalog to allow Databricks to securely access ADLS.
4. Develop Databricks notebooks for ETL processing.
5. Use Delta Lake for optimized and versioned data storage.
6. Load transformed data into Synapse Analytics.
7. Build Power BI dashboards using Synapse as the data source.

---

## Key Features
- Automated data ingestion from GitHub to ADLS.
- Multi-layered data architecture (Bronze, Silver, Gold).
- Optimized transformations using Delta Lake.
- Secure data access using Unity Catalog.
- Real-time dashboards through Power BI.

---

## Expected Outcomes
- Improved data organization and lineage.
- Faster query execution through optimized Delta storage.
- Reliable insights into Netflix dataset patterns.

---

## Future Enhancements
- Integrate Azure Machine Learning for predictive analytics.
- Add real-time data streaming using Event Hubs.
- Extend the pipeline to support additional streaming platforms.



---

## Setup & Deployment
1. Clone the repository containing the Netflix dataset.
2. Deploy Azure resources (ADLS, ADF, Databricks, Synapse).
3. Configure ADF pipelines for ingestion.
4. Execute Databricks ETL notebooks.
5. Apply Unity Catalog access configuration.
6. Load processed data into Synapse.
7. Connect Power BI to Synapse for reporting.

---

## Contact
For suggestions or improvements, feel free to contribute or reach out.
