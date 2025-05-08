Advanced ETL with Azure, Databricks, and PySpark
Introduction
This project showcases the use of Databricks and PySpark to perform scalable data transformation tasks within an Azure cloud ecosystem. Data is mounted from Azure Data Lake Storage Gen2 (ADLS Gen2), transformed using Databricks (via PySpark and SparkSQL), and written back to the data lake. The process is automated and orchestrated using Azure Data Factory, forming a robust, production-ready ETL pipeline. 
#### Data Flow project overview
![Data_Factory_overview](https://user-images.githubusercontent.com/45521680/215343684-0259be55-e9d3-4e19-8f09-f5de9f1fd20e.png)
#### Lakehouse project overview
![Data_Lakehouse](https://user-images.githubusercontent.com/45521680/215344008-2da6da03-76bd-420b-9bb4-8a8dced25bb5.png)


Tools & Technologies
Databricks (PySpark, SparkSQL)

Azure Data Lake Storage Gen2

Azure Key Vault

Azure Data Factory

Azure Storage Explorer

Azure Resource Group & Storage Account

Python

Power BI (for visualization)

Project Workflow
Environment Setup

Create an Azure Resource Group and Storage Account.

Register an application for secure access (App Registration).

Generate and store secrets in Azure Key Vault.

Create a secret scope in Databricks to retrieve credentials securely.

Mounting Data to Databricks

Use the OAuth 2.0 configuration to securely mount data from ADLS Gen2.

Example mount configuration using dbutils.fs.mount():
```
dbutils.fs.mount(
    source = "abfss://<container>@<storage-account>.dfs.core.windows.net/<path>",
    mount_point = "/mnt/flightdata",
    extra_configs = configs
)

```
Data Transformation

Load data into a PySpark DataFrame.

Perform transformations using PySpark and SparkSQL.

Implement Delta Tables for ACID-compliant operations and efficient updates.

Handle both full and incremental loads (e.g., raw_incremental_load folder mimics real-time streaming data).

Loading Data Back to ADLS

Write transformed datasets back to Azure Data Lake Storage Gen2 for downstream consumption.

Orchestration with Azure Data Factory

Combine and schedule Databricks notebooks into a cohesive pipeline using Azure Data Factory.

Data Sources
Raw Data: Used for full-load transformations.

Incremental Load Data: Structured to simulate streaming or periodically updated data.

Conclusion
This project demonstrates an end-to-end ETL pipeline leveraging Azure cloud services and Databricks. The architecture supports both batch and incremental data processing, making it suitable for enterprise-scale data engineering tasks. The integration with Delta Lake ensures data reliability and performance, while Azure Data Factory provides orchestration at scale.



### Used Azure Services
<img width="739" alt="Screenshot 2023-01-29 at 11 14 32" src="https://user-images.githubusercontent.com/45521680/215344570-bf7415cb-0940-4848-a983-9d12bd687d00.png">

### Azure Data Factory 
We can either connect the databricks instance to the DataFactory instance through AD or though a personalised acces token, which we can generate in Databricks and pass as an authentication method. 

<img width="347" alt="Screenshot 2023-01-29 at 18 28 28" src="https://user-images.githubusercontent.com/45521680/215344532-2a6c4bb4-cf04-445c-b514-b70a369b243c.png">
<img width="632" alt="Screenshot 2023-01-29 at 11 45 39" src="https://user-images.githubusercontent.com/45521680/215344561-c2461509-1648-491f-a417-76b8355c0543.png">



### Potential project architecture (Big picture)
<img width="508" alt="Screenshot 2023-01-25 at 14 14 10" src="https://user-images.githubusercontent.com/45521680/214684174-7fb3e321-588a-4808-8f46-af497fff6ebc.png">

### Incremetal load architecture
![incremen<img width="604" alt="Screenshot 2023-01-29 at 17 04 17" src="https://user-images.githubusercontent.com/45521680/215344558-b368ee72-0734-4fdb-9fc8-80f3f9d76582.png">
tal_load_pipeline](https://user-images.githubusercontent.com/45521680/215343729-7da58562-4b5f-47d9-a9ff-c44e17dbc46e.png)

### Databricks Architecture
<img width="1390" alt="Screenshot 2023-01-25 at 13 28 10" src="https://user-images.githubusercontent.com/45521680/214684129-b83f23c8-ae6d-4cf7-942e-fea5fb152ef7.png">
