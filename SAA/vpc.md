# Virtual Private Cloud

### Overview

**Fully customizable network**

- Web tier: public facing
- Application tier: private subnet, speaks to web tier and database tier
- Database tier: Private subnet. Can only speak to application tier.

**What can we do with VPC**

- Launch instances into a subnet
- Assign custom IP
- Configure route tables between subnets
- Attach internet gateway

- Access Control List (NACL can block some addresses)

**Default VPC & custom VPC**

- Default VPC
  - user-friendly
  - have a route out to the internet
  - Each EC2 has both a public and private IP address
- Custom
  - fully customizable
  - takes time to set up

**Tips**

- one subnet is always in one AZ

### Demo: Provisioning a VPC

### NAT Gateway

**definition**: NAT enable instances in a private subnet to connect to the internet while preventing the internet from initiating a connection with those instances.

**Facts**

- Redundant inside the AZ
- Starts at 5Gbps and scales up to 45 Gbps
- No need to patch
- Not associated with security groups
- Automatically assigned a public IP address

**Security groups**

- Virtual firewalls for an EC2 instance
- security groups are **stateful** -- response traffic is always allowed, regardless of in/outbound rules.
- **You can specify allow rules but not deny rules**
- There are quotas on the number of security groups that you can create per VPC, the number of rules that you can add to each security group, and the number of security groups that you can associate with a network interface. 

**ACL (Access Control List)**

- First line of defense
  - An optional layer acts as a firewall  for controlling traffic in and out of a VPC
  - It can add another layer of security on top of security groups

**Overview of NACL**

- **Default NACL**: allow all inbound and outbound
- **Custom NACL** denies all out- and inbound traffic by default
- **Subnet Association**: Each subnet is associated with a NACL
- **Block IP address**: Use NACL, not SG

**Exam tips**

- each subnet can have only one ACL attached
- evaluated in order, starting with **lowest** number rule
- In/outbound, allow/deny
- Stateless!

### VPC Endpoints

**Concept**

- VPC endpoints enable you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink
- Instances in VPC do not need a public IP to communicate with AWS services
- Traffics between VPC and AWS services do not leave AWS network
- Endpoints are virtual devices. They are horizontally scaled, redundant and highly available VPC components.

**Types**

- Interface Endpoint: is an *elastic network interface with a private IP address* that serves as an entry point for traffic headed to a supported services. They support a large number of AWS services.
- Gateway Endpoint: Similar to NAT gateways, a gateway endpoint is a *virtual device that you provision*. It supports S3 and DyanmoDB.

**Exam tips**

- Use case: connect AWS services without leaving Amazon internal network

### Network Privacy with AWS PrivateLink

**Open application to another VPC**

- Open the VPC to the Internet (risky)

- Use VPC Peering

  - Manage many peering relationship
  - everything in VPC exposed

- Best: PrivateLink

  Requires a Network Load Balancer on the services VPC and an ENI on the customer VPC

  ![AWS PrivateLink – Amazon Web Services](https://d1.awsstatic.com/product-marketing/PrivateLink/privatelink_how-it-works.a8ae3df6830296337b30a7c4e75d8eed403eb5d2.png)

### VPC Peering

**Multiple VPCs**

- production VPC
- content VPC
- Intranet

**Peering**

- Allow connect VPC to another via direct network route and private IP addresses
- Instances behaves as if they were on a same VPC
- Can peer within or across accounts
- Star topological
- Can peer between regions

**Notes**

- Transitive peering NOT supported
- No overlapping CIDR address ranges

### VPN CloudHub

- Connect multiple sites together

  - Hub-and-spoke
  - Operate over public network

  ![Providing secure communication between sites using VPN CloudHub - AWS  Site-to-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/images/AWS_VPN_CloudHub-diagram.png)

### Connect On-Premises with Direct Connect

AWS Direct Connect is a cloud service that establishes a dedicated network connection from your premise to AWS.

- Features
  - reduce network cost
  - increase bandwidth
  - more consistent network experience

**Types**

- Dedicated connection: Physical ethernet connection
- Hosted connection: Physical ethernet connection hosted by AWS partners

### Simplifying network with Transit Gateway

Connects VPCs and on-premise networks through a central hub

![AWS Transit Gateway_VPC虚拟私有云链接服务-AWS云服务](https://d1.awsstatic.com/product-marketing/transit-gateway/tgw-after.d85d3e2cb67fd2ed1a3be645d443e9f5910409fd.png)

**Facts**

- transitive peering
- Hub-and-spoke model
- works on region-basis, can cross regions
- can cross accounts with RAM (resource access manager)

**Tips**

- Use route tables to limit connection
- works with Direct Connect and VPN
- supports IP broadcast

## Exam Notes

**Policy**

- **Resource-based policies** are attached to a resource. For example, you can attach resource-based policies to Amazon S3 buckets, Amazon SQS queues, and AWS Key Management Service encryption keys. 

- **Identity-based policies** are attached to an IAM user, group, or role. These policies let you specify what that identity can do (its permissions). For example, you can attach the policy to the IAM user named John, stating that he is allowed to perform the Amazon EC2 RunInstances action. 