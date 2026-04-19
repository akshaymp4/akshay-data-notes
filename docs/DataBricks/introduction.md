<div class="databricks-hero">
  <div class="databricks-chip">Lakehouse | Spark | Data Platforms</div>
  <h1>Databricks Introduction</h1>
  <p>
    Databricks is a modern unified data and AI platform built around the lakehouse architecture.
    These notes cover the platform from basics to core architecture, governance, storage, and analytics concepts.
  </p>
</div>

## 1.1 What Is Databricks? { .databricks-h2 }

Databricks is a cloud-based unified data and AI platform built on top of Apache Spark that enables organizations to process, analyze, and build machine learning solutions on large-scale data.

It is designed around the Lakehouse architecture, which combines:

- Data Lake capabilities: low-cost storage, flexibility, and support for structured and unstructured data
- Data Warehouse capabilities: high performance, ACID transactions, governance, and BI optimization

This means Databricks gives you the flexibility of a data lake and the reliability of a data warehouse in a single platform.

```text
                    +------------------------------+
                    |        User Personas         |
                    |------------------------------|
                    |  - Data Engineer (DE)        |
                    |    - Jobs and Workflows      |
                    |    - ETL Pipelines           |
                    |                              |
                    |  - Data Analyst (DA)         |
                    |    - SQL Queries             |
                    |    - Dashboards              |
                    |                              |
                    |  - Data Scientist (DS)       |
                    |    - AI and ML Models        |
                    |    - Notebooks               |
                    +------------------------------+
                                ^
                                |
                    +------------------------------+
                    |   Data Intelligence Engine   |
                    |------------------------------|
                    |  Lakehouse + GenAI           |
                    |  - Query Optimization        |
                    |  - AI-powered Insights       |
                    |  - Natural Language to SQL   |
                    +------------------------------+
                                ^
                                |
                    +------------------------------+
                    |        Unity Catalog         |
                    |------------------------------|
                    |  Governance Layer            |
                    |  - Access Control            |
                    |  - Data Lineage              |
                    |  - Audit Logs                |
                    +------------------------------+
                                ^
                                |
                    +------------------------------+
                    |         Delta Lake           |
                    |------------------------------|
                    |  Lakehouse Storage Engine    |
                    |  - ACID Transactions         |
                    |  - Schema Enforcement        |
                    |  - Time Travel               |
                    |  - Batch + Streaming         |
                    +------------------------------+
                                ^
                                |
                    +------------------------------+
                    |            Cloud             |
                    |------------------------------|
                    |  AWS | Azure | GCP           |
                    |  (Compute + Storage)         |
                    +------------------------------+
```

> Integration with Azure gives more features because it is the primary owner, while others are third-party integrations.

## 1.2 High-Level Architecture { .databricks-h2 }

| Control Plane | Data Plane |
|---------------|------------|
| Managed by Databricks | Managed by customer |
| Databricks cloud account | Customer cloud account |
| Manages backend servers | Data is processed here |
| Hosts web application (UI) | Contains cluster |
| Cluster configuration | Cluster runs here |
| Jobs are created and managed | Jobs are executed here |
| Stores metadata | Stores client data |

## 1.3 Roles in Databricks { .databricks-h2 }

### 1.3.1 Account Administrator { .databricks-h3 }

- Creates and manages workspaces
- Manages users at the account level
- Controls global permissions
- Has the highest level of administrative control

### 1.3.2 Metastore Administrator { .databricks-h3 }

- Creates and manages catalogs
- Manages schemas and tables
- Controls data-level permissions
- Governs data objects in Unity Catalog

### 1.3.3 Workspace Administrator { .databricks-h3 }

- Admin of a specific workspace
- Manages users at the workspace level
- Assigns roles within the workspace
- Controls clusters and workspace settings

### 1.3.4 Owner { .databricks-h3 }

- User who creates an object such as a table, schema, or view
- Has full control over that object
- Can grant or revoke access to other users
- Responsible for managing that specific object

## 1.4 Why Databricks Is Called a Managed Service { .databricks-h2 }

Databricks is a managed service, meaning you do not need to manually set up or maintain infrastructure.

Instead of configuring servers, installing Spark, handling failures, and tuning performance, Databricks manages these automatically.

### 1.4.1 What Databricks Manages { .databricks-h3 }

- Cluster management
- Infrastructure provisioning
- Scaling
- Performance optimization
- Security integrations

### 1.4.2 What This Allows Users to Focus On { .databricks-h3 }

- Data engineers focus on pipelines
- Analysts focus on insights
- Data scientists focus on models

Instead of spending time on DevOps or infrastructure setup.

### 1.4.3 Cluster Management { .databricks-h3 }

Cluster management refers to the automatic creation, configuration, monitoring, and termination of compute clusters used to process data.

Databricks automatically manages Spark clusters so users do not need to manually configure servers.

### 1.4.4 Infrastructure Provisioning { .databricks-h3 }

Infrastructure provisioning is the process of setting up cloud resources such as virtual machines, storage, and networking.

Databricks automatically provisions the required cloud infrastructure on AWS, Azure, or GCP when you start a cluster.

### 1.4.5 Scaling { .databricks-h3 }

Scaling is the ability to increase or decrease computing resources based on workload demand.

Databricks supports auto-scaling, meaning it can add or remove worker nodes automatically depending on workload size.

### 1.4.6 Performance Optimization { .databricks-h3 }

Performance optimization involves tuning system resources and execution strategies to run workloads faster and more efficiently.

Databricks optimizes Spark jobs automatically using features like query optimization, caching, and optimized execution engines.

### 1.4.7 Security Integrations { .databricks-h3 }

Security integrations ensure that data access and system usage are secure and compliant with organizational policies.

Databricks integrates with cloud IAM systems, role-based access control, encryption, and Unity Catalog for governance.

### 1.4.8 Simple Explanation { .databricks-h3 }

Without Databricks, you manage servers, install Spark, scale manually, and secure everything yourself.

With Databricks, you write code and the platform manages the infrastructure around it.

This allows data engineers, analysts, and data scientists to focus on building data solutions instead of managing infrastructure.

## 1.5 Lakehouse Architecture Workflow Diagram { .databricks-h2 }

![Lakehouse architecture workflow](image-1.png)

## 1.6 Key Components of Databricks { .databricks-h2 }

- Workspaces: collaborative environment for notebooks, jobs, and dashboards
- Clusters: compute resources to run Spark workloads
- DBFS (Databricks File System): distributed file system abstraction
- Delta Lake: storage layer providing ACID transactions
- Unity Catalog: centralized governance layer

> Competitors of Delta Lake include Apache Iceberg, Apache Hudi, Snowflake, and Microsoft Fabric (OneLake).

## 1.7 Data Lake vs Data Warehouse vs Lakehouse { .databricks-h2 }

| Feature | Data Lake | Data Warehouse | Lakehouse (Databricks) |
|---------|-----------|----------------|-------------------------|
| Storage Cost | Low | High | Low |
| Schema | Flexible | Structured | Structured + Flexible |
| Performance | Medium | High | High |
| ACID Support | No | Yes | Yes (Delta Lake) |
| Governance | Limited | Strong | Strong (Unity Catalog) |
| Supports ML | Yes | Limited | Yes |

## 1.8 What Is Metadata? { .databricks-h2 }

Metadata is "data about data."

It provides information that describes, explains, or gives context to other data.

### 1.8.1 Examples of Metadata { .databricks-h3 }

- Table name
- Column names
- Data types
- File location
- Owner
- Created date
- Permissions

### 1.8.2 Why Metadata Helps { .databricks-h3 }

- Data discovery
- Governance
- Access control
- Query optimization

## 1.9 Databricks Account Setup { .databricks-h2 }

1. Create an Azure account.

## 1.10 Managed Tables vs External Tables { .databricks-h2 }

Databricks supports two main types of tables.

### 1.10.1 Managed Tables { .databricks-h3 }

In managed tables, Databricks manages both metadata and physical data storage.

Characteristics:

- Storage location controlled by Databricks
- Dropping the table deletes both metadata and data
- Strong governance using Unity Catalog
- Suitable for fully controlled environments
- Multi-tool access: difficult
- Data governance: fully governed
- Use case: quick analytics, internal BI systems, tightly controlled environments

### 1.10.2 External Tables { .databricks-h3 }

In external tables, Databricks manages only metadata, while data remains in external storage such as S3, ADLS, or GCS.

Characteristics:

- Data stored outside Databricks-managed location
- Dropping the table removes only metadata
- Flexible integration with other tools
- Requires governance discipline
- Multi-tool access: easy
- Data governance: flexible but requires discipline
- Use case: shared datasets, existing data lakes, multi-tool ecosystems

### 1.10.3 Managed vs External Tables { .databricks-h3 }

| Feature | Managed Table | External Table |
|---------|----------------|----------------|
| Metadata Management | Databricks | Databricks |
| Data Storage | Managed by Databricks | Stored externally (S3/ADLS/GCS) |
| Data Deletion | Metadata + data deleted | Only metadata deleted |
| Multi-tool Access | Limited | Easy |
| Governance | Fully controlled | Flexible |
| Best For | Internal analytics | Shared datasets or existing data lakes |

## 1.11 Lakehouse Architecture { .databricks-h2 }

Databricks implements the Lakehouse architecture, which combines:

| Data Lake | Data Warehouse |
|-----------|----------------|
| Cheap storage | High performance |
| Flexible schema | Structured governance |
| Raw data storage | BI-ready data |

Lakehouse provides:

- ACID transactions
- Schema enforcement
- Time travel
- Batch and streaming support

## 1.12 Medallion Architecture { .databricks-h2 }

The Medallion architecture is a data design pattern used in Databricks to organize data into three layers.

### 1.12.1 Medallion Architecture and Unity Catalog Overview { .databricks-h3 }

![Medallion architecture and Unity Catalog overview](image-2.png)

### 1.12.2 Bronze Layer { .databricks-h3 }

Bronze is the raw data layer.

- Ingested data from source systems
- Minimal transformation
- Used for auditing and traceability

### 1.12.3 Silver Layer { .databricks-h3 }

Silver is the cleaned and transformed data layer.

- Data cleaning
- Deduplication
- Standardization
- Schema enforcement

### 1.12.4 Gold Layer { .databricks-h3 }

Gold is the business-level data layer.

- Aggregated and curated datasets
- Business KPIs
- Optimized for reporting and analytics

### 1.12.5 Benefits of This Layered Approach { .databricks-h3 }

- Data quality
- Maintainability
- Performance
- Governance

### 1.12.6 Bronze vs Silver vs Gold { .databricks-h3 }

| Layer | Purpose | Data Quality | Transformation Level | Used By |
|-------|---------|--------------|----------------------|---------|
| Bronze | Raw ingestion | Low | Minimal | Data Engineers |
| Silver | Cleaned and standardized | Medium | Moderate | Data Engineers and Analysts |
| Gold | Business-ready data | High | Aggregated and curated | BI and business users |

Source -> Bronze -> Silver -> Gold -> BI / ML

## 1.13 Delta Lake { .databricks-h2 }

Delta Lake is the storage layer of Databricks that adds reliability to data lakes.

It is an open-source storage layer that brings ACID transactions, schema enforcement, and time travel capabilities to data lakes.

### 1.13.1 Delta Lake Provides { .databricks-h3 }

- ACID transactions
- Schema enforcement
- Schema evolution
- Time travel (versioning)
- Scalable metadata handling

### 1.13.2 Problems Delta Lake Solves { .databricks-h3 }

- Dirty reads
- Data corruption
- Concurrent write issues

## 1.14 Unity Catalog { .databricks-h2 }

Unity Catalog is Databricks' unified governance solution for data and AI assets.

### 1.14.1 Unity Catalog Manages { .databricks-h3 }

- Tables
- Views
- Files
- ML models
- Permissions
- Lineage tracking

### 1.14.2 Benefits of Unity Catalog { .databricks-h3 }

- Centralized access control
- Fine-grained permissions at row and column level
- Data lineage tracking
- Cross-workspace governance

It ensures secure and compliant data usage across the organization.

## 1.15 ACID Principles { .databricks-h2 }

Databricks, through Delta Lake, supports ACID properties.

### 1.15.1 Atomicity { .databricks-h3 }

A transaction either fully completes or fully fails.

### 1.15.2 Consistency { .databricks-h3 }

Data remains valid before and after a transaction.

### 1.15.3 Isolation { .databricks-h3 }

Concurrent transactions do not interfere with each other.

### 1.15.4 Durability { .databricks-h3 }

Once committed, data remains stored even if failures occur.

ACID ensures reliability in large-scale data systems.

### 1.15.5 ACID Properties in Delta Lake { .databricks-h3 }

| Property | Meaning | Example |
|---------|---------|---------|
| Atomicity | All-or-nothing execution | Failed transaction rolls back |
| Consistency | Data remains valid | Constraints enforced |
| Isolation | Transactions do not interfere | Concurrent writes handled safely |
| Durability | Data remains after commit | Data persists after crash |

## 1.16 OLTP vs OLAP { .databricks-h2 }

OLTP is for running daily business transactions, while OLAP is for analyzing data and generating insights.

Since you are moving toward data engineering and analytics, understanding this clearly is very important.

### 1.16.1 What Is OLTP? { .databricks-h3 }

OLTP stands for Online Transaction Processing.

- Used for day-to-day operations
- Handles many small transactions

Examples:

- Amazon placing an order
- Paytm making a payment
- Bank ATM withdrawal

When you add an item to a cart, make a payment, transfer money, or book a ticket, the database:

- Inserts data
- Updates records
- Deletes records
- Ensures data consistency

#### 1.16.1.1 OLTP Database Structure { .databricks-h4 }

![OLTP database structure](image-3.png)

- Highly normalized tables
- Fast inserts and updates
- Supports thousands of concurrent users

Example OLTP query:

```sql
UPDATE orders
SET status = 'Shipped'
WHERE order_id = 101;
```

This is a small, fast transaction.

### 1.16.2 What Is OLAP? { .databricks-h3 }

OLAP stands for Online Analytical Processing.

- Used for analysis and reporting
- Works on large historical data

Used by:

- Data analysts
- Data scientists
- Business intelligence teams

Examples:

- Tableau
- Power BI
- Snowflake
- Databricks

#### 1.16.2.1 OLAP Structure { .databricks-h4 }

![OLAP structure](image-4.png)
![OLAP schema example](image-5.png)

- Star schema
- Fact table plus dimension tables
- Aggregations
- Historical data

Example OLAP query:

```sql
SELECT region, SUM(sales)
FROM sales_data
GROUP BY region;
```

This scans millions of rows.

### 1.16.3 OLTP vs OLAP Comparison Table { .databricks-h3 }

| Feature | OLTP (Online Transaction Processing) | OLAP (Online Analytical Processing) |
|---------|---------------------------------------|--------------------------------------|
| Purpose | Run business operations | Analyze business data |
| Users | Customers, application users | Analysts, data scientists |
| Data | Current or real-time data | Historical data |
| Queries | Simple (INSERT, UPDATE, DELETE) | Complex (aggregations, joins) |
| Speed | Milliseconds | Seconds or minutes |
| Schema | Normalized | Star or Snowflake schema |
| Example DB | MySQL, PostgreSQL | Snowflake, BigQuery, Redshift |

### 1.16.4 Simple Real-Life Example { .databricks-h3 }

Think of a supermarket:

- Billing counter -> OLTP
- Monthly sales analysis -> OLAP

Since you:

- Work in analytics
- Want data engineer or BI roles

You will mainly work with OLAP systems, but you must understand OLTP to design pipelines.

### 1.16.5 Why It Matters for Data Engineers { .databricks-h3 }

- OLTP -> source systems
- ETL/ELT -> moves data
- OLAP -> data warehouse or analytics system

Understanding both is critical for designing data pipelines.

## 1.17 Databricks Hierarchy { .databricks-h2 }

Workspace -> Catalog -> Schema -> Tables

## 1.18 Summary { .databricks-h2 }

Databricks is a modern data platform that:

- Implements Lakehouse architecture
- Uses Delta Lake for reliability
- Supports Medallion architecture for structured data processing
- Provides centralized governance via Unity Catalog
- Enables scalable data engineering, analytics, and AI workloads

It simplifies big data processing while maintaining enterprise-grade governance and reliability.
