# Serverless Architecture

### Overview

**history of computing**

- Physical Datacenter
- Virtualization
- The Cloud
- Serverless

**serverless benefits**

- Leaving the management aside
- Ease of use
- event based: serverless brought online in response to events
- Billing Model: Pay as You GO

### Lambda

**Concept**: Serverless compute service

**Building a Function**

1. pick a supported runtime
2. attach roles to lambda functions
3. Networking
4. Define available resources (RAM, CPUs...)
5. define triggers that kicks Lambda off when an event occurs

**Limits**

- Maximus 15 minutes

### Container

Packages up code and its dependencies

**Terminology**

- **Dockerfile**: text document that contains all commands or instructions that will be used to build an image.
- **Image**: Immutable file that contains code, libraries, dependencies and configuration files
- **Registry**: Stores docker images for distribution
- **Container**: An running copy of the image

### ECS and EKS

**problems with containers**: Hard to manage while it scales out

**ECS (Elastic Container Service)**

- Manage container at scale
- ELB Integration
- Role Integration
- Ease of use

**Cross Platform Alternative - Kubernetes**

- Can be on-premise or in the cloud
- AWS managed version: EKS

**ECS v.s. EKS**

- ECS: Proprietary AWS container. Simple
- EKS: not all in AWS

### Fargate

A serverless compute engine for containers that works with ECS and EKS.

![AWS Fargate（サーバーやクラスターの管理が不要なコンテナの使用）| AWS](https://d1.awsstatic.com/re19/FargateonEKS/Product-Page-Diagram_Fargate%402x.a20fb2b15c2aebeda3a44dbbb0b10b82fb89aa6a.png)

**EC2 v.s. Fargate**

- EC2
  - responsible for underlying OS
  - can use EC2 pricing model
  - suitable for long running containers
  - Multiple containers can share a same host

- Fargate
  - No access to OS
  - Pay based on resources allocated and run time.
  - Suitable for short running tasks
  - Provides isolated environments

**Fargate v.s. Lambda**

- Fargate
  - more consistent workload
  - docker access gives greater level of control by developers
- Lambda
  - better for unpredictable or inconsistent workload
  - Perfect for applications that can be expressed as a function

### EventBridge (CloudWatch Events)

A serverless **event bus**.  It allows pass events from source to endpoints.

**Creating a rule**

1. Define pattern: event-driven, scheduled
2. Select events: customer events? AWS-based events?
3. Select target: what to do when...?
4. Need to **tag** everything

**Tips**

- A common use case is to trigger Lambad functions when AWS API call happens
- Lambda loves roles
- Any AWS API call can trigger EventBridge rule