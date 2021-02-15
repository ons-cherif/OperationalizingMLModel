# Operationalizing Machine Learning Model

## Overview 

This project is part of the Udacity Azure ML Nanodegree. It aims to Deploy a Model, configure logging and consume its endpoint by providing a URI and a key using consume tab under the Model pane within the endpoint section on Azure ML. This model is then compared to an Azure ML SDK implementation of the same steps.

## Architectural Diagram

![alt_text](Screenshots/ArchitecturalDiagram.png)

## Key Steps

### Authentication: Create a Service Principle is not allowed within the Udacity VM account, so I skipped it.

### Automated ML Experiment

#### 1- Upload the dataset to use within the experiment:
   
   ![alt_text](Screenshots/BankMarketingDataset.png)
### Deploy the Best Model: 

#### 2- Deploy model in Azure ML Studio

   **- Submit and complete an AutoML run from the Azure AutomationML section:**
   
   ![alt_text](Screenshots/AutoMLCreated.png)
   
   ![alt_text](Screenshots/CompletedExperiment.png)
   
   ![alt_text](Screenshots/AdditionalConfigFroMLExperiment.png)
   
   ![alt_text](Screenshots/BestModel.png)
   
   **- Select the best model, enable  authentication and deploy it using Azure Container Instance (ACI), then enable "Application Insights"** using Python Azure SDK and the logs.py script.Finally, verify the endpoint details from the _endpoints_ section:
   
   ![alt_text](Screenshots/RunnedLogScript.png)
   
   ![alt_text](Screenshots/EnabledAppInsights.png)
   
#### 3- Swagger Documentation:
   
   **- Activate Swagger by running _swagger.sh_ script**: Because we don't have perimissions to use the port _80_ we need to choose another above the _8000_ port, in my case it's _9001_:
   
   ![alt_text](Screenshots/RunningSwagger.png)
   
   
   **- Create an HTTP server** to expose the current working directory via the _serve.py_ script:
   
   ![alt_text](Screenshots/RunServe.png)
   
   **- Visit the Swagger UI** and use the http://localhost:8000/swagger.json to explore the endpoint created earlier:
   
   ![alt_text](Screenshots/SwaggerDeployedModel.png)
   
   #### 4- Consume Model Endpoints:
   
   **- Using endpoint.py script**: First, change the Scoring Uri and the key by the ones provided within the _Details_ and _Consume_ tabs from the _Endpoints_ section, then test it, the result will be:
   
   ![alt_text](Screenshots/EndpointResult.png)
   
   **- Using benchmark.sh script**: As explained above, after changing the Uri and the key, run the benchmark.sh to visualize the HTTP requests from the created endpoint: 
   
   ![alt_text](Screenshots/ApachFromBenchmark.png)
   
   ![alt_text](Screenshots/ApachFromBenchMark2.png)
   
   ![alt_text](Screenshots/ApacheResult.png)
   
   ### Publish an ML Pipeline
   
   #### 5- Create, Publish and Consume a Pipeline:
   
   Using the same Experiment, model and cluster, I created and published a pipeline via Jupyter Notebook:
   
   **- Created pipeline:** 
   
   ![alt_text](Screenshots/Pipelines.png)
   
   **- Pipeline endpoint:** 
   
   ![alt_text](Screenshots/PipelineEndpoint.png)
   
   **- Bankmarketing dataset with the AutoML module:** 
   
   ![alt_text](Screenshots/DataSetWithAzureMLModels.png)
   
   ![alt_text](Screenshots/DataSetWithAzureMLModelsDetails.png)
   
   **- The “Published Pipeline overview”, showing a REST endpoint and a status of ACTIVE:**
   
   ![alt_text](Screenshots/PublishedPipelinewithActiveStatus.png)
   
   **- Showing the step runs using _RunDetails Widget_ via _Jupyter Notebok_ :**
   
   ![alt_text](Screenshots/StetpsRunsWidget.png)
   
   ![alt_text](Screenshots/StetpsRunsWidgetDetails1.png)
   
   ![alt_text](Screenshots/StetpsRunsWidgetDetails2.png)
   
   **- Showing the scheduled and completed run via ML Studio portal :**
   
   ![alt_text](Screenshots/PipelineCompletedInML.png)

## Screen Recording
  

## A short description of how to improve the project in the future

1 - Consider giving more time for training the model since we were rrestricted to one hour within this project.



## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
