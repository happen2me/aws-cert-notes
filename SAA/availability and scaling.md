# High Availability and Scaling

### Horizontal and Vertical Scaling

**Vertical Scaling**: More powerful CPU / Bigger Storage and Memory

**Horizontal Scaling**: Many instances -> higher availability

**3 W's of scaling**

- What do we scale
- Where do we scale
- When do we scale

### Lauch Templates and Launch Configurations

**What are we scaling**

**Templates v.s. Configuration**

- **Lauch template**: specifies all needed **settings** that go into building an EC2 instances. It's a collection of settings. (you don't have to walk through EC2 creating page multiple times)
  - newer and better
  - More that just autoscaling
  - supports versioning
  - More granularity
- **Configuration**: 
  - only for autoscaling
  - immutable
  - limited configuration options

**Tips**

### Autoscaling Groups

A collection of EC2 instances treated as a group for scaling and management

**Steps**

1. Defin template
2. Networking and purchasing
3. ELB configure: can be registered behind a LB, can respect LB health checks
4. Scaling policies: min, max, desired
5. Notifications

**Autoscaling Restriction**

- Minimum
- Maximum
- Desired: How many do you want right now

### Autoscaling Policies

**Step Scaling**

![Step Scaling vs Simple Scaling Policies vs Target Tracking Policies in  Amazon EC2 - Tutorials Dojo](https://k2y3h8q6.stackpathcdn.com/wp-content/uploads/2020/06/Step-Scaling1.jpg)

**Warm-up and cool-down**

- Warmup: How long to pause health check and wait instances to come online
- Cooldown: Pause autoscaling for a period of time
- Avoid thrashing

**Scaling types**

- Reactive scaling
- scheduled scaling
- predicted scaling

### Scaling Relational Database

**4 ways to scale**

- Vertical scaling
- Scaling storage
- Read replicas: read-only copies
- Aurora serverless: offload scaling to AWS

### Scaling Non-relational Database

**Options**

- Provisioned
  - use case: predicatable workload
  - Effort: need review past use
  - Cost effective
- On-demand
  - Sporadic workload
  - no effort
  - Charged per read/write, not cost-effective

**Exam tips**

- Keep cost in mind
- Autoscaling is only for EC2
- Get ahead of the workload
- Bake AMIs to reduce build times