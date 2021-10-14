# Elastic Block Store

### Overview

**Definition**

Storage Attached to EC2.

**Types**

- General Purpose SSD (gp2 & gp3)

  suitable for boot, high performance at low cost
  1000~3000 IOPS

- Provisioned IOPS SSD (io1 & io2)
  - 64000 IOPS
  - For IO intensive application (OLTP)
- Throughput Optimized HDD (st1)
  - Lowcost
  - 40 ~ 250 MB/s per TB
  - Max 500 MB/s per volume
  - Frequently accessed, throughput intensive application
  - For big data, data warehouse, ETL, log processing
  - cannot be boot volume
- Cold HDD (sc1)
  - Lowest cost option
  - 12 ~ 80 MB/s per TB

**IOPS vs. Throughput**

- IOPS measures number of read and write operations per second

- Throughput measures number of bits read and write

### Volumes and Snapshots

**Volumes**: 

- virtual hard disks
- in the same AZ as EC2 instances
- resize on the fly

**Snapshots**

- exists on s3
- snapshot volume. 
- Point-in-time copy.
- Incremental! First snapshot takes longer.

**Tips**:

- Consistent snapshot: stop the instance then capture
- Encrypted snapshots: snapshots of encrypted EBS volume will be encrypted.
- Sharing snapshots: can be shared within the same region. (For crossing region: copy snapshots)

### EBS Encryption

- Encrypt an unencrypted volume
  - Create a snapshot of it
  - Copy and encrypt
  - Create am AMI from the snapshot
  - Use AMI to launch encrypted instance

### EC2 Hibernation

**Concepts**

- Suspend-to-disk
  Hibernation save contents from EC2 RAM memory to EBS disk
- Restarted - RAM restores from EBS
- RAM should be less than 150G

**Effect:**

- faster boot

### EFS (Elastic File System)

**Concepts**

- Managed NFS (network file system) that can be mounted on **many** EC2 instances
- Cross AZ
- High available and scalable, but expensive
- NFSv4 protocol
- Read-after-write consistency

**Use case**

- Content management - easy share
- Webserver - single folder

**Storage Tiers**

- Standard
- Infrequent accessed

### FSx

**FSx for Windows**

- runs Windows Server Message Block (SMB)-based file system

**FSx for Lustre**

Fully managed file system optimized for **compute-intensive** workloads

- HPC, ML
- Media Data Processing
- Can directly save data to S3

### AMI (Amazon Machine Images)

Provides information about creating instances, it's a **blueprint** for EC2 instances.

**5 base**

- region
- OS
- Architecture (32/64)
- Launch permission
- Storage for root device (root device volume)

**EBS-backed AMI**

Root device created from EBS snapshot

- Can be stopped. Root volume can be kept (deleted by default)

**Instance store based AMI**

Root device created from a template stored in Amazon S3

- Cannot be stopped! Ephemeral

**EBS Exam Tips**



