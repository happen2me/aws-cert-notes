# Chapter 8. Databases

### Relational Database Service (RDS)

**Advantages**

- Up and run in minutes
- Multi AZ
- Failover capability
- Automated backup

**Use case**

For **OLTP** (online transaction processing)

**Exam Notes**

- Amazon RDS Multi-AZ deployments provide enhanced availability and durability for RDS database (DB) instances, making them a natural fit for production database workloads.
- read replicas are not updated synchronously.

### Aurora

**Basics**

- 10GB - 128TB
- Minimum 3 AZ, 6 copies

**Aurora Serverless**

On-demand MySQL and PostgreSQL compatible editions of Aurora. Suitable for spike workloads.

### DynamoDB

**Basics**

- Fast and reliable **No-SQL** database.
- Supports document & key-value model
- Stored on SSD
- Spread across 3 DC
- Eventual consistent read (default)
- Supports strong consistent reads

**Eventual consistency & strong consistency**

- Eventual: Copies of data reach in one second.
- Strong: read after write consistency. Returns results that reflect all writes.

**DynamoDB Accelerator (DAX)**

- In-memory cache DB for DynamoDB
- Reduce request time from milliseconds to microseconds

**DynamoDB Transaction**

- **ACID for DynamoDB**
  - All or nothing
- **Use case**
  - finacial transactions
  - Manage orders
  - Multiplayer games

**DynamoDB Backups**

- Zero impact on performance and availability

**Point-in-time Recovery**

- Protect against accidental writes or deletes
- Restore to any point in the last 5 minutes to 35 days
- Incremental backups
- Not enabled by default

### DynamoDB to Global

**Streams**

- Time-ordered sequence of time-level changes in a table
- Like a FIFO list of recent data, splited in shards
- Stored for 24 hours
- Inserts updates and deletes

**Global Tables**

**Concept**: Managed multi-master, multi-region replication

- For globally distributed application
- Based on DynamoDB streams
- Multi-region redundancy for **disaster recovery** or **high availability**
- Replication latency less than 1 seconds