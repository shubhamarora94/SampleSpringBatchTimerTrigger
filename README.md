# SpringBatch Application invoked by Timer Trigger

This repository consists of sample application to showcase a way to run springboot batch application invoked by timer trigger.

# Technologies Used

* Java version 11
* SpringBoot Batch
* Azure Funtions
* Azure SQL

# Prerequisite

* [Java Developer Kit](https://docs.microsoft.com/en-us/azure/developer/java/fundamentals/java-support-on-azure), version 11

* [Apache Maven](https://maven.apache.org/), version 3.0 or above

* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure)

* [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#v2) version 3.0.13901.0 or above
* Create [Function App](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-function-app-portal) in portal

# Installation

* Clone the project: git clone https://github.com/shrivastavarashmi/SampleSpringBatchTimerTrigger.git

* Configure the project to use your own resource group and your own application name (it should be unique across Azure)

  * Open the ``` pom.xml file ```

  * Customize the resourceGroup and appName properties
  
* Configure Storage account key with your own Storage Account connection string details

  * Open the ``` local.settings.json ```
  * Customize the AzureWebJobsStorage property with your own storage account key

* Configure Azure SQL Server details with your own Azure SQL Server details

  * Open the ``` application.properties ```
  * Customize the spring.datasource.url, spring.datasource.username and spring.datasource.password properties with your own Azure SQL server instance details.


* Build the project: ``` mvn clean package ```

# Quickstart

* Create [Azure SQL](https://docs.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal) on your resource group and use the details as per above-mentioned changes.
* Create [Storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal) and use details as per above-mentioned changes.
* Once the application is built, you can run it locally using the Azure Function Maven plug-in:

``` mvn azure-functions:run ```

# Deploying to Azure Functions

Deploy the application on Azure Functions with the Azure Function Maven plug-in:

``` mvn azure-functions:deploy ```

# Reference Links
* [Create Azure Function using Intellij](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-maven-intellij)
* [Getting Started with Spring Cloud Function in Azure](https://docs.microsoft.com/en-us/azure/developer/java/spring-framework/getting-started-with-spring-cloud-function-in-azure)

