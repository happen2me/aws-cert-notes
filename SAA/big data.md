# Big Data

### Overview

**3 Vs**

- Volume
- Variety
- Velocity

**Redshift**

- Fully managed, peta-byte scale, **relational** database.

- For BI (Business Intelligence)

- Backups are kept for 1 day by default, but this can be raised up to 35 days at most.
- Redshift does not support multi-AZ deployments
- Redshift can hold up to 16 Petabytes of data per cluster

### EMR (Elastic MapReduce)

**ETL** - Extract, Transform, Load

**EMR** - AWS's ETL tool

**EMR Architecture**

- Lives inside a VPC
- Can use like spot EC2 instances

### Kinesis

Ingest, process and analyze real-time streaming data.

**2 versions**

- Data Stream

  - Real-time streaming for ingesting data
  - You are responsible for creating consumers and scaling the stream.
  - No auto scaling, you need to determine how many shards you need

  ![Amazon Kinesis Data Streams（リアルタイム分析向け大規模データを収集）| AWS](https://d1.awsstatic.com/Products/product-name/diagrams/product-page-diagram_Amazon-Kinesis-Data-Streams.074de94302fd60948e1ad070e425eeda73d350e7.png)

- Data Firehose

  - Data transfer tool to get information to S3, RedShift, ElasticSearch, or Splunk
  - Near real-time (within 60s)
  - Plug and play with AWS architecture
  - Auto-scaling

  ![Amazon Kinesis Data Firehose（ストリーミングデータをデータストアや分析ツールにロード）| AWS](https://d1.awsstatic.com/architecture-diagrams/product-page-diagram_Amazon-Kinesis_Data_Firehose%402x-updated.d7e297e0f79ee1a2dfe22d105fd53195e43ccfa4.png)

**Kinesis Data Analytics**

Analyze data using standard SQL

- Easy
- No servers
- Pay for what you used

**Kinesis v.s. SQS**

- SQS: easy to use, not real-time
- Kinesis: complicated, offer real-time

### Athena and AWS Glue

**Athena**: An interactive query service to analyze data in **S3** using **SQL**.

- Directly query data in S3 bucket without loading it into a database.
- Serverless SQL solution! (can be used to query logs stored in bucket)

**Glue**: A **serverless data integration** service that helps discover, prepare and combine data. It allows perform **ETL** workloads without managing underlying services.

**Use them together**

![Athena で AWS Glue を使用するときのベストプラクティス - Amazon Athena](https://docs.aws.amazon.com/ja_jp/athena/latest/ug/images/glue_crawler.png)

### QuickSight

Fully managed BI **data visualization** service. It allows easily create dashboards.

### ElasticSearch

- AWS manged version of open source ElasticSearch. 
- Search over stored data and analyze the result.
- Often used in ElasticSearch, Logstash, Kibana (ELK) stack.

![Amazon Elasticsearch Service（Elasticsearchを簡単にデプロイ、保護、運用）| AWS](https://d1.awsstatic.com/re19/ESS_HIW.db99588614cbf44e2d62ef9c9c173ebfe41e2834.png)

