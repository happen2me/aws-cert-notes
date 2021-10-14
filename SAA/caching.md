# Caching

### Overview

**Internal Cache**: i.e. Additional layer on top of database

**External Cache**: i.e. CDN

### CloudFront

**Using Edge Locations** - AWS CDN

**Some Features**

- Global: can't pick countries
- Non-aws Endpoint: support
- Can force expiring

**Tips**

- commonly used to front s3



### ElasticCache and DAX

#### **Elastic Cache**

AWS managed memcache and redis

**Memcache**

- Simple database cache
- Not a database by itself
- No failover or multi-AZ
- No backups

**Redis**

- Cache but also a database by itself
- Muti-AZ and failover
- Backups

#### **DynamoDB Accelerator (DAX)**

In memory cache for DynamoDB, lives inside VPC

### Fix Global Caching Issue with Global Accelerator

![AWS Global Accelerator（アプリケーションの可用性とパフォーマンスを向上）| AWS](https://d1.awsstatic.com/Networking/AGA-CaaS-Usecase-2000px.3844c1a8a54857b50eba690663a7885fa94e4bc5.png)

- Mask complex architecture
  - i.e. User cache GA's IP instead of the actual ALB. This solves **IP Caching** problem
- Speeds things up
- Weighted pools

**How to update?**

- Usually by setting TTL