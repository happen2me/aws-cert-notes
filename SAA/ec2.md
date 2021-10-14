### EC2 Pricing

- On-demand
- Reserved
- Spot: purchase unused resources at a discount
- Dedicated: most expensive

Special licensing -> use dedicated server

### Metadata and User Data

- Retrieve metadata

  `curl http://ip/latest/meta-data/`

- User data
  are just bootstrap scripts

### Networking with EC2

- ENI (Elastic Network Interface)

  Basic networking

- ENA (Elastic Network Adapter / Enhanced Networking)

  supports up to 100Gbps

- EFA (Elastic Fabric Adapter)

  for HPC on EC2

### Placement Groups

Logical grouping of EC2 instances.

- Cluster Placement Groups
  - Grouping of instances within AZ
  - **Can't** span across AZ

- Spread Placement Groups

  - A group of instances that are each placed on **distinct** underlying hardware

  - For applications that have a small number of critical instances that should be kept separate from each other
  - Used for individual instances

- Partition Placement Groups

  - Each partition is on different set of racks -- failure safe

**Exam tips**

- Cluster: low network latency, high throughput
- Spread: individual critical EC2 instances
- Partition: Mutiple EC2 instances; HDFS, HBase, and Cassandra

### Spot Instances

**Pricing**

- Hourly spot price varies.
- Set a maximum price, instances will be terminated/stopped if price goes over it.
- Spot block: don't terminate the machine even if it goes over (1~6 hours)

**Usecase**

- HPC
- Big data
- CI/CD
- Image/Media rendering

**Not for**

- Persistent workloads
- Critical jobs
- Database

**Spot fleets**

A collection of spot instances and maybe on-demand instances. It will try to match target capacity with price limits.

### Exam Tips

**Security Groups** -- Simplify EC2 instances security policies 



