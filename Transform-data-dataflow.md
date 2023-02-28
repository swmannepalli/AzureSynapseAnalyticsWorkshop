In this exercise, you will transform data using the code-free tools available in Azure Synapse Analytics. You will use the previously copied data that is currently sitting in the Azure Data Lake Storage Gen2 storage account and land the data in a curated zone.

## Create Pipline with Mapping Dataflow Activity
A pipeline contains the logical flow for an execution of a set of activities. In this section, you'll create a pipeline that contains a Data Flow activity.

1. Go to the **Integrate** tab. Select on the plus icon next to the pipelines header and select Pipeline.
![image](https://user-images.githubusercontent.com/94631202/221676074-1136c15c-8af6-414e-987d-4d08b0e225f1.png)

2. In the **Properties** settings page of the pipeline, enter **[AnyPipelineName]** for **Name**.

3. Under _Move and Transform_ in the _Activities_ pane, drag **Data flow** onto the pipeline canvas.

4. Select the **Settings** tab of the Data Flow activity in the pipeline and select **+ New** next to the Data
![image](https://user-images.githubusercontent.com/94631202/221681991-10b79b56-319e-4af5-926d-06d21c8ad394.png)

5. Name your data flow **[AnyDataflowName]** on the **Properties** page.

## Select the data sources

1. Select the **Develop** section on the far left blade
    - _You should see your newly created dataflow under the **Data Flows** section_
      
2. Add a source for the data you wish to transform by selecting **Add Source**
![image](https://user-images.githubusercontent.com/94631202/221684266-5ab5ed38-0295-489b-bc4a-4299799db406.png)

3. Select the source dataset in the **Source Settings** tab at the bottom of the page
![image](https://user-images.githubusercontent.com/94631202/221886201-fc69f8a4-01c2-46e3-a57a-60e1df593141.png)

4. You can select any additional data sources that you may need for lookups, joins, unions, etc.

5. Don't forget to hit the publish button. This is the save button for the Azure Synapse Analytics Workspace
![image](https://user-images.githubusercontent.com/94631202/221887334-9d7784ca-57a5-4fc5-817c-eeb771fe546d.png)

## Apply Transformations

1. do the thing

## Define Sink

1. do the thing

## Run the Pipeline and Dataflow

1. do the thing

