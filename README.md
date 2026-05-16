**SQL Medallion Data Lakehouse with Jenkins CI/CD**

**Overview**

This project demonstrates an end-to-end SQL-based Medallion Architecture implementation using:

Bronze, Silver, and Gold layers
SQL Stored Procedures for ETL
Jenkins Pipeline for CI/CD automation
Automated database object deployment
Incremental and structured data processing

The solution is designed to simulate a modern Data Engineering pipeline where raw data is transformed into business-ready datasets using scalable SQL procedures and automated deployments.

                +------------------+
                |   Source Data    |
                +------------------+
                          |
                          v
                +------------------+
                |     Bronze DB    |
                |  Raw Ingestion   |
                +------------------+
                          |
                  Stored Procedures
                          |
                          v
                +------------------+
                |     Silver DB    |
                | Cleansed &       |
                | Standardized     |
                +------------------+
                          |
                  Stored Procedures
                          |
                          v
                +------------------+
                |      Gold DB     |
                | Business Ready   |
                | Analytics Layer  |
                +------------------+
                          |
                          v
                Reporting / BI / Analytics

**Key Features**
Medallion Architecture implementation
SQL Stored Procedure driven ETL
Automated Jenkins CI/CD pipeline
Modular SQL scripts
Layer-wise transformation
Reusable ETL framework
Scalable deployment approach

**Technology Stack**

| Technology             | Purpose                |
| ---------------------- | ---------------------- |
| SQL Server             | Database Engine        |
| Stored Procedures      | ETL Logic              |
| Jenkins                | CI/CD Automation       |
| GitHub                 | Version Control        |
| T-SQL                  | Data Transformation    |
| Medallion Architecture | Data Layering Strategy |

**Medallion Layers**
**Bronze Layer**
Purpose:
Raw data ingestion
Minimal transformation
Historical preservation

Typical Operations:
Initial loads
Raw staging
Audit tracking

**Silver Layer**
Purpose:
Data cleansing
Standardization
Deduplication
Business rule application

Typical Operations:
Null handling
Data type conversions
Referential integrity checks

**Gold Layer**
Purpose:
Business-ready datasets
Aggregations
Reporting tables
KPI generation

Typical Operations:
Fact and dimension creation
Reporting views
Analytical models

**Jenkins CI/CD Workflow**
The Jenkins pipeline automates:

Pull latest code from GitHub
Validate SQL scripts
Execute database deployment
Run ETL stored procedures
Generate execution logs

**How to Run**
**Prerequisites**
SQL Server Installed
Jenkins Installed
Git Installed
Database Access Configured

**Steps**
1. **Clone Repository**
git clone https://github.com/yourusername/SQL_DataLake.git

2. **Configure Database Connection**
Update connection parameters in:
Jenkins credentials
SQL connection scripts

3. **Run Jenkins Pipeline**
Trigger the Jenkins job manually or configure webhook automation.

**Business Use Cases**
This framework can be extended for:
Enterprise Data Warehousing
Reporting Platforms
Analytics Solutions
Customer Analytics
Operational Reporting

**Author**
Preetham
Senior Data Engineer

**Connect**
LinkedIn: https://linkedin.com/in/Preetham1791
GitHub: https://github.com/Preetu-17

**License**
This project is for learning, demonstration, and portfolio purposes.
