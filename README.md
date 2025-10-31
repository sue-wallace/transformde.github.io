## Contents - testing github pages

[1. Learning Pathways](#1.-Learning-Pathways)

[2. Useful resources](#2.-Useful-resources)

## 1. Learning Pathways

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

## 2. Useful resources

## 3. Common Architectural patterns in data engineering

### Medallion Architecture

The Medallion Architecture is a data design pattern that structures data pipelines into three logical layers - Bronze, Silver, and Gold. The aim of this is to improve data quality, reliability, and reusability across an organisation. This architecture helps data teams manage the gradual refinement of raw data into business-ready insights. Each layer represents a different stage of data curation: Bronze holds raw, unprocessed data ingested from various sources; Silver contains cleaned and conformed data, where schema enforcement, deduplication, and validation occur; and Gold provides fully refined, aggregated, and business-oriented data models optimized for analytics, reporting, and machine learning.

By layering data transformations in this way, the Medallion Architecture promotes modularity, governance, and trust in the data ecosystem. It encourages teams to apply consistent data quality checks and transformation logic at defined points, enabling clear data lineage and simplifying troubleshooting. Additionally, it supports a test-driven and incremental development approach — new logic or data sources can be introduced at the Bronze or Silver layer without disrupting downstream users consuming Gold datasets. The result is a scalable, maintainable framework that supports both operational efficiency and analytical agility in modern data platforms.

[Microsoft: What is the medallion lakehouse architecture?](https://learn.microsoft.com/en-us/azure/databricks/lakehouse/medallion)

