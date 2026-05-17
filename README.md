# FMCG Sales & Supply Chain Analytics Platform – Azure Data Engineering Project

End-to-End Enterprise Data Engineering Solution using Azure Databricks, ADLS Gen2 External Storage, Delta Lake Medallion Architecture, Unity Catalog Governance, and Real-Time Business Analytics for FMCG Operations.

# 📌 Table of Contents
- [Overview](#overview)
- [Business Problem](#business-problem)
- [Tech Stack](#tech-stack)
- [Solution Architecture](#solution-architecture)
- [Fact Data Processing](#fact-data-processing)
- [Dimensional Data Processing](#dimensional-data-processing)
- [Data Model](#data-model)
- [BI Dashboard](#bi-dashboard)
- [Databricks Orchestration](#databricks-orchestration)
- [Project Structure](#project-structure)
- [Business Impact](#business-impact)
- [Key Engineering Concepts Implemented](#key-engineering-concepts-implemented)
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

- ✅ Handling enterprise-scale FMCG data
- ✅ Enabling near real-time analytics
- ✅ Improving reporting performance
- ✅ Supporting parent organization consolidated reporting
- ✅ Building governed and reusable datasets for BI teams

# Tech Stack 

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

# Solution Architecture

The project follows the Bronze → Silver → Gold layered architecture pattern.

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/60bf2434191f2941f1262315f47f4190d1fa32a3/Medallion%20Architecture%20FMCG.png)

### Bronze Layer – Raw Ingestion

The Bronze Layer stores raw ingested FMCG data exactly as received from source systems.

Key Features
- Incremental file ingestion
- Schema preservation
- Audit tracking
- Raw historical storage
- Append-only architecture
- External ADLS storage integration
#### Example Tables
- bronze_dim_products
- bronze_dim_product_pricing
- bronze_dim_customers
- bronze_dim_date
- bronze_fact_orders
  
### Silver Layer – Data Transformation

The Silver Layer applies cleansing, transformation, and standardization logic.

Transformations Performed
- Null handling
- Deduplication
- Data quality validation
- Standardized business schema
- Column normalization
- Data enrichment
- Incremental merge processing
#### Example Tables
- silver_dim_products
- silver_dim_product_pricing
- silver_dim_customers
- silver_dim_date
- silver_fact_orders
  
### Gold Layer – Business Analytics

The Gold Layer contains curated business-ready analytics tables optimized for reporting and dashboards.

#### Business KPIs Generated
- Revenue trends
- FMCG sales performance
- Inventory turnover
- Product category analysis
- Regional sales analytics
- Supply chain efficiency
- Retail distribution insights
#### Example Gold Tables
- gold_dim_products
- gold_dim_product_pricing
- gold_dim_customers
- gold_dim_date
- gold_fact_orders

# Fact Data Processing

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/e87a04da1c1f40fd5505e4041a27605ec3dba129/Fact%20Data%20Processing.png)

This architecture represents an incremental fact data processing pipeline using the Medallion Architecture (Bronze → Silver → Gold). Raw source files are ingested into the Bronze layer as append-only historical fact data. Incremental records are extracted into staging tables for data cleaning, validation, and transformations before being appended or merged into the Silver layer. Additional business transformations and aggregations are processed through staging before loading into the Gold layer for analytics reporting. Finally, child-level Gold facts are incrementally rolled up into Parent + Child aggregate tables, enabling efficient large-scale reporting without reprocessing the entire historical dataset.

# Dimensional Data Processing

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/e87a04da1c1f40fd5505e4041a27605ec3dba129/Fact%20Data%20Processing.png)

This dimensional data processing pipeline follows the Medallion Architecture approach, where source dimension data is ingested from the Landing Layer into the Bronze layer for raw data validation and cleansing. The cleaned data is then fully loaded into the Silver layer, where business transformations and schema standardization are applied. Finally, curated and analytics-ready dimension tables are loaded into the Gold layer to support downstream reporting, dashboarding, and business analytics workloads.


# Data Model 

### Implemented a Star Schema Data Model.

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/25d9dcec7c8d3806813ce6f86e61871eb5d509e4/Data%20Model.png)


# BI Dashboard

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/8f05f99866baa90823f7c18b712bdfbf49bd1188/Dashboard/DashboardFMCG.png)

The Sales Insights Dashboard provides a comprehensive overview of business performance by tracking key metrics such as Total Revenue, Total Quantity Sold, Unique Customers, and Average Selling Price (ASP). It enables users to analyze top-performing products, monitor monthly revenue trends, and evaluate sales contribution across different channels. Interactive filters for Year, Quarter, Month, Channel, and Category allow detailed drill-down analysis, helping stakeholders make data-driven decisions related to sales growth, customer behavior, pricing strategy, and channel performance.

# Databricks Orchestration

Databricks Workflows orchestrate the complete pipeline.

![image_alt](https://github.com/AjayAntonyPowerBIDataEngineer/FMCG--Azure-Data-Engineer-DataBricks/blob/af837a96e9bb8df42588b68e5d660c993d03bf1d/Orchestration.png)

### Workflow Stages
- Raw File Detection
- Bronze Ingestion
- Silver Transformations
- Gold Aggregations
- Parent Org Consolidation
- Dashboard Refresh
### Pipeline Characteristics

- ✅ Automated orchestration
- ✅ Dependency management
- ✅ Retry mechanisms
- ✅ Incremental processing
- ✅ Scalable distributed execution

# Project Structure
```plaintext
fmcg-azure-data-engineering-platform/
│
├── Dashboard/
│   ├── DashboardFMCG.png
│   └── Demo/
│
├── Data_Model/
│   ├── Data_Model.png
│   └── Demo/
│
├── DimFactDataProcessing/
│   ├── DimDataProcessing.png
│   ├── FactDataProcessing.png
│   └── Demo/
│
├── Solution_Architecture/
│   ├── Medallion_Architecture_FMCG.png
│   └── Orchestration.png
│
├── code/
│   │
│   ├── dimension_data_processing/
│   │   ├── 1_customers_data_processing.ipynb
│   │   ├── 2_products_data_processing.ipynb
│   │   └── 3_pricing_data_processing.ipynb
│   │
│   ├── fact_data_processing/
│   │   ├── 1_full_load_fact.ipynb
│   │   └── 2_incremental_load_fact.ipynb
│   │
│   └── setup/
│       ├── dim_date_table_creation.ipynb
│       ├── setup_catalog.ipynb
│       └── utilities.ipynb
│
├── data/
│   │
│   ├── child_company/
│   │   │
│   │   ├── full_load/
│   │   │   │
│   │   │   ├── customers/
│   │   │   │   └── customers.csv
│   │   │   │
│   │   │   ├── gross_price/
│   │   │   │   └── gross_price.csv
│   │   │   │
│   │   │   ├── orders/
│   │   │   │   └── landing/
│   │   │   │       ├── orders_2025_07_01.csv
│   │   │   │       ├── orders_2025_07_02.csv
│   │   │   │       └── ...
│   │   │   │
│   │   │   └── products/
│   │   │       └── products.csv
│   │   │
│   │   └── incremental_load/
│   │       └── orders/
│   │           ├── orders_2025_12_01.csv
│   │           ├── orders_2025_12_02.csv
│   │           └── ...
│   │
│   ├── parent_company/
│   │   │
│   │   ├── full_load/
│   │   │   ├── dim_customers.csv
│   │   │   ├── dim_gross_price.csv
│   │   │   ├── dim_products.csv
│   │   │   └── fact_orders.csv
│   │   │
│   │   └── incremental_load/
│   │       └── fact_orders.csv
│   │
│   └── goldview_reporting/
│       └── denormalise_table_query_fmcg.txt
│
└── README.md
```
# Business Impact

This solution enables organizations to centralize and modernize their analytics platform by building a scalable Lakehouse architecture for enterprise reporting and decision-making. By transforming raw operational data into curated business-ready datasets, the platform helps stakeholders monitor seller performance, analyze product and sales trends, identify delivery and logistics inefficiencies, optimize customer experience, and track key revenue and operational KPIs through scalable and governed analytics solutions.

# Key Engineering Concepts Implemented
- Medallion Architecture
- Delta Lake Architecture
- External ADLS Storage
- Incremental ETL Processing
- Delta MERGE Operations
- Enterprise Data Governance
- Distributed Data Processing
- Data Quality Validation
- Databricks Workflow Orchestration
- Parent-Child Data Consolidation
- Enterprise Analytics Modeling

# Author & Contact

Ajay Suresh
Azure Data Engineer | Power BI Developer

💼 Focus Areas: Azure Data Engineering, ETL Pipelines, PySpark, Data Warehousing, Power BI
- 🔗 LinkedIn Portfolio
- 🔗 GitHub Projects

