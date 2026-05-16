# FMCG Sales & Supply Chain Analytics Platform – Azure Data Engineering Project

End-to-End Enterprise Data Engineering Solution using Azure Databricks, ADLS Gen2 External Storage, Delta Lake Medallion Architecture, Unity Catalog Governance, and Real-Time Business Analytics for FMCG Operations.

# 📌 Table of Contents
- [Overview](#overview)
- [Business Problem](#business-problem)
- [Solution Architecture](#solution-architecture)
- [Tech Stack](#tech-stack)
- [Medallion Architecture](#medallion-architecture)
- [End-to-End Data Flow](#end-to-end-data-flow)
- [Project Structure](#project-structure)
- [Data Ingestion Layer](#data-ingestion-layer)
- [Bronze Layer](#bronze-layer)
- [Silver Layer](#silver-layer)
- [Gold Layer](#gold-layer)
- [Parent & Child Organization Architecture](#parent--child-organization-architecture)
- [Serving Layer & Analytics](#serving-layer--analytics)
- [Databricks Orchestration](#databricks-orchestration)
- [Business Use Cases](#business-use-cases)
- [Key Engineering Concepts Implemented](#key-engineering-concepts-implemented)
- [Architecture Diagram](#architecture-diagram)
- [How to Run This Project](#how-to-run-this-project)
- [Future Enhancements](#future-enhancements)
- [Author](#author)
  
# Overview
This project demonstrates a production-grade Azure Data Engineering Platform built for an FMCG enterprise handling large-scale sales, inventory, supply chain, and operational analytics.

The platform follows the Medallion Architecture (Bronze → Silver → Gold) using Azure Databricks, ADLS Gen2 External Storage, Delta Lake, and Unity Catalog for centralized governance and scalable analytics.

The architecture supports:

Large-scale FMCG transaction ingestion
Incremental ETL processing
Enterprise data governance
Parent-child organization analytics integration
Dashboarding & BI reporting
Scalable cloud-native analytics workloads

This project simulates a real-world enterprise Azure Data Platform commonly used by global FMCG organizations.

# Business Problem 
FMCG companies generate massive volumes of data from:

Sales transactions
Inventory systems
Supply chain operations
Distribution channels
Retailer orders
Warehouse systems

Traditional systems struggle with:

Data silos across business units
Slow reporting pipelines
Poor scalability
Lack of centralized governance
Delayed business insights
Complex parent-child organization reporting

The objective of this project is to build a centralized modern data platform capable of:

✅ Handling enterprise-scale FMCG data
✅ Enabling near real-time analytics
✅ Improving reporting performance
✅ Supporting parent organization consolidated reporting
✅ Building governed and reusable datasets for BI teams

# Solution Architecture

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/60a17e040906229b8c05139c4a03e2e868434a6c/Screenshot%20(139).png)

# Tech Stack 
## ⚙️ Tech Stack

| Technology | Purpose |
|---|---|
| Microsoft Azure | Cloud platform for scalable data engineering infrastructure |
| Azure Data Lake Storage Gen2 (ADLS Gen2) | External storage for Bronze, Silver, and Gold layers |
| Azure Databricks | Distributed data processing and transformation engine |
| Databricks Workflows / Lakeflow Jobs | Pipeline orchestration and workflow automation |
| Delta Lake | ACID-compliant storage layer for reliable lakehouse architecture |
| Unity Catalog | Centralized data governance and access management |
| Databricks Genie | Dashboarding and business analytics serving layer |
| PySpark | Large-scale ETL processing and data transformation |
| SQL | Data modeling, analytics, and Gold layer querying |
| Medallion Architecture | Layered data lake design pattern (Bronze → Silver → Gold) |
| Gold Analytics Tables | Business-ready curated datasets for reporting and dashboards |
| GitHub | Version control and project documentation |
