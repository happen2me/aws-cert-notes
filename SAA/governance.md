# Governance

### **Manage AWS Accounts with Organizations**

**Features**

- Set up logging account
  - best practice: set up an account dedicated to logging
- Programmatic creation
- Reserved Instances shared across all accounts
- Consolidated billing
- Service control policies

**SCP**

- Once implemented, it will be applied to every resource in the account

- SCP never gives permissions, but only throws
- Only way to restrict root account

### RAM (Recourse Access Manager)

**What can be shared**

- transit gateway
- VPC subnets
- license manager
- ...

**RAM v.s. Peering**

Across region: choose peering

Within: use RAM

### Cross-Account Role Access

**Tips**

- Use roles everywhere
- Auditing? Role!

### AWS Config

- Config is an inventory management and control tool.

- It allows show history of your infrastructure along with creating rules

- Query, Enforce, Learn 

AWS Config is a service that enables you to **assess**, **audit**, and **evaluate** the **configurations** of your AWS resources. Config continuously monitors and records your AWS resource configurations and allows you to automate the evaluation of recorded configurations against desired configurations.

**Exam tips**

- Standards -> Config
- Can track deleted resources
- Can use runbook to automatically remediate

### Offload Active Directory to AWS Directory

**Directory Service**

**Types**

- Managed MS AD
- AD connector: connect on-premise AD with AWS
- Simple AD: Linux samba AD

### Cost Explorer

### Trusted Advisor

Auditing

- Cost optimization
- Performance
- Security
- Fault Tolerance

