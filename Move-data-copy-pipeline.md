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

1. In Synapse Studio, select Develop from the left-hand menu.

![image](https://user-images.githubusercontent.com/84516667/219264799-0517e3ef-cde7-4913-91f5-e6d5794d640d.png)

2. Select +, then Notebook to add a new notebook.

![image](https://user-images.githubusercontent.com/84516667/219264937-a0b32f5f-f700-4f83-9f29-4790542c4418.png)

3. Attach your Apache Spark pool by selecting it from the Attach to (1) drop-down list, then select {} Add code (3) to create a new cell.

![image](https://user-images.githubusercontent.com/84516667/219265118-b495572f-7804-4535-8d4e-517cc552d692.png)

4. Paste the following into the new cell, and replace YOUR_DATALAKE_NAME with the name of your Storage Account Name provided in the environment details section on Lab Environment tab on the right.

   ```scala
    %%spark

    // Set the path to read the WWI Sales files
    import org.apache.spark.sql.SparkSession

    // Set the path to the ADLS Gen2 account
    val adlsPath = "abfss://wwi@YOUR_DATALAKE_NAME.dfs.core.windows.net"
    ```

    Select the **Run cell** button to execute the new cell:
 
 ![image](https://user-images.githubusercontent.com/84516667/219265549-a04cf055-7ce0-4849-b77d-6975ba5f210e.png)

   > This cell imports required libraries and sets the `adlsPath` variable, which defines the path used to connect to an Azure Data Lake Storage (ADLS) Gen2 account. Connecting to ADLS Gen2 from a notebook in Azure Synapse Analytics uses the power of Azure Active Directory (AAD) pass-through between compute and storage. The `%%spark` "magic" sets the cell language to Scala, which is required to use the `SparkSession` library.

5. Hover over the area just below the cell in the notebook, then select {} Add code to add a new cell.

![image](https://user-images.githubusercontent.com/84516667/219265767-1a1b5c5a-fe74-490d-961f-795200c779d0.png)

6. Paste the following and run the new cell:

%%spark

// Read the sales into a dataframe
val sales = spark.read.format("csv").option("header", "true").option("inferSchema", "true").option("sep", "|").load(s"$adlsPath/factsale-csv/2012/Q4")
sales.show(5)
sales.printSchema()
