# Data engineering playbook

Add X logo here

Welcome to X and the data engineering playbook! The purpose of this pack is to acclimatise you to X's landscape as a data engineer and to help you understand commonly used approaches in data engineering.

## Contents 

[Learning Pathways](#learning-pathways)

[Data Engineer Consulting Skills](#data-engineer-consulting-skills)

[Software and tech stack](#software-and-tech-stack)

[Data engineering techniques](#data-engineering-techniques)

[Software development best practice](#software-development-best-practice)

[Common architectural patterns in data engineering](#common-architectural-patterns-in-data-engineering)

[Data Modelling Methodologies](#data-modelling-methodologies)


## Learning Pathways

### Azure certifications for data engineers

* [Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/?practice-assessment-type=certification)
* [Data Engineering on Microsoft Azure](https://learn.microsoft.com/en-us/training/courses/dp-203t00)
* [Azure AI Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-fundamentals/?practice-assessment-type=certification)
* [Azure AI Engineer Associate](https://learn.microsoft.com/en-us/credentials/certifications/azure-ai-engineer/?practice-assessment-type=certification)
* [Fabric Data Engineer Associate](https://learn.microsoft.com/en-us/credentials/certifications/fabric-data-engineer-associate/?practice-assessment-type=certification)

### Databricks certifications for data engineers

* [Data Engineer Associate](https://www.databricks.com/learn/certification/data-engineer-associate)
* [Data Engineer Professional](https://www.databricks.com/learn/certification/data-engineer-professional)
* [Generative AI Engineer Associate](https://www.databricks.com/learn/certification/genai-engineer-associate)

### Palantir

* [Data Engineer training track](https://learn.palantir.com/page/training-track-data-engineer)

## Data Engineer Consulting Skills

Working as a data engineer in a consulting role requires belnding technical expertise with strong communication and problem solving skills. 

🎯 Focus on delivering value to the business, not just code.

A consultant's primary goal is to solve a client's business problem, not just build a perfect pipeline.

Understand the "Why": Always start by asking, "What business decision or outcome will this data product enable?" If the pipeline doesn't drive business value (e.g., increased revenue, reduced cost, mitigated risk), it may be unnecessary.

Prioritise Impact: Design solutions that are "good enough" and fast over "perfect" and slow. A solution delivered in three months that captures 80% of the value is better than a perfect solution delivered in nine.

Cost-Benefit Analysis: Be ready to justify the technology choices based on total cost of ownership, licensing, and cloud compute usage.

🗣️ Master Communication and Stakeholder Management

Translate technical concepts: Be able to explain complex architecture (e.g., ACID properties, denormalization, streaming ingestion) to non-technical stakeholders (e.g., executives, marketing teams) using simple analogies and focusing on the impact and risk.

Manage expectations: Be transparent about project scope, realistic timelines, and potential roadblocks. 

Active Listening: Spend more time listening to the client's current pain points, existing architecture, and internal team capabilities before proposing a solution.

🗺️ Follow a Structured Methodology
Consulting engagements should follow a clear, repeatable process.

Discovery phase: Dedicate time upfront to map out the current state (existing systems, data sources, people) and the future state (the desired solution and architecture).

Data Governance & Quality: Never neglect to discuss data quality checks, metadata management, and security/compliance (PII) early on. These are often the biggest risks and costs.

Knowledge Transfer: Always plan for a formal handover and documentation phase to ensure the client's internal team can maintain and extend the solution after you leave or if you are not available..


## Software and tech stack

### Languages

As a data engineer you should have a good understanding of python/pyspark and sql/spark sql. You should also have a good understanding of [spark](https://www.databricks.com/glossary/what-is-apache-spark) and distributed compute. 

We dont have admin rights on our devices but any apps that you will need should be available in the company portal for download. If an app that you need is not in the company portal then you should contact IT and ask if they can add it.

### Coding style guide

#### Commenting in code

Comments should enhance understanding such as explaining complex logic, and shouldn't document what can already be gleaned from the code. Any comments in code should be brief and direct. Pipelines should be fully documented as part of the DevOps process within a wiki page. Refer to the 'Documentation' section in Data Engineer Consulting Skills to understand how to properly document a project. 

#### SQL query best practice

These rules ensure queries are high-performing, maintainable, and explicitly clear.

* Avoid SELECT *: Always explicitly list the columns you need. This prevents fetching unnecessary data (improving performance), avoids naming conflicts if tables change, and clarifies exactly what data is being returned.

* Use Explicit JOIN Syntax: Use INNER JOIN, LEFT JOIN, RIGHT JOIN, or FULL JOIN.

* Use Table and Column Aliases. Always assign an alias to every table in a query with multiple tables (e.g., FROM table_name AS t1).

* Always qualify every column with its table alias (e.g., SELECT t1.column_name).

* Always use the AS keyword when aliasing columns or tables for clarity.

* Use Common Table Expressions (CTEs): Use WITH clauses instead of nesting subqueries. CTEs significantly improve readability by breaking down complex logic into sequential, named steps.


## Software development best practice

### Getting started with git. 

Git is available on the company portal. If you want to use git with vs code you'll need to set it as an environment variable path on your device once you have downloaded it so that vs code can access it. 

### Version control and software development best practice

For data engineers working in cloud infrastructure, version control and software development best practices are essential to ensure reliability, collaboration, and traceability across data pipelines and environments. Using tools like Git and Azure DevOps allows teams to manage changes to infrastructure-as-code, ETL scripts, and data models in a controlled and auditable way. 

Adopting branching strategies, code reviews, and pull requests promotes code quality and knowledge sharing. Automated testing and CI/CD pipelines should be integrated to validate transformations, enforce coding standards, and streamline deployments to cloud environments. Together, these practices reduce errors, improve reproducibility, and enable scalable, maintainable data engineering workflows.

### Test Driven Development

As data engineers we should adopt a test-driven development (TDD) approach whenever possible to ensure that data pipelines, transformations, and models are robust, reliable, and maintainable. By writing tests before implementing code, engineers can define clear expectations for data quality and logic which means catching issues early in development rather than in production. 

TDD encourages modular, reusable code and builds confidence when refactoring or scaling pipelines. It also supports automated validation of schema changes, business rules, and performance assumptions.

### Pull requests

Pull requests are a key part of collaborative development, allowing data engineers to propose changes for review before merging into shared codebases. Protecting the main branch ensures that only tested, reviewed, and approved code is deployed which will prevent accidental overwrites or unverified changes that could disrupt production pipelines. 

During code reviews, engineers should look out for data logic accuracy, adherence to coding and naming standards, performance implications (e.g. inefficient queries or transformations), and test coverage. Reviews also provide an opportunity to share knowledge, maintain consistency across the team, and uphold data quality and reliability standards. 

## Common architectural patterns in data engineering

How the architecture is designed will be based on the clients use case and thier infrastructure they already have in place. The below concepts are to give an overview of commonly used architectural patterns.

## Data engineering techniques

### Warehouses, lakes and lakehouses

🔷 Data Warehouse (Structured Analytics)

Azure Synapse Analytics – Microsoft’s flagship cloud data warehouse for large-scale analytics and reporting.

Azure SQL Database – A managed relational database suitable for smaller-scale warehousing or departmental analytics.

Power BI – Often paired with Synapse for visualization and reporting.

💡 Example use case: Curating and modeling clean, structured data from multiple sources into star schemas for BI dashboards.

🔷 Data Lake (Raw, Unprocessed Storage)

Azure Data Lake Storage Gen2 (ADLS Gen2) – A scalable data lake built on top of Azure Blob Storage, ideal for storing raw structured, semi-structured, and unstructured data.

Azure Databricks – Commonly used to process and transform raw data stored in ADLS using Spark.

💡 Example use case: Storing raw IoT logs, CSVs, and JSON files from multiple systems for future transformation and analytics.

🔷 Data Lakehouse (Unified Analytics Platform)

Azure Databricks with Delta Lake – Implements the lakehouse paradigm by combining the flexibility of a data lake with the transactional reliability and query performance of a data warehouse.

Microsoft Fabric (Lakehouse) – A newer, fully integrated lakehouse offering that unifies data engineering, analytics, and BI on top of OneLake.

💡 Example use case: Using Delta tables in Databricks or Fabric’s Lakehouse to enable both SQL-based reporting and machine learning from the same data source.

### Medallion Architecture

The Medallion Architecture is a data design pattern that structures data pipelines into three logical layers - Bronze, Silver, and Gold. The aim of this is to improve data quality, reliability, and reusability across an organisation. This architecture helps data teams manage the gradual refinement of raw data into business-ready insights. Each layer represents a different stage of data curation: Bronze holds raw, unprocessed data ingested from various sources; Silver contains cleaned and conformed data, where schema enforcement, deduplication, and validation occur; and Gold provides fully refined, aggregated, and business-oriented data models optimized for analytics, reporting, and machine learning.

By layering data transformations in this way, the Medallion Architecture promotes modularity, governance, and trust in the data ecosystem. It encourages teams to apply consistent data quality checks and transformation logic at defined points, enabling clear data lineage and simplifying troubleshooting. Additionally, it supports a test-driven and incremental development approach — new logic or data sources can be introduced at the Bronze or Silver layer without disrupting downstream users consuming Gold datasets. The result is a scalable, maintainable framework that supports both operational efficiency and analytical agility in modern data platforms.

![MedallionArch](images/medallion.png)

[Microsoft: What is the medallion lakehouse architecture?](https://learn.microsoft.com/en-us/azure/databricks/lakehouse/medallion)

### File formats

Understanding different file formats is a cricial aspect of data engineering because data is stored, transferred, and processed in many forms, each with its own strengths and trade-offs. The right format impacts performance, cost, and compatibility across data pipelines.

For example:

*CSV* is simple and human-readable but inefficient for large-scale analytics.

*Parquet* has columnar format optimised for compression and query performance in cloud data warehouses.

*Avro* and *JSON* are often better suited for streaming or schema evolution use cases.

*Delta* files add transactional reliability and version control on top of data lakes. The data aspect of delta files are stored in parquet format. 

Delta (often called Delta Lake) is a modern open-source storage layer  that brings reliability, consistency, and performance to data lakes. It essentially upgrades a traditional data lake (like one on Azure Data Lake Storage) into a transactional, ACID-compliant data lakehouse. 

Delta also offers 'time travel' and versioning which is tracked in a transactional log, as well as schema enforcement or schema evolution depending on the use case. 

[More on Delta](https://delta.io/)

### Monitoring, error handling and alerting

This guidence is based on using Azure and Dtaabricks but the core principles are applicable across most platforms and projects. 

#### Monitoring — Observing Pipeline Health and Performance

Monitoring helps you understand pipeline reliability, performance, and data quality.
In Azure, you typically monitor across several layers:

Azure Data Factory (ADF) / Synapse Pipelines

Use Azure Monitor integration to track pipeline and activity runs and enable diagnostic logging to send metrics and logs to:

* Log Analytics Workspace

* Azure Storage

* Event Hubs (for downstream systems)

Key metrics you might want to monitor for include:

* Pipeline success/failure rates

* Duration and performance trends

* Data volumes processed

Storage and Compute Monitoring

* Azure Data Lake Storage Gen2: Track read/write operations, throttling, and latency in Azure Monitor.

* Synapse / SQL Pools: Monitor query performance, concurrency, and resource utilisation via SQL Insights or Query Store.

#### Error handling 

A robust pipeline should gracefully handle errors and allow controlled retries if applicable.

For example in ADF/Synapse in the events of a failure you can configure retry policies on critical activities (e.g. copy, notebook, stored procedure).

For transient errors due to things like network issues or cloud resource scaling you can use backoff strategies which give an exponential delay between retries. This is essentially how ling the pipeline should wait before conducting a retry after each failed attempt. 

You can also store error metadata (pipeline name, activity, error message, timestamp) in a central log table for audit and debugging.

### Partitioning

Partitioning is an important concept in data engineering as it directly affects query performance, scalability, and cost in big data systems.

Partitioning means dividing a large dataset into smaller, more manageable chunks (called partitions) based on the value of one or more columns — typically something like date, region, or customer_id.
Instead of storing all records in one massive file or table, the data is split across directories or files that correspond to those partition values.

Partitioing also means that distrobuted systems like Spark can handle the data more effectively as each partition can be processed in parallel. You can also easily drop, reload, or archive specific partitions without touching the rest of the data.

### ETL/ELT

Whether to use ETL (Extract, Transform, Load) or ELT (Extract, Load, Transform) is a core decision in data engineering, regardless of whether you're using batch or streaming data ingestion.

The primary difference lies in the timing and location of the Transformation (T) step and is largely dictated by the technology used in the destination system.

*ETL* (Extract, Transform, Load) is the older, more traditional paradigm.

Extract: Data is pulled from the source system.

Transform: The raw data is moved to a separate staging area or dedicated server where it is cleaned, structured, aggregated, and standardised. This step consumes processing power outside the final data warehouse.

Load: The cleaned, structured, and compliant data is finally loaded into the target data warehouse.

*ELT* (Extract, Load, Transform) is the modern standard, enabled by the massive processing power of the cloud.

Extract: Data is pulled from the source system.

Load: The raw, unaltered data is immediately loaded directly into the destination system (usually a Cloud Data Warehouse or Data Lake).

Transform: Transformation, cleansing, and modeling (often using SQL tools like dbt) are performed inside the destination system, leveraging its processing power.

### ACID Properties

*ACID* (Atomicity, Consistency, Isolation, Durability) is a set of properties that guarantee that database transactions are processed reliably. While ACID is fundamental to relational databases (OLTP systems), it is also crucial in modern data engineering, particularly in data lakehouse environments, to ensure data integrity during complex batch and streaming processes.

*Atomicity* guarantees that a transaction is treated as a single, indivisible unit of work. It either succeeds completely or fails completely.

*Isolation* ensures that the concurrent execution of multiple transactions results in the same state that would have been achieved if the transactions had been executed sequentially. Transactions do not interfere with each other.

*Durability* guarantees that once a transaction has been committed (successfully completed), its changes are permanent and will survive any subsequent system failures (power loss, crashes, etc.)

### Incremental/delta Loads

Incremental/Delta Loads are a fundamental data engineering technique used to move only the data that has changed or is new since the last successful load, rather than reloading the entire dataset. This process is essential for efficiency, speed, and cost reduction in data pipelines.

In order for an incremental load to work the boundry between the data that has already been loaded and the new or modified data needs to be idenitified. There are three key steps:

Identify Changes (The "Delta"): The process determines which records in the source system have been added, modified, or sometimes deleted since the last load time.

Extract Only the Delta: The pipeline extracts only these identified changes (the "delta") from the source.

Apply to Destination: The delta records are loaded into the destination table, either by appending new records or updating/merging existing ones.

The most common method for tracking new or changed records is using a timestamp variable to understand when the pipeline was last sucessfully run - only records with a timestamp that is greater than the last run are loaded. 

### Idempotency

Idempotency is the property of an operation that ensures it produces the exact same result every time it's executed, regardless of how many times it runs. In data engineering, this means running an ETL/ELT pipeline or a specific transformation multiple times with the same input data will not result in duplicated data or inconsistent states, making pipelines safe to retry upon failure and ensuring data quality and reliability.

### Batching and Streaming

*Batch* and *Streaming* represent the two fundamental paradigms for handling data in data engineering. The choice whether to batch or stream data is driven primarily by the required latency and the volume/nature of the data.

Batch processing involves collecting and processing data in large, finite chunks at scheduled intervals (e.g., hourly, daily, weekly). Batch pipelines usually offer high latency, for example the results from the data is needed hours or days later. Batch pipelines are generally less complex to set up and are generally more cost efficient. For these reasons it is usually the prefered methodology.

Streaming processing involves handling data continuously, record-by-record, or in very small, rapid "micro-batches," immediately as it arrives. Data is processed event by event and this kind of pipeline is only usually used when a pipeline needs to have low latency, meaning results are needed within seconds. Streaming pipelines can be complex to handle due to having to deal with out of order data. 

## Data Modelling Methodologies

Data modelling is the process of designing how data is structured, stored, and related within a system. As a data engineer, it involves defining entities, attributes, and relationships to create efficient, scalable, and consistent database or data warehouse schemas. Good data models ensure data integrity, support analytics and reporting needs, and make it easier for teams to extract reliable insights from the data.

The type of data model you chose will depend on the usecase and data. Generally speaking you will need to choose between a normalised or denormalised appraoch. Typically normalised data suits OLTP (Online Transactional Processing) data and denormalised modelling suits OLAP (Online Analytical Processing). 

*OLTP*

Imagine you're processing sales data for a retailer. An OLTP system would record each sale as it occurs and would include current and recent data to understand operations daily, for example understanding if an order has been shipped that day. This suits a normalised structure. 

*OLAP*

The OLAP system would take the sales data to analyse trends or customer behaviour, so the data would be historical and should be easily aggregated, for example how many orders were shipped last month. This suits a denormalised structure. 

### Dimensional data modelling (denormalisation & the Kimball approach)

⚙️ Best Practices

* Always define grain first as it drives everything else

* Prefer denormalised dimensions for simplicity and performance.

* Keep the model extensible (graceful extensions).

* Use conformed dimensions for cross-domain reporting.

* Maintain data quality and consistency through surrogate keys and controlled ETL processes.

Below is a distilled summary of the “Dimensional Modeling Techniques” page from the [Kimball Group](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/) — it outlines the core concepts, best practices, and advanced patterns that underpin dimensional models in data warehousing. 


1. Foundations / Fundamental Concepts

The page emphasizes starting by gathering both business requirements and data realities — i.e. you need to align what the business needs to analyse with what the data sources can actually provide. 

To do this you would hold collaborative dimensional modeling workshops (with business stakeholders and domain experts) to refine and validate your design. 

Kimball define a Four-Step Dimensional Design process as detailed below.

Key concepts introduced:

- Business processes — what events or operations will be captured (e.g. orders, payments).

- Grain — the level of detail (i.e. the “atomic” level) that your fact records will represent.

- Dimensions — are descriptive context (who, what, where, when, how).

- Facts — the numeric measurements or metrics associated with the business process.

- Star schemas & OLAP cubes — dimensional models are often implemented in star schema layout (fact in center, dimensions around) and can support OLAP-style analysis.


![FactsDims](facts_dims.png)


- Graceful extensions — ability to evolve and extend the model over time without massive rework. 
Kimball Group

2. Fact Table Techniques

This section enumerates various patterns and considerations for fact tables: 

*Fact table structure — core layout and linking to dimensions*

Fact tables can be additive, semi-additive, non-additive  — whether measures can be summed across all dimensions (e.g. sales is additive, inventory balance is semi-additive).

Variants of facts:

* Transaction fact tables (each event recorded).

* Periodic snapshot fact tables (e.g. daily/monthly aggregates).

* Accumulating snapshot fact tables (e.g. tracking a process with start and end milestones).

* Factless fact tables (no numeric measure, just capturing an event or relationship).

* Aggregated fact tables / cubes and consolidated fact tables for performance optimizations. 


3. Dimension Table Techniques

This part addresses how to design the descriptive side of the schema through dimentions tables. 

Dimension structure should include the use of surrogate keys (artificial integer keys) rather than relying on natural keys.

![Dimention detail](dim_detail.png)

Special dimension types:

* Calendar date / time dimensions.

* Role-playing dimensions (same dimension used for different roles, e.g. Order Date vs Ship Date).

* Junk dimensions (grouping miscellaneous flags/attributes).

* Snowflaked dimensions (less common, normalized sub-dimensions). 

*Integration via Conformed Dimensions*

A key principle in the Kimball methodology is conformed dimensions, which are shared across multiple fact tables, ensuring consistency and enabling cross-subject “drill across.” 

*Slowly Changing Dimensions (SCD)*

Slowly Changing Dimensions (SCD) are methods for managing data that changes over time in a data warehouse, allowing you to track historical information instead of just keeping the current state.


Type 0: retain original value (do nothing)

Type 1: overwrite with new value (loses history)

Type 2: add a new row (full historical trace)

Type 3: add a new attribute (partial history)

Type 4: mini-dimension (offload historical attributes)

### Normalised modelling

Most data engineering use cases would fit under the structure of OLAP as data engineering processes more often than not are sufacing data for analytics rather than understanding transactions. Despite this distinction it is still worth having an understanding of normalised data modelling.

Normalisation is a systematic process of organising the fields and tables of a relational database to minimize data redundancy and improve data integrity. It ensures that data is stored logically and consistently.

⚙️ Key Goals of Normalization

* Reduce Redundancy: Store each piece of information only once, saving storage space.

* Improve Data Integrity: Since data is stored in one place, updates are easy and consistent, which reduces the risk of data anomalies (inconsistencies caused by insertion, update, or deletion).

* Efficient Writes (Updates): Changes only need to be made in a single location.

Normal Forms (The Rules)

Normalisation is achieved by following a series of rules called Normal Forms. The first three are the most common

![Normal Forms](normal_forms.png)


### One big table

One big table is an extreme normalisation strategy whereby all necessary data for an analyticsla purpose is stored in one really wide table. However unlike the normalised methid as described above which is largely used for transactional data, one big table is usually reserved for analytics. 

There are some pros to using the one big table method - it allows for extremely fast query execution and makes querying data much simpler. The downside is it lacks flexibility, this goes back to teh rule about keeping data models extensible. This is difficult to acheive with one big table. For eg say a customer moves to a new address - this address would need to be amended in every row that the customer appears, rather than just amending it directly in a dim table. 






