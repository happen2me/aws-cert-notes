# Decoupling Workflows

### Overview

- Talk to a fleet of instances instead of a single machine

### SQS (Simple Queue Service)

**Poll based messaging**

Producer-consumer model

**SQS**

A message queue that enables asynchronous processing of work

**Important Setting**

- Delivery delay: default 0, up to 15 minutes. (Hide the message until delay times out)
- Message size: up to 256 KB of text
- Encryption: Encrypted  in transit, not at rest by default
- Message retention: default 4 days, can be 1 minute to 14 days. Messages are discarded after this.
- Long vs. short: 
  - Short: default, consumer actively query again and again (waste CPU and money)
  - Long: connect and wait (should pick this)
  - Queue depth: can be triggered for autoscaling

**Visibility timeout**

After a backend instances polls the messaged, it is locked for i.e. 30 seconds. The message is not visible during this period. If the processing is unsuccessful, the message reapears, otherwise it's deleted. This makes sure messages don't get lost.

### Sidelining Messages with Dead-Letter Queue

**Dead-letter queues**

- Problem: A message contains mistakes, no instance can process it correctly. So it reappears again and again.

- Solution: Set up a DLQ to sideline this kind of messages
  - DLQ is just also another standard queue
  - 'Maximum Receives' specifies how many times to retry before sending it to DLQ

Tips: set up alarms for queue depth

### FIFO Messages

**ordering**

- Standard: may be out of order and duplicated
  - Best effort
  - Unlimited transactions per second
- FIFO
  - 300 messages per second
  - Fields:
    - Message Group ID (message within a group will be ordered)
    - Message Deduplication ID

### SNS (Simple Notification Service)

**Push based messaging**

**SNS Settings**

- Subscribers
- Message size: 256 KB text
- Support DLQ

### Fronting Application with API Gateway

**API Gateway**: A fully managed service that allows publish, create, maintain, monitor and secure APIs. It's a safe front door.

**Features**

- Security: allows attaching WAF (web application firewall)

- Stop abusing: 
- Ease of use

