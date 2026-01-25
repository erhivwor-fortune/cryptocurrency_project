# Project Title
Designing a Scalable Cryptocurrency Data Pipeline Using  Azure Blob Storage, Databricks Autoloader, and Delta  Lake.

# Project Overview
This project focuses on building a scalable and automated cryptocurrency data pipeline for IntelloBank using Azure cloud services and Databricks.
The pipeline ingests real-time cryptocurrency market data from the CoinGecko API, processes it using Databricks and Delta Lake, and stores analytics-ready data for reporting and decision-making.
The solution follows the Medallion Architecture pattern using Bronze, Silver, and Gold layers.

# Problem Statement
IntelloBank faces challenges managing cryptocurrency portfolio data due to manual workflows, fragmented data extraction, and the absence of a centralized data architecture.
These limitations lead to
Delays in data availability
Inconsistent insights
Poor scalability as data volume grows
This project addresses these issues by implementing an automated, cloud-native data pipeline on Azure.

# Project Objective
Extract cryptocurrency market data from the CoinGecko API
Clean and preprocess data to ensure quality and consistency
Store raw and processed data using Azure Data Lake Gen2
Automate ingestion and transformation using Databricks Autoloader
Orchestrate workflows using Azure Data Factory and Databricks jobs
Deliver analytics-ready data for downstream use

# Architecture Overview
The pipeline follows a modern Medallion Architecture.
Bronze Layer
Stores raw data from the CoinGecko API
Implemented using Azure Data Lake Gen2
Silver Layer
Cleansed and standardized data
Deduplication and schema enforcement using Delta Lake
Gold Layer
Curated, analytics-ready data
Stored in Azure SQL Database for reporting and BI tools

# Tech Stack
Python
API integration and data processing
CoinGecko API
Azure Blob Storage Data Lake Gen2
Storage for Bronze and Silver layers
Azure Databricks
Data ingestion, transformation, and orchestration
Delta Lake and Autoloader
Azure SQL Database
Gold layer storage

# Learning Outcomes
This project helped me develop skills in
Cloud-native data engineering
Modern data pipeline architecture
API-driven data ingestion
Automation and orchestration
Data modeling and management
Problem-solving in real-world scenarios

# Future Enhancements
Add real-time streaming analytics
Integrate Power BI dashboards
Implement data quality checks
Add monitoring and alerting
Improve schema evolution handling

# Author
Fortune Erhivwor
Data Engineer
