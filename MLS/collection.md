# Data Collection

### Terminologies

**Data Warehouse**

[What is data warehouse](https://aws.amazon.com/data-warehouse/)

- A data warehouse is a central repository of information that can be analyzed to make more informed decisions.
- Data flows into a data warehouse from transactional systems, relational databases, and other sources, typically on a regular cadence.
- **With preprocess**

**Data Lake**

[What is data lake](https://aws.amazon.com/big-data/datalakes-and-analytics/what-is-a-data-lake/)

- A data lake is a centralized repository that allows you to store all your structured and unstructured data at any scale.

- You can store your data as-is, without having to first structure the  data, and run different types of analytics—from dashboards and  visualizations to big data processing, real-time analytics, and machine  learning to guide better decisions.

- **Without preprocess**: Just dump

![Data Lake vs. Data Warehouse - Working Together in the Cloud | Panoply](https://panoply.io/uploads/data-warehouse-vs-data-lake-2.png)

### AWS Data Store

- S3
- RDS
- DynamoDB
- Redshift
- Timestream
- Document DB - migrate mongoDB

**Migration**

- Data Pipeline

  - Transfer between different data source
  - Transfer from on-premise
  - i.e. RDS -> S3: Specify a SqlActivity and places results into S3

- DMS (Data Migration Service)

  - Transfer between transactional database
  - i.e. On-premise MySQL -> S3

- AWS Glue (Load data from one source to another)

  - Fully managed ETL

  - Data catalog:

    When migrate data onto S3, data catalog create a skeleton of the dataset

    - Database: 
    - Crawler

  - i.e. Unstructured logs: Create custom classifier and output results to S3

  - i.e. Clustered Redshift -> S3: Query results -> CSV -> DataCatalog describes data and load it to S3

**Helper tools**

- EMR (integrates many big data software)
- Athena (run SQL on S3 data)
  - Difference between **Athena** and Redshift **Spectrum**
  - Redshift Spectrum
    - Query S3
    - Must have Redshift Cluster
    - Made of existing Redshift Customers
  - Athena
    - Query S3
    - No need for Redshift Cluster
    - New customers quickly query S3



### Exam Tips

## Streaming Data Collection

### Kinesis Data Streams

**1. Data Producer** creates streams of data

**2. Kinesis Streams**:

- Shard: a container that holds data we want to send to AWS

**3. Data Consumers** process data

- EC2, Lambda, Kinesis Data Analytics, EMR Spark

**4. Storage and Analyzation** S3, DynamoDB, RedShift, BI tools

**Shards**

- One shard contains a sequence of records.
- Default limit: 500 shards, can be increased
- A data record is the unit of data captured
  -  partition key (same within a shard)
  - sequence number 
  - data blob (up to 1MB)
- Transient data store: retention perioid is between 24h to 7 days

**How to get data into Shards / Kinesis Stream?**

- Use Kinesis Producer Library (KPL) (**Java**): a lib that allows data writes to Kinesis Data Stream
- Kinesis Client Library: for consumer applications
- Kinesis API (AWS SDK): Can do the same with above, but lower level API

### Kinesis Data Firehose

Amazon Kinesis Data Firehose is the easiest way to reliably load  streaming data into data lakes, data stores, and analytics services. It  can capture, transform, and deliver streaming data to Amazon S3, Amazon  Redshift, Amazon OpenSearch Service (successor to Amazon Elasticsearch  Service), generic HTTP endpoints, and service providers like Datadog,  New Relic, MongoDB, and Splunk. [src](https://aws.amazon.com/kinesis/data-firehose/?kinesis-blogs.sort-by=item.additionalFields.createdDate&kinesis-blogs.sort-order=desc)

**When to use**

- easily connect streaming data
- preprocessing is optional
- final destination is s3
- data retention is not important
- Typical scenario:
  - stream and store data from devices
  - create ETL jobs on streaming data

### Kinesis Video Stream

- Process real-time video stream
- Batch-process and store video stream
- Feed stream data into AWS services

### Kinesis Data Analytics

Read and process streaming data in real-time	