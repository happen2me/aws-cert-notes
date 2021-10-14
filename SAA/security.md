# Security

### DDoS

**DDoS**: Distributed Denial of Services

- Can be achieved by packet floods, reflection, amplification, or use of large botnets.

**Layer 4 DDoS**

SYN Flood: many SYN but ignore SYN-ACK, many half-opened connection on server side uses up resources.

**Amplification Attack**

Attacker send third-party server a request using a spoofed IP address. Many legimate traffic are sent to the spoofed address. (Response are much larger than request, so "amplification")

**Layer 7 Attack**

A webserver receives floods of GET or POST

### CloudTrail

**CloudTrail **- CCTV for AWS account, records all API calls to account.

- record console actions and AWS API calls.

- WHAT are logged:
  - metadata of API call
  - identify of caller
  - time
  - caller's IP
  - request parameter
  - response elements

### Shield

Free DDoS protection, protect **layer 3** and **layer 4** only.

### WAF - Web Application Firewall

Works at **layer 7**

Protect against:

- DDoS
- SQL injection
- Cross-site scripting
- block specific countries or IP addresses

### GuardDuty

- Use AI to learn normal behavior

- Update database of known malicious sites

- Monitor CloudTrail logs, VPC flow logs and DNS logs.

- Findings in GuardDuty dashboard

### Macie

- Use AI to analyze data in S3, helps identify PII, PHI, and finacial data

- Creat for HIPAA and GDPR

- Works with EventBridge and automated remediation actions.

### Inspector

Perform **vulnerability scans** on EC2 and VPCs (host assesment and network assessment)

### KMS and CloudHSM

KMS: create and control keys

- Need CMK

**Control Permission**

- Use key policy: full scope of CMK defined in a doc.
- IAM + Key Policy
- Grants + Key Policy

**KMS vs. CloudHSM**

KMS: 

- shared underlying hardware
- Automatic key rotation
- Automatic key generation

CloudHSM

- Dedicated HSM
- Full control of users, groups, keys
- No automatic key rotation

### Scrects Manager

- Store secret
- Application use Secret manager API
- When enabled, Secrets manager **immediately** rotate keys

### Parameter Store

Free

Up to 10,000 records

### Presigned URL

Share private S3

```
aws s3 presign s3://xxxxx/xxxx
```

### Advanced IAM Policies

- default deny
- explicity deny > else
- AWS can join policies

