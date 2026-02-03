# Power Query–Driven ETL in Azure Data Factory

## Overview
This project implements a **Power Query–centric ETL pipeline using Azure Data Factory (ADF)** to clean, standardize, and integrate Employee and Department datasets stored in **Azure Data Lake Storage Gen2 (ADLS)**. The pipeline addresses common real-world data quality issues and produces a curated, analytics-ready dataset through automated ingestion.

---

## Source Data
Two CSV datasets stored in ADLS are used as inputs:

- **Employee dataset**: Employee identifiers, job details, salary information, manager references, and department IDs  
- **Department dataset**: Department metadata including department name, manager ID, and location ID  

The raw data intentionally contains typical ingestion issues such as **masked date values, incorrect data types, unused columns, and sparsely populated reference fields**, reflecting real-world data scenarios.  
**Sample versions of the datasets used in this project are provided in the repository for reference.**

---

## Power Query Transformations
All transformations were implemented using **Azure Data Factory Power Query**:

- Enforced correct data types for identifiers, salary, and numeric fields  
- Filtered invalid and incomplete records (e.g., masked hire dates)  
- Removed columns with no business value  
- Integrated Employee and Department data using an **inner join on `DEPARTMENT_ID`** to enforce referential integrity  
- Added metadata columns for lineage and auditing:
  - `Source`
  - `Ingestion_Date`
- Applied conditional logic to classify employees into salary scales based on business rules  

---

## Orchestration & Automation
- Power Query transformations are executed within an **ADF pipeline**
- Pipeline execution is automated using a **schedule trigger**
- Curated output is written back to ADLS for downstream analytics and reporting

---

---

## Technologies Used
- Azure Data Factory  
- Power Query  
- Azure Data Lake Storage Gen2  

---

## Summary
This project demonstrates practical use of **Power Query within Azure Data Factory** to handle data quality issues, enforce schemas, integrate datasets, and automate ingestion workflows—reflecting patterns commonly used in production data engineering environments.
