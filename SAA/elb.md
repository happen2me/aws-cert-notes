# Elastic Load Balancer

### Overview

Automatically distributes incoming application traffic to multiple targets.

**Types**

- Application Load Balancer (Intelligent Load Blaner): Suitable for HTTP and HTTPS. Works at layer 7.
- Network Load Balancer (Performance Load Balancer): Works at layer 4, can handle millions of request per second with ultra-low resource cost
- Classic Load Balancer: Legacy LB. Can LB HTTP(s) and use level-7 specific features.

**Health Checks**

- Periodically send requests to LB's registered instances to test their status. (InService / OutOfService)

- LB only routes to healthy instances

### Application Load Balancer

**Layer 7 Load Balancing**

After LB receives a request, it evaluates  the listener rules in priority order to determine which rule to apply, and then select a target from target group.

**Listener**

- A listener checks requests using protocal and port you set.

- You define **rules** on how LB routes

- Each rule: priority, actions, conditions

**Path-based Routing**

**Limitations of ALB**

- only supports HTTP and HTTPS

Note:

- For https listener, LB decrypts requests and route them to targets

### Network Load Balancer

**Layer 4 LB**

**Listener**

A listener on NLB checks connection requests and forward the requests to the target group. There **no** rules.

**Target Groups**

routes requests to one or more registered targets

**Ports and Protocols**

- Protocols: TCP, TLS, UDP, TCP_UDP
- Ports: any

**Encryption**

You can use TLS listener to off load encryption to LB

**Use case**

TCP traffic where extreme performance matters

Use protocols not supported by ALB

## Classic Load Balancer

**X-Forwarded-For**

Traffics from LB contains only IP of LB/proxy, X-Forward-For can see original IP address.

**Gateway Timeouts**

If your application stops responding, the CLB responds with 504 (Web server / database have issue, but CLB works)

**Sticky Session**

- CLB route each request independently to registered EC2 instance with the smallest load.

- Sticky session allows bind a user's session to a specific EC2 instance
- It can also be used with **ALB**, but traffic is routed at the target group level.

### Leaving the LB with Deregistration Delay

Allow LB to keep existing connections open if the EC2 instances are de-registered or become unhealthy.

This enables the LB to complete in-flight requests made to instances that are de-registering or unhealthy

