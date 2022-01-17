# SampleSpringBatchTimerTrigger

This is a sample application to showcase the use of Spring Cloud Function on top of Azure Functions for Spring batch application.

# Prerequisite

* [Java Developer Kit](https://docs.microsoft.com/en-us/azure/developer/java/fundamentals/java-support-on-azure), version 11

* [Apache Maven](https://maven.apache.org/), version 3.0 or above

* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure)

* [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#v2) version 3.0.13901.0 or above

# Installation

* Clone the project: git clone https://github.com/shrivastavarashmi/SampleSpringBatchTimerTrigger.git

* Configure the project to use your own resource group and your own application name (it should be unique across Azure)

  * Open the ``` pom.xml file ```

  * Customize the resourceGroup and appName properties
  
* Configure Storage account key with your own Storage Account key details

  * Open the ``` local.settings.json ```
  * Customize the AzureWebJobsStorage property with storage account key

* Build the project: ``` mvn clean package ```

# Quickstart

Once the application is built, you can run it locally using the Azure Function Maven plug-in:

``` mvn azure-functions:run ```

# Deploying to Azure Functions

Deploy the application on Azure Functions with the Azure Function Maven plug-in:

``` mvn azure-functions:deploy ```

# Reference [Link](https://docs.microsoft.com/en-us/azure/developer/java/spring-framework/getting-started-with-spring-cloud-function-in-azure)

