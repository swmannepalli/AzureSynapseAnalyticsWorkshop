In Azure Synapse Analytics, you can use either the SQL Serverless engine, the big-data Spark engine, or both to explore your Data Lake. In this exercise, you will explore data using Serverless SQL pool.

**Task 1 - Explore the data lake with Azure Synapse SQL On-demand**

In this task, you will browse your data lake using SQL On-demand.

1. In Synapse Analytics Studio, from the left panel click on the expand icon and navigate to the Data hub.

![image](https://user-images.githubusercontent.com/41644397/221718459-82159944-c56e-49e8-b47a-a10b03bfe5d2.png)
![image](https://user-images.githubusercontent.com/41644397/221718536-b3773aa6-b5d9-41e8-b67f-1ac94af57301.png)

2. Switch to the Linked tab (1). Under Azure Data Lake Storage Gen2 (2), expand the "smcsynapseanalytics" primary data lake storage account (3), and then select the "synapsedemos" file system (4).

![image](https://user-images.githubusercontent.com/41644397/221719002-19474cc3-1933-4aa0-a874-a94f25ce4d57.png)

3. Inside the selected file system, double-click to navigate to raw -> IMDB (5).

4. Once you are in IMDB right-click "title.basics.tsv" and select New SQL script - Select TOP 100 rows.

A script is automatically generated. Run this script to see how SQL on demand queries the file and returns the first 100 rows of that file with the header, allowing you to easily explore data in the file.

![image](https://user-images.githubusercontent.com/41644397/221721140-f6a26902-936c-462c-bed0-ae42b2deb67f.png)

5. Ensure the newly created script is connected to the Built-in pool and select Run. Data is loaded by the built-in SQL pool and processed as if it was coming from any regular relational database.

![image](https://user-images.githubusercontent.com/41644397/221721861-f390f1ed-d5ef-4977-881e-bda82fa058ed.png)
