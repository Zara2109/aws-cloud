# AWS Load Balancer

## What is a Load Balancer?

A Load Balancer distributes incoming traffic across multiple servers (EC2 instances).

Instead of sending all requests to a single server, traffic is distributed to healthy servers, improving availability and performance.

## Benefits

- High Availability
- Fault Tolerance
- Scalability
- Better Performance

## Types of AWS Load Balancers

### 1. Application Load Balancer (ALB)

- Layer 7 (Application Layer)
- HTTP and HTTPS traffic
- Host-based routing
- Path-based routing

### 2. Network Load Balancer (NLB)

- Layer 4 (Transport Layer)
- TCP, UDP, TLS traffic
- Ultra-high performance
- Low latency

### 3. Gateway Load Balancer (GWLB)

- Used for security appliances
- Firewall integration
- Intrusion detection systems

## Components

### Listener

Checks incoming traffic on a specific port.

Examples:

- Port 80 (HTTP)
- Port 443 (HTTPS)

### Target Group

A collection of targets that receive traffic.

Examples:

- EC2 Instances
- IP Addresses
- Lambda Functions

### Health Checks

Load Balancer continuously checks target health.

Unhealthy instances stop receiving traffic.

## Architecture

Internet
↓
Load Balancer
↓
Target Group
↓
EC2 Instances

## Summary

AWS Load Balancers improve application availability, reliability, and scalability by distributing traffic across multiple resources.