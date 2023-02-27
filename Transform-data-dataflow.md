In this exercise, you examine various methods for ingesting data into Azure Synapse Analytics and Azure Data Lake Storage Gen2.

The tasks you will perform in this exercise are:

  - Task 1 - Create and run a Synapse copy pipeline 
  - Task 2 - Query Azure Data Lake Storage Gen 2 data and load into dedicated SQL Pool using Spark Pool

## Task 1 - Create and run a Synapse copy pipeline 

Here, we will copy data from SQL Server on Azure Virtual Machine to Azure Data Lake Storage Gen 2.

**Prerequisites:**
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
**1. Create Self-hosted Integration Runtime for SQL Server:**

If your data store is located inside an on-premises network, an Azure virtual network, or Amazon Virtual Private Cloud, you need to configure a self-hosted integration runtime to connect to it.

Follow instructions provided in the link to set up Self-hosted Integration Runtime. [Self-hosted IR Set up steps](https://learn.microsoft.com/en-us/azure/data-factory/create-self-hosted-integration-runtime?tabs=data-factory#create-a-self-hosted-ir-via-ui)
