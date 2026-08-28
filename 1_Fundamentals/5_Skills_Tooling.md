# Skills & Tooling for Data Engineering

## 1. Data Warehousing Tools

### Recommended: Snowflake

**Why Snowflake?**
- Cloud-independent (works on AWS, Azure, GCP)
- Highly in-demand in the market
- Separation of storage and compute
- Easy to learn and use

### What to Learn in Snowflake:

| Topic | Description |
|:---|:---|
| **Basics** | What is a data warehouse, OLTP vs OLAP |
| **Dimensional Modeling** | Fact tables, dimension tables, star schema, snowflake schema |
| **SCD** | Slowly Changing Dimensions (Type 1, 2, 3, 6) |
| **ETL/ELT** | Extract, Transform, Load processes |
| **Staging** | Staging areas and copy commands |
| **File Formats** | Working with CSV, JSON, Parquet |
| **Virtual Warehouses** | Compute resources in Snowflake |
| **Caching** | Result caching, metadata caching |
| **Clustering** | Data clustering for performance |
| **Storage Integration** | Integration with cloud storage (S3, GCS, Azure Blob) |
| **Snowpipe** | Automated data loading |
| **Time Travel** | Viewing and restoring historical data |
| **Zero-Copy Cloning** | Efficient database cloning |
| **Data Sharing** | Secure data sharing across accounts |
| **Materialized Views** | Pre-computed views for performance |

### Other Options:

| Tool | Use Case |
|:---|:---|
| **Amazon Redshift** | AWS native data warehouse |
| **Google BigQuery** | GCP native, serverless, petabyte-scale |
| **Azure Synapse** | Azure native data warehouse |
| **Apache Hive** | Open-source, metastore for Spark/Hadoop |

---

## 2. Data Processing Tools

### Apache Spark (Must Learn)

Spark is essential for processing big data at scale.

**Why Spark?**
- Batch and streaming processing
- In-memory computation (fast)
- Unified platform (SQL, streaming, ML, graph)
- Used by top companies worldwide

### What to Learn in Apache Spark:

| Topic | Description |
|:---|:---|
| **Basics** | What is Spark, why do we need it |
| **Architecture** | Spark architecture, cluster managers |
| **DataFrame API** | Structured API, DataFrames |
| **Transformations** | Lazy evaluation, transformations vs actions |
| **Structured API** | Data types, data sources |
| **Partitioning** | Data partitioning, bucketing |
| **User-Defined Functions** | UDFs in Spark |
| **Lower-Level API** | RDDs (Resilient Distributed Datasets) |
| **Production** | Running Spark on clusters, Databricks |
| **Spark SQL** | SQL interface for Spark |
| **Streaming** | Structured Streaming |

### Apache Kafka (For Real-time)

Kafka is the standard for real-time data streaming.

**Why Kafka?**
- Real-time data streaming
- Distributed and fault-tolerant
- High throughput
- Used with Spark, Flink, and other stream processors

### What to Learn in Kafka:

| Topic | Description |
|:---|:---|
| **Basics** | What is Kafka, why use it |
| **Architecture** | Producers, consumers, brokers, topics |
| **Topics** | Creating and managing topics |
| **Producers** | Producing data to topics |
| **Consumers** | Consuming data from topics |
| **Consumer Groups** | Scaling consumption |
| **Partitions** | Understanding partitions |
| **Offsets** | Message offsets |
| **Integration** | Kafka with Spark, Flink |

### Other Options:

| Tool | Use Case |
|:---|:---|
| **Apache Flink** | Real-time analytics and streaming |
| **Apache NiFi** | Data flow automation |
| **Apache Beam** | Unified batch and stream processing |

---

## 3. Data Orchestration Tools

### Apache Airflow (Highly Recommended)

Airflow is the most widely used orchestration tool.

**Why Airflow?**
- Industry standard
- Schedule and monitor workflows
- Dependency management
- Python-based (easy to write DAGs)

### What to Learn in Airflow:

| Topic | Description |
|:---|:---|
| **Basics** | What is orchestration, why need it |
| **DAGs** | Directed Acyclic Graphs |
| **Tasks** | Defining and chaining tasks |
| **Operators** | PythonOperator, BashOperator, etc. |
| **Scheduling** | Schedule intervals, cron expressions |
| **Monitoring** | UI, logs, task status |
| **Connections** | Connecting to databases and services |
| **XComs** | Cross-communication between tasks |
| **Best Practices** | Writing production-ready DAGs |

### Modern Orchestration Tools:

| Tool | Description |
|:---|:---|
| **Dagster** | Modern, data-aware orchestration |
| **Prefect** | Python-based, easy to learn |
| **Mage** | Modern, intuitive UI |

> **Note:** Modern tools (Dagster, Prefect, Mage) take 30 minutes to 1 hour to learn if you understand the fundamentals.

---

## 4. Modern Data Stack

The modern data stack uses ELT (Extract, Load, Transform) instead of traditional ETL.

![Modern Data Stack](./assets/Screenshot%20from%202026-08-28%2016-32-22.png)

### Key Components:

| Layer | Tools | Purpose |
|:---|:---|:---|
| **Ingestion** | Fivetran, Airbyte, Stitch | Connect to sources, load data |
| **Storage** | Snowflake, BigQuery, Databricks | Data warehouse/lake |
| **Transformation** | dbt (Data Build Tool) | Modern data transformation |
| **Orchestration** | Airflow, Dagster, Prefect | Schedule workflows |
| **BI/Analytics** | Looker, Tableau, Power BI | Dashboards and reporting |
| **Data Quality** | Great Expectations | Data validation |
| **Metadata** | OpenLineage, DataHub | Data lineage and metadata |
| **Reverse ETL** | Hightouch, Census | Send data to operational systems |

### Understanding Modern Tools:

| Tool | Problem It Solves |
|:---|:---|
| **Fivetran/Airbyte** | Data ingestion from sources to warehouse |
| **dbt** | Modern data transformation using SQL |
| **Airflow** | Orchestration and scheduling |
| **Great Expectations** | Data quality and testing |
| **DataHub** | Data discovery and governance |

---

## 5. Data Security & Data Masking

### Data Security Principles

| Principle | Description |
|:---|:---|
| **Confidentiality** | Data accessible only to authorized users |
| **Integrity** | Maintaining accuracy and completeness of data |
| **Availability** | Data available to authorized users when needed |

### Security Measures

| Measure | Description |
|:---|:---|
| **Encryption** | Data encrypted in transit and at rest |
| **Access Control** | Role-based access control (RBAC) |
| **Data Classification** | Categorizing data by sensitivity |
| **Network Security** | Secure data at network level |

### Data Masking

Data masking is a technique to protect sensitive information by hiding the actual data values.

**Example:**

```
Original Social Security Number: 123-45-6789
Masked SSN: XXX-XX-6789

Original Credit Card: 4111-1111-1111-1111
Masked Credit Card: XXXX-XXXX-XXXX-1111
```

**Why Masking?**
- Government regulations (GDPR, CCPA, HIPAA)
- Protect personally identifiable information (PII)
- Prevent data leaks

---

## 6. File Formats for Big Data

| Format | Description | Use Case |
|:---|:---|:---|
| **CSV** | Simple, human-readable | Small datasets, compatibility |
| **JSON** | Semi-structured, nested data | APIs, web data |
| **Parquet** | Columnar storage, compressed | Big data, analytics |
| **ORC** | Optimized Row Columnar | Hive, Hadoop workloads |
| **Avro** | Row-based, schema-based | Streaming, Kafka |

> **Why Parquet/ORC?**
> - Columnar storage (better for analytics)
> - High compression (90%+ compression)
> - Faster query performance

---

## 7. Summary: Skills Roadmap

### Priority Order

| Priority | Skill | Why |
|:---:|:---|:---|
| **1** | **SQL** | Non-negotiable, backbone of data |
| **2** | **Python** | Essential for ETL, automation |
| **3** | **Linux** | Required for server interaction |
| **4** | **Apache Spark** | Big data processing standard |
| **5** | **Apache Airflow** | Workflow orchestration standard |
| **6** | **Snowflake** | Cloud-independent data warehouse |
| **7** | **Apache Kafka** | Real-time streaming (if needed) |

### Skill Level Guidance

| Skill | Beginner | Intermediate | Advanced |
|:---|:---:|:---:|:---:|
| **SQL** | SELECT, INSERT, UPDATE | Joins, Aggregations | Window Functions, CTEs |
| **Python** | Basics, Data Structures | Pandas, File Handling | OOP, Testing, Packaging |
| **Spark** | DataFrames, SQL | Transformations, UDFs | Performance Tuning, Streaming |
| **Airflow** | DAGs, Operators | Scheduling, Monitoring | Custom Operators, Best Practices |
| **Snowflake** | Basics, Loading | Modeling, SCD | Performance, Clustering |

---

## 8. Recommended Learning Path

### Phase 1: Foundation
1. **Python** – Basics and data manipulation
2. **SQL** – From basics to advanced
3. **Linux** – Essential commands

### Phase 2: Data Engineering
1. **Data Warehousing** – Snowflake or Redshift/BigQuery
2. **Dimensional Modeling** – Star schema, snowflake, SCD
3. **ETL/ELT** – Understanding the process

### Phase 3: Big Data
1. **Apache Spark** – Core concepts and implementation
2. **Apache Kafka** – Real-time streaming basics
3. **Data Lake** – Object storage (S3, GCS, Azure Blob)

### Phase 4: Production
1. **Apache Airflow** – Orchestration and scheduling
2. **Data Quality** – Great Expectations, testing
3. **Data Governance** – Lineage, metadata, security

### Phase 5: Cloud
1. **AWS** – S3, Redshift, Glue, EMR, Athena
2. **Azure or GCP** – As per your target companies

---

## 9. Visual Learning Resources

Here are some visual representations of the skills and tools landscape:

### The Complete Data Engineering Skills Map

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    DATA ENGINEERING SKILLS MAP                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                     FOUNDATION SKILLS                               │   │
│  ├───────────────┬───────────────┬───────────────┬─────────────────┤   │
│  │    Python     │      SQL      │    Linux      │   Version Ctrl  │   │
│  │   (Must)      │  (Must)       │   (Must)      │   (Git)         │   │
│  └───────────────┴───────────────┴───────────────┴─────────────────┘   │
│                                    │                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐│
│  │                     DATA WAREHOUSING                               ││
│  ├───────────────┬───────────────┬───────────────┬─────────────────┤│
│  │   Snowflake   │   BigQuery    │   Redshift    │   Synapse       ││
│  │  (Recommended)│               │               │                 ││
│  └───────────────┴───────────────┴───────────────┴─────────────────┘│
│                                    │                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐│
│  │                    BIG DATA PROCESSING                             ││
│  ├───────────────┬───────────────┬───────────────┬─────────────────┤│
│  │  Apache Spark │  Apache Kafka │  Apache Flink │   Databricks    ││
│  │   (Must)      │  (Recommended)│               │                 ││
│  └───────────────┴───────────────┴───────────────┴─────────────────┘│
│                                    │                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐│
│  │                    ORCHESTRATION                                   ││
│  ├───────────────┬───────────────┬───────────────┬─────────────────┤│
│  │  Apache       │   Dagster     │   Prefect     │     Mage        ││
│  │  Airflow      │               │               │                 ││
│  │  (Must)       │               │               │                 ││
│  └───────────────┴───────────────┴───────────────┴─────────────────┘│
│                                    │                                     │
│  ┌─────────────────────────────────────────────────────────────────────┐│
│  │                    MODERN DATA STACK                               ││
│  ├───────────────┬───────────────┬───────────────┬─────────────────┤│
│  │     dbt       │   Fivetran    │    Airbyte    │   Looker/PowerBI││
│  │  (Transforms) │  (Ingest)     │  (Ingest)     │  (BI)           ││
│  └───────────────┴───────────────┴───────────────┴─────────────────┘│
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Tools Comparison Chart

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    TOOLS COMPARISON CHART                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  INGESTION        ──►  Kafka, Kinesis, Fivetran, Airbyte                    │
│                                                                             │
│  STORAGE          ──►  S3, GCS, Azure Blob (Data Lake)                     │
│                       Snowflake, BigQuery, Redshift (Warehouse)             │
│                                                                             │
│  PROCESSING       ──►  Apache Spark (Batch + Stream)                       │
│                       Apache Flink (Streaming)                              │
│                       AWS Glue (Serverless)                                 │
│                                                                             │
│  TRANSFORMATION   ──►  dbt (In-warehouse)                                   │
│                       Python/Pandas (Custom)                                 │
│                       Spark SQL                                             │
│                                                                             │
│  ORCHESTRATION    ──►  Apache Airflow (Standard)                            │
│                       Dagster, Prefect, Mage (Modern)                      │
│                                                                             │
│  BI & VISUALIZE   ──►  Tableau, Power BI, Looker, Quicksight               │
│                                                                             │
│  MONITORING       ──►  Great Expectations (Quality)                        │
│                       OpenLineage, DataHub (Lineage)                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

*End of Part 5: Skills & Tooling for Data Engineering*