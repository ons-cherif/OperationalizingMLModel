# Operationalizing Machine Learning Model

## Overview 

This project is part of the Udacity Azure ML Nanodegree. It aims to Deploy a Model, configure logging and consume its endpoint by providing a URI and a key using consume tab under the Model pane within the endpoint section on Azure ML. This model is then compared to an Azure ML SDK implementation of the same steps.

## Architectural Diagram

![alt_text](Screenshots/ArchitecturalDiagram.png)

## Key Steps
   1- Upload the dataset to use within the experiment:
   
   ![alt_text](Screenshots/BankMarketingDataset.png)
   
### Deploy model in Azure ML Studio

   2- Submit and complete an AutoML run from the Azure AutomationML section, then deploy the best model:
   
   ![alt_text](Screenshots/AutoMLCreated.png)
   
   ![alt_text](Screenshots/CompletedExperiment.png)
   
   ![alt_text](Screenshots/AdditionalConfigFroMLExperiment.png)
   
   ![alt_text](Screenshots/BestModel.png)
   
   3- Enable "Application Insights" using Python Azure SDK and the logs.py script, then verify it via the the portal within the endpoints section:
   
   ![alt_text](Screenshots/RunnedLogScript.png)
   
   ![alt_text](Screenshots/EnabledAppInsights.png)
   
   #### 4- Swagger:
   
     **- Activate Swagger by running swagger.sh**, and because we don't have perimissions to use the port number _80_ we need to choose another one above _8000_, in my case it's _9001_
   
   ![alt_text](Screenshots/RunningSwagger.png)
   
   
       **- then create an HTTP server to expose the current working directory via the serve.py script:
       
   ![alt_text](Screenshots/RunServe.png)
   
   
  
   
### Publish an ML Pipeline

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## A short description of how to improve the project in the future

1 - Consider giving more time for training the model since we were rrestricted to one hour within this project.


## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
