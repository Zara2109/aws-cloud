# Target Groups

## Introduction

A Target Group is a collection of resources that receive traffic from a Load Balancer.

When a user sends a request to an Application Load Balancer (ALB), the Load Balancer forwards the request to a Target Group, which then distributes the traffic to healthy targets.

Target Groups are a core component of Elastic Load Balancing (ELB).

---

## How Target Groups Work

```text id="v2n8sq"
Users
   ↓
Application Load Balancer
   ↓
Target Group
   ↓
EC2 Instance 1
EC2 Instance 2
EC2 Instance 3
```

The Load Balancer does not directly send traffic to EC2 instances.

Instead:

1. User sends request
2. Load Balancer receives request
3. Target Group selects a healthy target
4. Request is forwarded to that target

---

## Types of Targets

AWS supports multiple target types.

### 1. EC2 Instances

Most commonly used.

Example:

```text id="4f8xmu"
Web Server 1
Web Server 2
Web Server 3
```

---

### 2. IP Addresses

Traffic can be routed directly to specific IP addresses.

Use Cases:

* On-premises servers
* Hybrid cloud environments

---

### 3. Lambda Functions

Target Groups can invoke Lambda functions directly.

Use Cases:

* Serverless applications
* Event-driven workloads

---

## Health Checks

A Target Group continuously checks whether a target is healthy.

Example:

```text id="7r3nqk"
HTTP:80
Path: /
```

If a target fails the health check:

```text id="q1y7pl"
Healthy → Receives Traffic

Unhealthy → No Traffic
```

This ensures users only reach functioning applications.

---

## Health Check Components

### Protocol

Examples:

```text id="3k5vde"
HTTP
HTTPS
TCP
```

---

### Port

Example:

```text id="v7a8lt"
80
443
8080
```

---

### Path

Example:

```text id="m2q9wh"
/health
/status
/
```

---

## Target Group Attributes

Target Groups store information such as:

* Registered Targets
* Health Check Configuration
* Protocol
* Port Number
* Load Balancing Settings

---

## Target Groups with Auto Scaling

Target Groups integrate directly with Auto Scaling Groups.

```text id="z5c8xr"
Auto Scaling Group
          ↓
Launches EC2 Instances
          ↓
Registers Instances
          ↓
Target Group
```

New instances are automatically added to the Target Group.

Terminated instances are automatically removed.

---

## Benefits of Target Groups

* Improved availability
* Automatic health monitoring
* Better traffic distribution
* Integration with Auto Scaling
* Simplified application scaling

---

## Real-World Example

A company hosts an e-commerce website on three EC2 instances.

```text id="g4x2mb"
EC2-1
EC2-2
EC2-3
```

An Application Load Balancer receives customer requests.

The Load Balancer forwards requests to a Target Group, which sends traffic only to healthy EC2 instances.

If one server fails, traffic is automatically redirected to the remaining healthy servers.

---

## Summary

* A Target Group is a collection of resources that receive traffic from a Load Balancer.
* Target Groups support EC2 instances, IP addresses, and Lambda functions.
* Health Checks ensure traffic is sent only to healthy targets.
* Target Groups work closely with Application Load Balancers and Auto Scaling Groups.
* They improve application availability, scalability, and reliability.
