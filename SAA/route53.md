# Route 53

### Overview

**TTL**: The length that a DNS record is cached on either the resolving server or the user's own local PC

**CNAME**: Canonical Name. Resolve one domain name to another.

- Can't be used for naked domain names

**Alias Record (only in AWS)**: Maps resource record in your hosted zone to other AWS services .

- Can be used for a naked domain name.

**SOA Records**: The DNS 'start of authority' (SOA) record **stores important information about a domain or zone such as the email address of the administrator**, when the domain was last updated, and how long the server should wait between refreshes.

### Simple Route Policy

You can only have one record with multiple IP addresses. If you specify multiple values in a record, route 53 will returen all values in a random order.

### Failover Routing Policy

Used when you want to create an active/passive set up.

When the passive site fails, route 53 failover policy will automatically route to the passive site. This is achived with health status check.

### Geolocation Routing Policy

Configured in records.

### Geoproximity Routing Policy

**Route 53 traffic flow**

Can build route system uses a combination of:

- Geographic location
- latency
- Availability to route traffic

**Geoproximity Routing**

- lets route 53 routes based on geo location and your resources
- can control route more/less traffic with **bias** value

### Latency Routing Policy

Route based on the lowest network latency for your end user

**Latency resource record set**

### Multivalue Answer Routing

- Route 53 returns multiple values such as IP address in response to DNS queries

- resembles simple routing, but can do healthy checking: returns only values for healthy resources

### Weighted routing policy

10% -> A, %90 -> B

**Health Checks**

You can set health check on individual record sets

Records fails health checks will be removed until it passes it



## Tips from exercies

1. Route 53 allows domain registration
