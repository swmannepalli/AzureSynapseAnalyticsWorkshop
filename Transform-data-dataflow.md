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

3. Select the source dataset in the **Source Settings** tab at the bottom of the page.
   - You can re-use the dataset that you used as the sink in previous copy pipelines
   - Create a new dataset if needed
    
![image](https://user-images.githubusercontent.com/94631202/221886201-fc69f8a4-01c2-46e3-a57a-60e1df593141.png)

4. You can select any additional data sources that you may need for lookups, joins, unions, etc.

5. Don't forget to hit the publish button. This is the save button for the Azure Synapse Analytics Workspace

![image](https://user-images.githubusercontent.com/94631202/221887334-9d7784ca-57a5-4fc5-817c-eeb771fe546d.png)

## Apply Transformations

1. This is the part that will require a little bit of creativity. There are many options for transformations that can have multiple input streams, multiple output streams, and logic build into them. Review the list of transformations by hitting the little **+** button to the right of the source.

![image](https://user-images.githubusercontent.com/94631202/222166701-37045fa8-6716-4112-8975-8ad06c913eb5.png)

2. When you have selected the desired transformation(s), make sure that all input streams and required settings are defined

![image](https://user-images.githubusercontent.com/94631202/222167350-e4b6bf45-91d6-42ce-9e3d-790075715da0.png)

3. Verify you are seeing the desired output in the **Data Preview** tab
   - _You will need to turn on **Data Flow Debug** to view the data preview_

![image](https://user-images.githubusercontent.com/94631202/222168963-7f9ed21a-92d0-4031-a5bc-23aa9aeafbf2.png)

## Define Sink

1. Select the little **+** next to the final transformation in the data flow and select **Sink**

![image](https://user-images.githubusercontent.com/94631202/222169341-770b9d07-72f2-4099-afff-712a08129b39.png)

2. Select which destination dataset where you want the transformed data to land
   - _You will need to create a new dataset if you haven't created a destination dataset_

![image](https://user-images.githubusercontent.com/94631202/222169972-a2c2c833-4dbf-42ef-8ea9-95ed5414b018.png)
   - _Don't forget to check the **Preview Tab** to verify the format and contents of the data that will land in the sink_

## Run the Pipeline and Dataflow

1. Click the **Publish All** button to save all changes

![image](https://user-images.githubusercontent.com/94631202/222171920-f9002e9e-7d6d-4e8a-8c97-5369f9cc5c22.png)

2. Navigate back to the pipeline
   - _You will probably have a tab open with this pipeline. If not you can select the **Integrate** option on the far right blade_

3. Run the pipeline by clicking **Add Trigger** and then **Trigger Now**

![image](https://user-images.githubusercontent.com/94631202/222172651-52375cad-a424-406a-bb28-519647440579.png)

4. Verify that the data has landed in the sink as you expect

