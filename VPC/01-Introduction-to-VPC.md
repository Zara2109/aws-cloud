# Introduction to VPC

## What is a VPC?

Amazon Virtual Private Cloud (VPC) is a service that allows you to create a logically isolated virtual network within AWS.

You can launch AWS resources such as EC2 instances, databases, and load balancers inside your VPC while controlling networking and security settings.

Think of a VPC as your own private data center inside AWS.

---

## Why Do We Need a VPC?

Without a VPC, all AWS resources would exist in a shared network environment.

A VPC provides:

* Network Isolation
* Security Control
* Custom IP Addressing
* Traffic Management
* Internet Connectivity Control

---

## Real-World Analogy

Imagine AWS as a large apartment building.

```text id="vpc1"
AWS Cloud = Apartment Building

VPC = Your Private Apartment

EC2 Instances = Rooms Inside Apartment
```

Although many customers use AWS, your VPC remains isolated from others.

---

## Key Features of VPC

### Network Isolation

Resources inside your VPC are separated from other AWS customers.

---

### Custom IP Address Range

You can define your own CIDR block.

Example:

```text id="vpc2"
10.0.0.0/16
192.168.0.0/16
172.31.0.0/16
```

---

### Security Controls

Control traffic using:

* Security Groups
* Network ACLs

---

### Internet Connectivity

Resources can be connected to the internet using:

* Internet Gateway
* NAT Gateway

---

## Default VPC

AWS automatically creates a Default VPC in each region.

Characteristics:

```text id="vpc3"
✓ Ready to use
✓ Public subnets available
✓ Internet access configured
✓ Suitable for beginners
```

---

## Custom VPC

A Custom VPC is manually created by the user.

Characteristics:

```text id="vpc4"
✓ Full control
✓ Custom CIDR blocks
✓ Custom subnets
✓ Enhanced security
✓ Production-ready architecture
```

---

## Default VPC vs Custom VPC

| Feature                 | Default VPC | Custom VPC |
| ----------------------- | ----------- | ---------- |
| Created Automatically   | Yes         | No         |
| Ready to Use            | Yes         | No         |
| Full Network Control    | Limited     | Yes        |
| Suitable for Production | Limited     | Yes        |
| Custom CIDR             | No          | Yes        |

---

## Components of a VPC

A VPC consists of multiple networking components:

```text id="vpc5"
VPC
│
├── Subnets
├── Route Tables
├── Internet Gateway
├── NAT Gateway
├── Security Groups
├── Network ACLs
├── VPC Peering
└── VPC Endpoints
```

---

## VPC Architecture Example

```text id="vpc6"
Internet
    │
Internet Gateway
    │
┌────────────VPC────────────┐
│                           │
│  Public Subnet            │
│      │                    │
│     EC2                   │
│                           │
│  Private Subnet           │
│      │                    │
│     Database              │
│                           │
└───────────────────────────┘
```

---

## Benefits of VPC

### Improved Security

Resources remain isolated and protected.

### Better Traffic Control

Manage inbound and outbound traffic efficiently.

### Flexible Networking

Create custom network architectures.

### Scalability

Easily expand infrastructure as requirements grow.

---

## Real-World Example

A company hosts:

```text id="vpc7"
Web Server
Application Server
Database Server
```

Architecture:

```text id="vpc8"
Public Subnet
   ↓
Web Server

Private Subnet
   ↓
Application Server

Private Subnet
   ↓
Database Server
```

This design improves security by preventing direct internet access to sensitive systems.

---

## Summary

* VPC stands for Virtual Private Cloud.
* A VPC is a logically isolated network within AWS.
* It provides security, networking control, and resource isolation.
* AWS offers Default VPCs and Custom VPCs.
* VPC components include Subnets, Route Tables, Gateways, Security Groups, and NACLs.
* VPC is the foundation of AWS networking.
