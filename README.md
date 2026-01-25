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

## Implementation Notes
https://excalidraw.com/#json=L_Ac5d2-GQ8BcgHHS9ZGx,AFTFvICAhLyWfcyZ4lh47A

METASTORE ----> Stores all data in a particular region. Each region must have one metastore
UNITY CATALOG ----> When you create Azure Databricks, it creates a UC by default. The downside is that you might not know how it works, so create one yoirself.
We use Unity Catalogue to govern data that goes btwn Azure storage and Databricks
Unity Catalog is only attached to Databricks, so we need to give it access (Access Connector) to Azure storage account that we created.
UC cannot access AS by default, therefore we need to create a member that can be given a role in order to access AS.
This is called an Access Connector, which can connect DB to AS.
We start by creating a container in Azure titled METASTORE (1:17:19) This is where data of the region can be stored.

Access Connector for Azure Databricks ----> Create an Access Connector.
We need the Access connector to give Databricks Unity Catalog access to our Azure Storage Account. 
To do this, go to Azure Storage Account and click on Access Control(IAM) and Add Role Assignment.
Now give access to the Access Connector that was created (Storage Blob contributor).
Create a Unity Catalog Metastore - azure
Create a metastore, which is the top level container for Unity Catalogue.
Create another meta store where extracted data goes into.
Create a new UC from databricks

RESOURCE GROUP
STORAGE ACCOUNT (create containers for medallion)
DATABRICKS
ACCESS CONNECTOR

Now is the time to give DATABRICKS (cryptobricks) access to the STORAGE ACCOUNT (cryptostorage).

Go to SA and select Access Control (IAM) and ADD ROLE ASSIGNMENT, then give access to the Connector (storage blob data contributor)
This will enable the Access Connector access to the data storage resource to be able to read, write, and delete data.

Click Managed identity and Select Member - Choose Access Connector for Azure Databricks and select the Access Connector you created.

SETUP UNITY CATALOG FROM AZURE
Copy your Microsoft Entra ID from Azure and login to azure databricks account.

CREATE A NEW META STORE - Only one meta store is allowed for each region.
We created a new meta store bcos we need full access to manage it. 
#Select your container name and storage name from Azure as highlighted in Databricks when you try to create a new metastore.

Go to Resource Connector created in Azure and copy the Resource ID.
Paste the Resource ID under Databricks Access Connector ID.

ONCE THIS IS DONE, CREATE CREDENTIALS.
SETUP EXTERNAL LOCATION - Creating a path where databricks UN has control.
EXTERNAL DATA  --> CREATE EXTERNAL LOCATION (connect the path where we created.)

SEND YOUR WORK TO GITHUB. 
Select Workspace, your_folder

Ensure you create cedentials before you create  external location.
AUTOLOADER
We use Autoloader to update our data for silver container. Start by importing dependencies
Go to Catalogue and create external location for Silver and schema.

CREATE A NEW DATABRICKS AND ASSIGN TO YOUR WORKSPACE

CATALOG ---> WORKSPACE ---> ASSIGN TO WORKSPACE

Spark cannot work with inconsistent data. So the data must be loaded with pandas which does automatic
transformation before loading to Spark.


# Author
Fortune Erhivwor
Data Engineer
