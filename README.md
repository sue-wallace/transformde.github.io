Add X logo here

Welcome to X and the data engineering playbook! The purpose of this pack is to acclimatise you to X's landscape as a data engineer and to help you understand commonly used approaches in data engineering.

## Contents 

X's Structure

The general X structure can be found in Bamboo under people > org chart. The data engineering team meets every two weeks on a Monday afternoon. 

Could ask the team to write a short bio each here. 

[Learning Pathways](#Learning-Pathways)

[Software and tech stack](#Software-and-tech-stack)

[Software development best practice](#Software-development-best-practice)

[Common architectural patterns in data engineering](#Common-architectural-patterns-in-data-engineering)

[Data Modelling](#Data-Modelling)

[Data engineering techniques](#Data-engineering-techniques)

[Batching and Streaming](#Batching-and-Streaming)

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

* [Training track for data engineers](https://learn.palantir.com/page/training-track-data-engineer)

## Software and tech stack

Add in any useful resources for new data engineering starters here.


### Languages

As a data engineer you should have a good understanding of python/pyspark and sql/sqpark sql. You should also have a good understanding of [spark](https://www.databricks.com/glossary/what-is-apache-spark) and distributed compute. 

We dont have admin rights on our devices but any apps that you will need should be available in the company portal for download. If an app that you need is not in the company portal then you should contact IT and ask if they can add it.

### Coding style Guide


### Technology

Databricks

Azure Synapse Analytics and ADF

Commonly used Azure components

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

### Concepts: Warehouses, lakes and lakehouses

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

![MedallionArch](medallion.png)

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

For transient errors due to things like network issues or cloud resource scaling you can use backoff strategies which give an exponential delay between retries. This is essentially how ling teh pipeline should wait before conducting a retry after each failed attempt. 

You can also store error metadata (pipeline name, activity, error message, timestamp) in a central log table for audit and debugging.

### Partitioning

Partitioning is an important concept in data engineering as it directly affects query performance, scalability, and cost in big data systems.

Partitioning means dividing a large dataset into smaller, more manageable chunks (called partitions) based on the value of one or more columns — typically something like date, region, or customer_id.
Instead of storing all records in one massive file or table, the data is split across directories or files that correspond to those partition values.

Partitioing also means that distrobuted systems like Spark can handle the data more effectively as each partition can be processed in parallel. You can also easily drop, reload, or archive specific partitions without touching the rest of the data.

### ETL/ELT

### ACID Transactions

## Data Modelling

Data modelling is the process of designing how data is structured, stored, and related within a system. As a data engineer, it involves defining entities, attributes, and relationships to create efficient, scalable, and consistent database or data warehouse schemas. Good data models ensure data integrity, support analytics and reporting needs, and make it easier for teams to extract reliable insights from the data.



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

Special dimension types:

* Calendar date / time dimensions.

* Role-playing dimensions (same dimension used for different roles, e.g. Order Date vs Ship Date).

* Junk dimensions (grouping miscellaneous flags/attributes).

* Snowflaked dimensions (less common, normalized sub-dimensions). 

4. Integration via Conformed Dimensions

A key principle is conformed dimensions: dimensions shared across multiple fact tables, ensuring consistency and enabling cross-subject “drill across.” 
Kimball Group

Concepts like shrunken rollups, drilling across, bus architecture (data warehouse bus), and bus matrix are introduced as architectural tools to manage integration across domains. 
Kimball Group
+1

Also mentions how to maintain consistency across subject areas (the “value chain”). 
Kimball Group

5. Slowly Changing Dimensions (SCD)

The page covers various techniques for managing dimension attribute changes over time: 
Kimball Group

Type 0: retain original value (do nothing)

Type 1: overwrite with new value (loses history)

Type 2: add a new row (full historical trace)

Type 3: add a new attribute (partial history)

Type 4: mini-dimension (offload historical attributes)

Type 5, 6, 7: hybrid or combined approaches (mixing strategies) 
Kimball Group

6. Dimension Hierarchy Techniques

Techniques for handling hierarchies in dimensions:

Fixed-depth positional hierarchies (e.g. levels known ahead).

Slightly ragged / variable-depth hierarchies (some branches shorter).

Ragged hierarchies (variable depth, “holes” in levels). 
Kimball Group

7. Advanced Fact Table Techniques

This section touches on more sophisticated modeling patterns for fact tables: 
Kimball Group

Using surrogate key in fact tables.

Centipede fact tables (a kind of fan-out structure).

Treating numeric values as attributes vs facts.

Lag / duration facts (e.g. time between events).

Header/line fact tables (for hierarchical facts, e.g. invoices + line items).

Allocated facts (e.g. allocating overheads) and profit & loss tables.

Handling multiple currencies, multiple units of measure.

Year-to-date facts, multipass SQL to avoid fact-to-fact joins.

Timespan tracking, late arriving facts. 
Kimball Group

8. Advanced Dimension Table Techniques

Finally, the page mentions advanced patterns for dimensions: 
Kimball Group

Dimension-to-dimension table joins (dimension relationships).

Multivalued dimensions and bridge tables (e.g. a fact could be associated with multiple members of a dimension).

Behavior tag time series, behavior study group, aggregated facts as dimension attributes.

Dynamic value banding, text comments, multiple time zones, measure type dimensions, step dimensions, hot-swappable dimensions, abstract / generic dimensions, audit dimensions, and late arriving dimensions.

### Other types of modelling & one big table

## Batching and Streaming

## Data engineering techniques

### Best practice

### Incremental/delta Loads

### Idempotency

