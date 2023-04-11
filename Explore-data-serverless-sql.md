In Azure Synapse Analytics, you can use either the SQL Serverless engine, the big-data Spark engine, or both to explore your Data Lake. In this exercise, you will explore data using Serverless SQL pool.

**Task 1 - Explore the data lake with Azure Synapse SQL On-demand**

In this task, you will browse your data lake using SQL On-demand.

1. In Synapse Analytics Studio, from the left panel click on the expand icon and navigate to the Data hub.

   ![image](https://user-images.githubusercontent.com/41644397/221718459-82159944-c56e-49e8-b47a-a10b03bfe5d2.png)
   ![image](https://user-images.githubusercontent.com/41644397/221718536-b3773aa6-b5d9-41e8-b67f-1ac94af57301.png)

2. Switch to the Linked tab (1). Under Azure Data Lake Storage Gen2 (2), expand the "southridgesmadls" primary data lake storage account (3), and then select the "southridgesm-ws" file system (4).

   ![image](https://user-images.githubusercontent.com/41644397/231219939-2c8b92d8-49f9-4460-a2fa-3fbf2d9ac5df.png)

3. Inside the selected file system, double-click to navigate to Customers.csv (5).

4. Right-click "Customers.csv" and select New SQL script - Select TOP 100 rows.

   A script is automatically generated. Run this script to see how SQL on demand queries the file and returns the first 100 rows of that file with the header, allowing you to easily explore data in the file.

   ![image](https://user-images.githubusercontent.com/41644397/231227813-75a4dec3-dc95-4af3-9607-6482ee5c10ae.png)

5. Ensure the newly created script is connected to the Built-in pool and select Run. Data is loaded by the built-in SQL pool and processed as if it was coming from any regular relational database.

   ![image](https://user-images.githubusercontent.com/41644397/221721861-f390f1ed-d5ef-4977-881e-bda82fa058ed.png)

6. In Azure Synapse Analytics Studio, navigate to the Develop hub.
 
   ![image](https://user-images.githubusercontent.com/41644397/225426403-41d0b1db-2e0c-4cc9-852a-b83a4b6354ae.png)
