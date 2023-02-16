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

**2. Create a SQL Server linked service using UI:**

Use the following steps to create a SQL Server linked service in the Azure portal UI.

1. Browse to the Manage tab in your Synapse workspace and select Linked Services, then click New:

![image](https://user-images.githubusercontent.com/84516667/219209501-6c14a774-bff3-4147-b2ef-db7ebf6b28e1.png)

2. Search for SQL and select the SQL Server connector.

![image](https://user-images.githubusercontent.com/84516667/219209624-72223cee-d70b-4437-ac7b-81f0efc46177.png)

Configure the service details, test the connection, and create the new linked service.

**Note:** Use Self-hosted Interstion Runtime created above for Connect via integration runtime option.

![image](https://user-images.githubusercontent.com/84516667/219210421-09040c74-28b8-4c38-a27e-9f39c3320cd6.png)

**3. Create a dataset with UI:**

![image](https://user-images.githubusercontent.com/84516667/219213463-6045cec8-e554-460b-b034-823830c4371a.png)

 Set properties to mention table name, select Lined service and integration runtime created above.
 
 **4. Create Azure Data Lake Storage Gen 2 Linked Service:**
 
 Use the following steps to create Azure Data Lake Storage Gen 2 linked service in the Azure portal UI.


---------------------------------------------------------------------------------------------------------------------------------------------------------

**Create Copy Pipeline:**

1. In Synapse Studio and select **Integrate** from the left-hand menu.

   ![Integrate hub.](https://github.com/solliancenet/azure-synapse-analytics-day/blob/581681ab061efc42f4348a7f12761b5360dc4c74/media/integrate-hub.png)

2. In the Integrate menu, select + button and select Pipeline.

<img width="689" alt="image" src="https://user-images.githubusercontent.com/84516667/219215510-b437a40c-3db7-4c2a-b98d-7e9a3a3653f8.png">

3. Expand Move & Transform, drag and drop Copy data to the canvas.

<img width="813" alt="image" src="https://user-images.githubusercontent.com/84516667/219216041-8611ccef-42bc-409e-84d6-31b2fa617fc0.png">

4. Go to Source Tab and select the SQL Server Dataset created above.
5. Go to Sink tab, select Azure Data Lake Storage Gen2 Dataset created above.
6. Click on Debug to run the pipeline. After successful completion, data will be copied from SQl Server on Azure VM to Azure Data Lake Storage Gen2.

## Task 2 - Query Azure Data Lake Storage Gen 2 data and load into dedicated SQL Pool using Spark Pool

