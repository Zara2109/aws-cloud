# Subnets

## Introduction

A Subnet is a smaller network created within a VPC.

Subnets help organize AWS resources and control network traffic by dividing a VPC into multiple sections.

Every subnet exists within a single Availability Zone (AZ).

---

## Why Use Subnets?

Subnets help:

* Organize resources
* Improve security
* Control traffic flow
* Separate public and private resources
* Build scalable architectures

---

## How Subnets Work

```text id="subnet1"
VPC (10.0.0.0/16)

├── Public Subnet
│      10.0.1.0/24
│
└── Private Subnet
       10.0.2.0/24
```

The VPC CIDR block is divided into smaller subnet ranges.

---

## Types of Subnets

### 1. Public Subnet

A Public Subnet allows resources to communicate directly with the internet.

Requirements:

* Route to Internet Gateway (IGW)
* Public IP Address

Example Resources:

```text id="subnet2"
Web Servers
Load Balancers
Bastion Hosts
```

---

### Public Subnet Architecture

```text id="subnet3"
Internet
    │
Internet Gateway
    │
Public Subnet
    │
EC2 Instance
```

Users can access the EC2 instance from the internet.

---

### 2. Private Subnet

A Private Subnet does not allow direct internet access.

Resources remain protected from public traffic.

Example Resources:

```text id="subnet4"
Databases
Application Servers
Internal Services
```

---

### Private Subnet Architecture

```text id="subnet5"
Internet
    │
Internet Gateway
    │
Public Subnet
    │
NAT Gateway
    │
Private Subnet
    │
Database Server
```

The database can access the internet for updates through the NAT Gateway but cannot be accessed directly from the internet.

---

## Availability Zones and Subnets

A subnet can exist in only one Availability Zone.

Example:

```text id="subnet6"
VPC

├── Public Subnet-A
│      ap-south-1a
│
├── Private Subnet-A
│      ap-south-1a
│
├── Public Subnet-B
│      ap-south-1b
│
└── Private Subnet-B
       ap-south-1b
```

Using multiple Availability Zones improves availability and fault tolerance.

---

## CIDR Blocks in Subnets

Each subnet receives a portion of the VPC CIDR range.

Example:

```text id="subnet7"
VPC:
10.0.0.0/16

Subnets:

10.0.1.0/24
10.0.2.0/24
10.0.3.0/24
10.0.4.0/24
```

---

## Public vs Private Subnet

| Feature                  | Public Subnet | Private Subnet |
| ------------------------ | ------------- | -------------- |
| Internet Access          | Yes           | No             |
| Internet Gateway Route   | Yes           | No             |
| Public IP Address        | Yes           | Usually No     |
| Suitable for Web Servers | Yes           | No             |
| Suitable for Databases   | No            | Yes            |

---

## Real-World Example

A company hosts a web application.

Architecture:

```text id="subnet8"
Internet
    │
Load Balancer
    │
Public Subnet
    │
Web Server
    │
Private Subnet
    │
Database
```

Benefits:

* Web servers are accessible from the internet.
* Databases remain protected in private subnets.
* Improved security and scalability.

---

## Best Practices

### Use Multiple Availability Zones

Create subnets across multiple AZs for high availability.

---

### Keep Databases Private

Place databases in private subnets.

---

### Separate Application Layers

Use separate subnets for:

```text id="subnet9"
Web Layer
Application Layer
Database Layer
```

---

### Use Meaningful Names

Examples:

```text id="subnet10"
Public-Subnet-A
Private-Subnet-A
Public-Subnet-B
Private-Subnet-B
```

---

## Summary

* A Subnet is a smaller network inside a VPC.
* Subnets divide a VPC into manageable sections.
* Public Subnets allow internet access.
* Private Subnets restrict direct internet access.
* Each subnet belongs to a single Availability Zone.
* Using multiple subnets improves security, availability, and network organization.
