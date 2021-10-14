# CloudWatch

### Overview

A monitoring and observability platform to give insights into our AWS architecture,

**Features**

- System Metrics: out of the box. 
- Applciation Metrics: By installing CloudWatch agent. Get info from inside of EC2 instances/application.
- Alarms

**Metrics**

- Default
- Custom: use installed agent
- Standard: 5 minutes; Detailed: 1 minutes

### Application Monitoring with CloudWatch Logs

Allows you monitor, store and acess log files

**Three key terms**

- **Log Event**: The record of what happened, contains timestep and the data.
- **Log Stream**: A collection of log events from the same source.
- **Log Group**: A collection of log streams.

**CloudWatch Log Features**

- Filter patterns
- CloudWatch Logs Insights: query using SQL like 
- Alarms

### Hands-on

cloudwatch agent:

```bash
yum install amazon-cloudwatch-agent
```

**Tips**

- Logs we need to process: go to cloudwatch
- We don't: go to S3

- Alarms: can be triggered when patterns matched