# Operationalizing Machine Learning Model

## Overview 

This project is part of the Udacity Azure ML Nanodegree. It aims to Deploy a Model, configure logging by enablibg "Application Insights" and consume its endpoint by the provided URI and a key from the endpoint details page. Then using the same created Experiment, same cluster and the same already uploaded dataset we created and published a pipeline REST endpoint using the Azure ML SDK within Jupyter.

## Architectural Diagram

![alt_text](Screenshots/ArchitecturalDiagram.png)

## Key Steps

### Authentication: Create a Service Principle is not allowed within the Udacity VM account, so I skipped it.

### Automated ML Experiment

#### 1- Upload the bank marketing dataset available from the link given with the project. We used this dataset within the experiment:
   
   ![alt_text](Screenshots/BankMarketingDataset.png)
   
### Deploy the Best Model: 

#### 2- Deploy model in Azure ML Studio

   **- First we need to submit and complete an AutoML run from the Azure AutomationML section by selecting the uploaded dataset and creating a cluster to run the experiment on, once the autoMl rn is created it will start automatically. The major steps have been captured with screenshots below :**
   
   ![alt_text](Screenshots/AutoMLCreated.png)
   
   ![alt_text](Screenshots/CompletedExperiment.png)
   
   ![alt_text](Screenshots/AdditionalConfigFroMLExperiment.png)
   
   ![alt_text](Screenshots/BestModel.png)
   
   **- After the Experiment is successfully completed, we need to select the best model and deploy it using Azure Container Instance (ACI). Also, we need to make sure to enable authentication before deploying.
   
   Once the deployment is done, we then run the logs.py script using Python Azure SDK or the machine _Git Bash_ to enable "Application Insights"** to log failures, track perfomance, browser/server usage and more. Finally, we can verify the endpoint details from the _endpoints_ section as shown in the below screenshots:
   
   ![alt_text](Screenshots/RunnedLogScript.png)
   
   ![alt_text](Screenshots/EnabledAppInsights.png)
   
#### 3- Swagger Documentation:
   
   **- We can use Swagger UI to overview and test the deployed endpoint via the provided methods. Within this project we're just using Swagger Ui to practice how to activate it. To do so, we need to run the _swagger.sh_ script** and because we don't have perimissions to use the port _80_ we need to choose another above the _8000_ port, in my case it's _9001_:
   
   ![alt_text](Screenshots/RunningSwagger.png)
   
   **- Then we need to create an HTTP server** to expose the current working directory via the _serve.py_ script which going to redirect us to the deployed best model as showing below:
   
   ![alt_text](Screenshots/RunServe.png)
   
   **- We can then visit the Swagger UI** and explore the endpoint created earlier by using the http://localhost:8000/swagger.json
   
   ![alt_text](Screenshots/SwaggerDeployedModel.png)
   
   #### 4- Consume Model Endpoints:
   
   **- To test if the created endpoint is working, we need to use the endpoint.py script**: First, we need to change the "Scoring Uri" and the "key" by the ones provided within the _Details_ and _Consume_ tabs from the _Endpoints_ section, then we run the script to test it, the result should be:
   
   ![alt_text](Screenshots/EndpointResult.png)
   
   **- We can also use the Apache HTTP server benchmarking** to test our endpoint. By providing the REST endpoint Uri and the ath key and run the benchmark.sh script to visualize the HTTP requests from the created endpoint, just like showed below: 
   
   ![alt_text](Screenshots/ApachFromBenchMark.png)
   
   ![alt_text](Screenshots/ApachFromBenchMark2.png)
   
   ![alt_text](Screenshots/ApacheResult.png)
   
   ### Publish an ML Pipeline
   
   #### 5- Create, Publish and Consume a Pipeline via SDK:
   
   Using the same Experiment, model and cluster, I created and published a pipeline via Jupyter Notebook:
   
   **- Created pipeline:** 
   
   ![alt_text](Screenshots/Pipelines.png)
   
   **- Pipeline endpoint:** 
   
   ![alt_text](Screenshots/EndpointBestModel.png)
   
   **- Bankmarketing dataset with the AutoML module:** 
   
   ![alt_text](Screenshots/DataSetWithAzureMLModels.png)
   
   
   ![alt_text](Screenshots/DataSetWithAzureMLModelsDetails.png)
   
   **- The “Published Pipeline overview”, showing a REST endpoint and a status of ACTIVE:**
   
   ![alt_text](Screenshots/PublishedPipelinewithActiveStatus.png)
   
   
   ![alt_text](Screenshots/PublishedPipelineOverview.png)

   
   **- Showing the step runs using _RunDetails Widget_ via _Jupyter Notebok_ :**
   
   ![alt_text](Screenshots/StetpsRunsWidget.png)
   
   ![alt_text](Screenshots/StetpsRunsWidgetDetails1.png)
      
   **- Showing the scheduled run via ML Studio portal :**
   
   ![alt_text](Screenshots/RunningPipeGraph.png)
   
   ![alt_text](Screenshots/runningPipe.png)

## Screen Recording

  This is the link to my screencast: https://youtu.be/N6rPYo678e0

## Future Improvments:

1 - Consider giving more time for training the model since we were restricted to one hour within this project, to go through all possible model combinations and comapare it with this experiment to highlight the changes if there are any.

2 - Enhancing the dataset and deal with the problems of the imbalaced data encountered within project one since we are using the same Bank Marketing dataset.

3 - This endpoint is only for learning puposes but I want to make more enhancments like: 
     -  Using the scaling feature of Azure based on demand 
     - Add more methods to swagger and enable swagger testing directly from the UI.
