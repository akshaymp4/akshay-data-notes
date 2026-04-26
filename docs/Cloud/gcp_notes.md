<div class="aws-hero">
  <div class="aws-chip">Cloud | Data Engineering | Analytics</div>
  <h1>GCP for Data Science, Analytics, and Engineering</h1>
  <p>
    Google Cloud Platform (GCP) is a cloud computing platform used to store data,
    run analytics, build pipelines, train machine learning models, and deploy applications.
  </p>
</div>

## 1.1 What Is GCP? { .aws-h2 }

GCP is Google's cloud platform.

It provides services for:

- Storage
- Compute
- Databases
- Networking
- Data analytics
- Machine learning
- Application deployment

GCP is especially well known for analytics services such as BigQuery.

## 1.2 Why GCP Is Useful for Data Work { .aws-h2 }

GCP is useful for teams that want strong managed analytics, serverless data warehousing, and scalable machine learning tools.

GCP helps data teams:

- Store large datasets
- Run SQL analytics at scale
- Build batch and streaming pipelines
- Process big data
- Train and deploy machine learning models
- Connect dashboards and BI tools
- Use managed services instead of managing servers

Simple example:

- Traditional way: store data in local databases and manually run reports
- GCP way: store files in Cloud Storage, load data into BigQuery, transform with Dataflow or Dataproc, and visualize using Looker Studio

## 1.3 Core Cloud Concepts { .aws-h2 }

### 1.3.1 Projects { .aws-h3 }

A GCP project is the main container for resources, billing, permissions, and APIs.

Example resources inside a project:

- Cloud Storage bucket
- BigQuery dataset
- Compute Engine VM
- Cloud Function
- Service account

### 1.3.2 Regions and Zones { .aws-h3 }

A region is a geographic area where Google has data centers.

A zone is a location inside a region.

Choosing the right region helps reduce latency and control data location.

### 1.3.3 APIs { .aws-h3 }

Many GCP services must have their APIs enabled before use.

Example:

Before using BigQuery or Cloud Storage in a project, the related API must be enabled.

## 1.4 GCP Storage Services { .aws-h2 }

### 1.4.1 Cloud Storage { .aws-h3 }

Cloud Storage is object storage for files, logs, images, backups, CSV files, Parquet files, and machine learning datasets.

It is similar to Amazon S3 and Azure Blob Storage.

Common uses:

- Store raw data
- Store processed data
- Keep backups
- Host static assets
- Build a data lake

### 1.4.2 Storage Classes { .aws-h3 }

Cloud Storage provides different storage classes based on how often data is accessed.

Examples:

- Standard: frequently accessed data
- Nearline: data accessed less often
- Coldline: rarely accessed data
- Archive: long-term archival data

### 1.4.3 Persistent Disk { .aws-h3 }

Persistent Disk provides block storage for Compute Engine virtual machines.

It is similar to a hard drive attached to a server.

## 1.5 GCP Compute Services { .aws-h2 }

### 1.5.1 Compute Engine { .aws-h3 }

Compute Engine provides virtual machines in the cloud.

You can install software, run applications, host APIs, or run custom data jobs.

Common use cases:

- Run Linux or Windows servers
- Host applications
- Install Python and data tools
- Run small batch jobs
- Build custom environments

### 1.5.2 Cloud Functions { .aws-h3 }

Cloud Functions is a serverless compute service.

It lets you run code when an event happens.

Common triggers:

| Trigger | Example |
|---|---|
| Cloud Storage | Run when a file is uploaded |
| HTTP | Run when an endpoint is called |
| Pub/Sub | Process messages from a topic |
| Eventarc | React to cloud events |
| Scheduler | Run on a schedule |

Common data use cases:

- Validate uploaded files
- Trigger a pipeline
- Call an external API
- Send alerts
- Run small automation scripts

### 1.5.3 Cloud Run { .aws-h3 }

Cloud Run runs containerized applications without managing servers.

It is useful for:

- APIs
- Web applications
- Data services
- Lightweight container workloads

## 1.6 Networking Basics { .aws-h2 }

### 1.6.1 VPC Network { .aws-h3 }

A VPC network is a private network inside GCP.

It controls how cloud resources communicate with each other and with the internet.

### 1.6.2 Firewall Rules { .aws-h3 }

Firewall rules control inbound and outbound traffic for resources in a VPC.

Example:

Allow SSH only from trusted IP addresses.

### 1.6.3 Public vs Private Access { .aws-h3 }

Public access means a resource can be reached from the internet.

Private access means only selected networks or internal services can reach it.

Production data systems usually prefer private access.

## 1.7 Security and Access Management { .aws-h2 }

### 1.7.1 IAM { .aws-h3 }

Identity and Access Management, or IAM, controls who can access GCP resources and what actions they can perform.

IAM is based on:

- Principals: users, groups, or service accounts
- Roles: permissions grouped together
- Resources: projects, buckets, datasets, and other services

### 1.7.2 Service Accounts { .aws-h3 }

A service account is an identity used by applications or services.

Example:

A Cloud Function can use a service account to read from Cloud Storage and write to BigQuery.

### 1.7.3 Principle of Least Privilege { .aws-h3 }

Give users and services only the permissions they need.

This reduces security risk and prevents accidental changes.

## 1.8 Google Cloud CLI { .aws-h2 }

Google Cloud CLI is the command-line tool used to manage GCP resources.

Example commands:

```bash
gcloud auth login
gcloud projects list
gcloud compute instances list
gsutil ls
```

For data roles, the CLI is useful for checking resources, copying files, and troubleshooting permissions.

## 1.9 Databases in GCP { .aws-h2 }

### 1.9.1 Cloud SQL { .aws-h3 }

Cloud SQL is a managed relational database service.

It supports common relational database engines such as PostgreSQL, MySQL, and SQL Server.

### 1.9.2 Cloud Spanner { .aws-h3 }

Cloud Spanner is a globally distributed relational database.

It is useful for applications that need relational structure, strong consistency, and global scale.

### 1.9.3 Firestore { .aws-h3 }

Firestore is a NoSQL document database.

It is commonly used for web, mobile, and application data.

## 1.10 Analytics and Data Engineering Services { .aws-h2 }

### 1.10.1 BigQuery { .aws-h3 }

BigQuery is a serverless data warehouse.

It lets you run SQL queries on large datasets without managing infrastructure.

Common uses:

- Data warehousing
- Analytics reporting
- Ad hoc SQL analysis
- Dashboard data source
- Machine learning with BigQuery ML

### 1.10.2 Dataflow { .aws-h3 }

Dataflow is a managed service for batch and streaming data processing.

It is based on Apache Beam.

Common uses:

- Streaming pipelines
- Batch transformations
- ETL processing
- Event processing

### 1.10.3 Dataproc { .aws-h3 }

Dataproc is a managed service for Spark and Hadoop workloads.

It is useful when teams want managed clusters for big data processing.

### 1.10.4 Pub/Sub { .aws-h3 }

Pub/Sub is a messaging service.

It helps connect systems using events and messages.

Common example:

An application publishes events to Pub/Sub, and a Dataflow pipeline processes them in near real time.

## 1.11 Vertex AI { .aws-h2 }

Vertex AI is GCP's managed machine learning platform.

It helps with:

- Dataset management
- Model training
- Experiment tracking
- Model registry
- Model deployment
- MLOps workflows

Typical workflow:

1. Store data in Cloud Storage or BigQuery
2. Prepare features using BigQuery or Dataflow
3. Train a model using Vertex AI
4. Register the model
5. Deploy the model to an endpoint
6. Monitor model performance

## 1.12 Beginner Data Architecture on GCP { .aws-h2 }

Example workflow:

1. Store raw files in Cloud Storage
2. Use Cloud Functions or Pub/Sub to trigger processing
3. Transform data using Dataflow or Dataproc
4. Load cleaned data into BigQuery
5. Run SQL analytics in BigQuery
6. Build dashboards using Looker Studio or another BI tool
7. Train models using Vertex AI

## 1.13 Pay-As-You-Go Model { .aws-h2 }

GCP generally charges based on usage.

Common cost areas:

- Storage size
- Compute time
- Data warehouse queries
- Data transfer
- Pipeline processing
- Machine learning training and endpoints

Important habit:

Stop or delete unused resources after practice.

## 1.14 When to Use What { .aws-h2 }

| Requirement | GCP Service |
|---|---|
| Object storage | Cloud Storage |
| Virtual machine | Compute Engine |
| Serverless function | Cloud Functions |
| Containerized app | Cloud Run |
| Managed SQL database | Cloud SQL |
| NoSQL database | Firestore |
| Data warehouse | BigQuery |
| Batch and streaming processing | Dataflow |
| Spark and Hadoop | Dataproc |
| Messaging | Pub/Sub |
| Machine learning | Vertex AI |
| Identity and access | IAM |

## 1.15 GCP Products and Their Normal Equivalent { .aws-h2 }

| GCP Product | Category | What It Is | Normal Equivalent |
|---|---|---|---|
| Cloud Storage | Storage | Object storage | Cloud hard drive for files |
| Compute Engine | Compute | Virtual machine in cloud | Physical server or laptop |
| Cloud Functions | Serverless Compute | Run code on events | Cron job or background script |
| Cloud Run | Containers | Run containers without servers | Managed container hosting |
| Cloud SQL | Database | Managed relational database | MySQL, PostgreSQL, or SQL Server database |
| Firestore | NoSQL Database | Document database | JSON-based application database |
| BigQuery | Analytics | Serverless data warehouse | SQL analytics warehouse |
| Dataflow | Data Processing | Batch and streaming pipelines | ETL processing engine |
| Dataproc | Big Data | Managed Spark and Hadoop | Spark cluster |
| Pub/Sub | Messaging | Event messaging | Message queue or event bus |
| Vertex AI | Machine Learning | ML platform | Managed ML workspace |

## 1.16 Quick Revision Notes { .aws-h2 }

- GCP is Google's cloud platform
- Projects organize resources, billing, APIs, and permissions
- Cloud Storage stores files and objects
- Compute Engine provides virtual machines
- Cloud Functions runs event-driven code
- Cloud Run runs containers without server management
- BigQuery is a major GCP analytics service
- Dataflow is used for batch and streaming pipelines
- Pub/Sub is used for event messaging
- Vertex AI supports machine learning workflows
- IAM controls access

## 1.17 Final Summary { .aws-h2 }

GCP provides:

- Storage
- Compute
- Networking
- Databases
- Data engineering tools
- Analytics services
- Machine learning services
- Security and identity management

For data roles, GCP is valuable because of BigQuery, Cloud Storage, Dataflow, Pub/Sub, and Vertex AI.
