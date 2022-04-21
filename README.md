# SpringBoot Batch Application on Azure Function invoked by Timer Trigger

This repository consists of sample application to showcase a way to run SpringBoot batch application on Azure Function invoked by timer trigger. 

This code has a flat ```sample-data.csv``` file which will be read by the Spring Batch job and data from the file will be inserted in Azure SQL database. Timer trigger is being used to trigger the batch job scheduled to be run in every 5 minutes interval.

# Technologies Used

* Java version 11
* SpringBoot Batch
* Azure Functions
* Azure SQL

# Prerequisite

* [Java Developer Kit](https://docs.microsoft.com/en-us/azure/developer/java/fundamentals/java-support-on-azure), version 11

* [Apache Maven](https://maven.apache.org/), version 3.0 or above

* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure)

* [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#v2) version 3.0.13901.0 or above

* Create [Azure SQL](https://docs.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal) on your resource group (use the same resource group name which you would use in ```pom.xml```)

# Installation

* Clone the project: git clone https://github.com/shrivastavarashmi/SampleSpringBatchTimerTrigger.git

* Configure the project to use your own resource group and your own function app name (it should be unique across Azure)

  * Open the ``` pom.xml file ```

  * Customize below properties
    * functionResourceGroup
    * functionAppName
    * functionAppRegion
  
* Configure Azure SQL Server details with your own Azure SQL Server details (created as prerequisite)

  * Open the ``` application.properties ```
  * Customize the spring.datasource.url, spring.datasource.username and spring.datasource.password properties with your own Azure SQL server instance details.

# Build the project

Navigate to the project folder and use below command to build the project :

 ``` mvn clean package ```

# To Run the project locally 

* Configure Storage account key with your own Storage Account connection string details

  * Open the ``` local.settings.json ```
  * Customize the AzureWebJobsStorage property with your own storage account key (You can have storage account created when you deploy the Azure function, use the details in here)

* Once the application is built, you can use below command to run the project :

    ``` mvn azure-functions:run ```

# Deploy the application to Azure Functions

Deploy the application to Azure Functions by using below command :

 ``` mvn azure-functions:deploy ```

This command will create new resource group (if not present already) as per given details in the properties setting of ```pom.xml```, also it will create function app, application insight and storage account and then deploy the azure function into the Function App.

# Verify Azure function

To verify if Azure function is working or not you can check below :
* Azure function gives facility to monitor your function for each successful or failure calls from your application, you can verify it easily and in case of any failure you can check the logs. Below are the checks you can do inside your function :
  ## Overview :
  
   ![image](https://user-images.githubusercontent.com/83832052/164419782-2b3bab39-cc12-4e4a-8bc2-68045f70c0dc.png)
  ## Monitor logs :
  
   ![image](https://user-images.githubusercontent.com/83832052/164419982-2af24cb9-cdbb-425e-8ce2-ea15b1730daf.png)
  ## Errors :
  
   ![image](https://user-images.githubusercontent.com/83832052/164420234-c854be27-b5a4-423f-8992-9e926824351a.png)
* Check Azure SQL database (_for data inserted from ```sample-data.csv``` file to the ```people``` table_ ) as below :

  ![image](https://user-images.githubusercontent.com/83832052/164417922-dff1bb91-97ee-45f2-bb00-00a8ef7e4ab6.png)
* Check Application insight (_for the logs and application map to see the call to Azure Functions_ ) as below :

  ![image](https://user-images.githubusercontent.com/83832052/164418988-5739c315-0084-4f96-a4c0-5b6517da775d.png)
  
  ![image](https://user-images.githubusercontent.com/83832052/164419111-159365d2-0e23-4dfb-8e76-6f9104edabd0.png)

# Reference Links
* [Create Azure Function using Intellij](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-maven-intellij)
* [Getting Started with Spring Cloud Function in Azure](https://docs.microsoft.com/en-us/azure/developer/java/spring-framework/getting-started-with-spring-cloud-function-in-azure)

