<div class="aws-hero">
  <div class="aws-chip">Cloud | Data Engineering | Analytics</div>
  <h1>Azure for Data Science, Analytics, and Engineering</h1>
  <p>
    Microsoft Azure is a cloud computing platform used to build data pipelines, store data,
    run analytics workloads, deploy applications, and train machine learning models.
  </p>
</div>

## 1.1 What Is Azure? { .aws-h2 }

Azure is Microsoft's cloud platform.

It provides services for:

- Virtual machines
- Storage
- Databases
- Networking
- Analytics
- Artificial intelligence and machine learning
- Application deployment

Instead of managing physical servers, teams use Azure services over the internet and pay based on usage.

## 1.2 Why Azure Is Useful for Data Work { .aws-h2 }

Azure is commonly used in companies that already work with Microsoft tools such as Windows Server, SQL Server, Microsoft 365, Power BI, and Active Directory.

Azure helps data teams:

- Store raw and processed data
- Build ETL and ELT pipelines
- Run SQL analytics
- Process big data
- Deploy machine learning models
- Control access using enterprise identity
- Connect data platforms with Power BI

Simple example:

- Traditional way: keep Excel files and databases on local machines or office servers
- Azure way: store files in Azure Data Lake Storage, transform them with Azure Data Factory or Databricks, query them with Synapse, and visualize them in Power BI

## 1.3 Core Cloud Concepts { .aws-h2 }

### 1.3.1 Regions and Availability Zones { .aws-h3 }

An Azure region is a geographic area where Microsoft has data centers.

Availability Zones are separate locations inside a region.

They help improve reliability because applications can continue running even if one zone has a problem.

### 1.3.2 Resource Groups { .aws-h3 }

A Resource Group is a container for Azure resources.

Example resources inside one Resource Group:

- Storage account
- Virtual machine
- Database
- Data Factory
- Virtual network

Resource Groups make it easier to organize, monitor, and delete related resources.

### 1.3.3 Azure Subscription { .aws-h3 }

An Azure subscription is the billing and access boundary for Azure resources.

Companies often create separate subscriptions for:

- Development
- Testing
- Production
- Different business teams

## 1.4 Azure Storage Services { .aws-h2 }

### 1.4.1 Azure Blob Storage { .aws-h3 }

Azure Blob Storage stores objects such as files, images, logs, CSV files, Parquet files, and backups.

It is similar to Amazon S3.

Common uses:

- Store raw data files
- Store application logs
- Keep backups
- Store datasets for analytics
- Build a data lake foundation

### 1.4.2 Azure Data Lake Storage Gen2 { .aws-h3 }

Azure Data Lake Storage Gen2 is optimized for big data analytics.

It is built on Blob Storage and adds a hierarchical namespace, which makes folders and file operations work better for analytics workloads.

Common uses:

- Data lake storage
- Bronze, silver, and gold layer storage
- Databricks data storage
- Synapse analytics storage

### 1.4.3 Azure Files { .aws-h3 }

Azure Files provides managed file shares in the cloud.

It is useful when applications need shared folders rather than object storage.

## 1.5 Azure Compute Services { .aws-h2 }

### 1.5.1 Azure Virtual Machines { .aws-h3 }

Azure Virtual Machines provide cloud servers.

You can install operating systems, databases, Python packages, notebooks, APIs, and custom applications.

Common use cases:

- Run development servers
- Host applications
- Practice Linux or Windows administration
- Run small data jobs
- Create custom environments

### 1.5.2 Azure Functions { .aws-h3 }

Azure Functions is a serverless compute service.

It lets you run code without managing servers.

Common triggers:

| Trigger | Example |
|---|---|
| Blob Storage | Run when a file is uploaded |
| HTTP | Run when an API endpoint is called |
| Timer | Run on a schedule |
| Queue Storage | Process messages from a queue |
| Event Grid | React to cloud events |

Common data use cases:

- Validate uploaded files
- Start a Data Factory pipeline
- Call an API
- Send notifications
- Run small automation scripts

### 1.5.3 Azure App Service { .aws-h3 }

Azure App Service is used to deploy web apps and APIs without managing the full server.

It is useful for:

- Flask or FastAPI applications
- .NET applications
- Simple APIs
- Internal data tools

## 1.6 Networking Basics { .aws-h2 }

### 1.6.1 Virtual Network { .aws-h3 }

Azure Virtual Network, or VNet, is a private network inside Azure.

It is similar to AWS VPC.

VNets help control how services communicate with each other and with the internet.

### 1.6.2 Network Security Group { .aws-h3 }

A Network Security Group, or NSG, controls inbound and outbound traffic.

It works like a firewall for subnets and network interfaces.

### 1.6.3 Public vs Private Access { .aws-h3 }

Public access means a resource can be reached from the internet.

Private access means only selected networks or private endpoints can reach the resource.

For production data systems, private access is usually preferred.

## 1.7 Security and Access Management { .aws-h2 }

### 1.7.1 Microsoft Entra ID { .aws-h3 }

Microsoft Entra ID is the identity service used to manage users, groups, applications, and access.

It was previously known as Azure Active Directory.

Common uses:

- User login
- Group-based access
- Single sign-on
- Service principals for applications

### 1.7.2 Role-Based Access Control { .aws-h3 }

Azure RBAC controls what users and applications can do with Azure resources.

Examples:

- Reader: view resources
- Contributor: create and manage resources
- Owner: manage resources and access permissions
- Storage Blob Data Reader: read data from Blob Storage

### 1.7.3 Managed Identity { .aws-h3 }

Managed Identity allows Azure services to access other Azure services without storing passwords or secrets in code.

Example:

An Azure Function can use a managed identity to read from Blob Storage.

## 1.8 Azure CLI { .aws-h2 }

Azure CLI is the command-line tool used to manage Azure resources.

Example commands:

```bash
az login
az group list
az storage account list
az vm list
```

For data roles, Azure CLI is useful for checking resources, automating setup, and troubleshooting access.

## 1.9 Databases in Azure { .aws-h2 }

### 1.9.1 Azure SQL Database { .aws-h3 }

Azure SQL Database is a managed relational database service.

It is based on SQL Server and is useful for structured application data and reporting workloads.

### 1.9.2 Azure Database for PostgreSQL { .aws-h3 }

Azure Database for PostgreSQL is a managed PostgreSQL service.

Azure manages backups, patching, availability, and scaling options.

### 1.9.3 Azure Cosmos DB { .aws-h3 }

Azure Cosmos DB is a globally distributed NoSQL database.

It is useful for low-latency applications that need flexible data models.

## 1.10 Analytics and Data Engineering Services { .aws-h2 }

### 1.10.1 Azure Data Factory { .aws-h3 }

Azure Data Factory is a managed data integration and pipeline service.

It is used to move and transform data between systems.

Common uses:

- Copy data from databases to a data lake
- Schedule ETL pipelines
- Orchestrate Databricks notebooks
- Connect cloud and on-premises sources

### 1.10.2 Azure Synapse Analytics { .aws-h3 }

Azure Synapse Analytics is an analytics platform that combines data warehousing, SQL analytics, Spark, and pipeline capabilities.

It is used for large-scale analytics and enterprise reporting.

### 1.10.3 Azure Databricks { .aws-h3 }

Azure Databricks is a managed Databricks service on Azure.

It is commonly used for:

- Spark processing
- Delta Lake
- Machine learning workflows
- Lakehouse architecture

### 1.10.4 Microsoft Fabric { .aws-h3 }

Microsoft Fabric is an analytics platform that brings together data engineering, data warehousing, real-time analytics, data science, and Power BI experiences.

It is useful for organizations that want a unified Microsoft analytics environment.

## 1.11 Azure Machine Learning { .aws-h2 }

Azure Machine Learning is a managed platform for building, training, tracking, and deploying machine learning models.

It helps with:

- Experiment tracking
- Model training
- Model registry
- Model deployment
- MLOps workflows

Typical workflow:

1. Store data in Azure Data Lake Storage
2. Prepare data using Databricks, Synapse, or notebooks
3. Train a model in Azure Machine Learning
4. Register the model
5. Deploy the model as an endpoint
6. Monitor model performance

## 1.12 Beginner Data Architecture on Azure { .aws-h2 }

Example workflow:

1. Store raw files in Azure Data Lake Storage
2. Use Azure Data Factory to ingest data
3. Transform data using Azure Databricks
4. Store cleaned data in Delta tables or Synapse
5. Query data using SQL
6. Build dashboards in Power BI
7. Deploy models using Azure Machine Learning

## 1.13 Pay-As-You-Go Model { .aws-h2 }

Azure generally charges based on usage.

Common cost areas:

- Storage size
- Compute hours
- Data transfer
- Database size
- Pipeline runs
- Analytics processing

Important habit:

Stop or delete unused resources after practice.

## 1.14 When to Use What { .aws-h2 }

| Requirement | Azure Service |
|---|---|
| Object storage | Blob Storage |
| Data lake | Azure Data Lake Storage Gen2 |
| Virtual machine | Azure Virtual Machines |
| Serverless function | Azure Functions |
| Managed SQL database | Azure SQL Database |
| NoSQL database | Cosmos DB |
| ETL orchestration | Azure Data Factory |
| Big data processing | Azure Databricks |
| Data warehouse and analytics | Synapse Analytics |
| Machine learning | Azure Machine Learning |
| Identity and access | Microsoft Entra ID and RBAC |

## 1.15 Azure Products and Their Normal Equivalent { .aws-h2 }

| Azure Product | Category | What It Is | Normal Equivalent |
|---|---|---|---|
| Blob Storage | Storage | Object storage | Cloud hard drive for files |
| Data Lake Storage | Storage | Analytics-optimized storage | Organized data folder system |
| Virtual Machine | Compute | Server in cloud | Physical server or laptop |
| Azure Functions | Serverless Compute | Run code on events | Cron job or background script |
| Azure SQL Database | Database | Managed SQL database | SQL Server database |
| Cosmos DB | NoSQL Database | Flexible document database | JSON-based database |
| Data Factory | Data Integration | Pipeline orchestration | ETL scheduler |
| Synapse Analytics | Analytics | Data warehouse and analytics | Enterprise analytics platform |
| Azure Databricks | Big Data | Spark and lakehouse platform | Managed Spark workspace |
| Entra ID | Identity | User and app identity | Company login system |

## 1.16 Quick Revision Notes { .aws-h2 }

- Azure is Microsoft's cloud platform
- Resource Groups organize related services
- Blob Storage stores files and objects
- Data Lake Storage Gen2 is important for analytics
- Azure Functions is used for event-driven automation
- Azure Data Factory is used for data pipelines
- Synapse and Databricks are used for analytics and big data
- Entra ID and RBAC control access
- Azure Machine Learning supports ML workflows
- Power BI connects naturally with Azure data services

## 1.17 Final Summary { .aws-h2 }

Azure provides:

- Storage
- Compute
- Networking
- Databases
- Data engineering tools
- Analytics platforms
- Machine learning services
- Security and identity management

For data roles, Azure is valuable because it works well with SQL Server, Power BI, Databricks, enterprise identity, and modern data lake architectures.
