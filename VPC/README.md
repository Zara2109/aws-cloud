# AWS VPC Notes

This repository contains my learning notes and hands-on practice for Amazon Virtual Private Cloud (VPC).

Amazon VPC allows users to create isolated virtual networks within AWS, providing complete control over networking, security, routing, and connectivity for cloud resources.

---

## About VPC

Amazon Virtual Private Cloud (VPC) is a networking service that enables you to launch AWS resources in a logically isolated network.

With VPC, you can control:

* IP Address Ranges
* Subnets
* Route Tables
* Internet Access
* Security Rules
* Network Connectivity

VPC forms the foundation of AWS networking and is one of the most important services for cloud architects, system administrators, and DevOps engineers.

---

## Topics Covered

### Introduction to VPC

* What is VPC?
* Benefits of VPC
* VPC Components
* Default VPC vs Custom VPC

---

### Subnets

* Public Subnets
* Private Subnets
* CIDR Blocks
* Availability Zones

---

### Route Tables

* Route Table Basics
* Route Propagation
* Traffic Routing
* Public and Private Routing

---

### Internet Gateway (IGW)

* Internet Connectivity
* Public Resource Access
* Internet Gateway Architecture

---

### NAT Gateway

* Private Subnet Internet Access
* Outbound Connectivity
* High Availability Considerations

---

### Security Groups vs Network ACLs

* Stateful vs Stateless Security
* Inbound and Outbound Rules
* Traffic Filtering
* Security Best Practices

---

### VPC Peering

* VPC-to-VPC Communication
* Cross-VPC Connectivity
* Peering Limitations

---

### VPC Endpoints

* Private AWS Service Access
* Gateway Endpoints
* Interface Endpoints
* Improved Security

---

## Hands-On Activities

* Created Custom VPCs
* Configured Public and Private Subnets
* Attached Internet Gateways
* Configured Route Tables
* Created NAT Gateways
* Configured Security Groups
* Configured Network ACLs
* Established VPC Peering Connections
* Tested Network Connectivity

---

## Real-World Architecture

```text
Internet
    │
Internet Gateway
    │
┌───────────────VPC───────────────┐
│                                │
│   Public Subnet               │
│      │                        │
│     EC2                       │
│      │                        │
│   NAT Gateway                 │
│      │                        │
│   Private Subnet              │
│      │                        │
│     EC2                       │
│                                │
└────────────────────────────────┘
```

---

## Key Concepts Learned

### Networking

* CIDR Blocks
* IP Addressing
* Routing
* Internet Connectivity

### Security

* Security Groups
* Network ACLs
* Private Networking
* Access Control

### Connectivity

* Internet Gateway
* NAT Gateway
* VPC Peering
* VPC Endpoints

---

## Skills Practiced

* AWS Networking
* Cloud Security
* Route Configuration
* Network Troubleshooting
* VPC Architecture Design
* Infrastructure Planning

---

## Repository Structure

```text
VPC/
├── README.md
├── 01-Introduction-to-VPC.md
├── 02-Subnets.md
├── 03-Route-Tables.md
├── 04-Internet-Gateway.md
├── 05-NAT-Gateway.md
├── 06-Security-Groups-vs-NACL.md
├── 07-VPC-Peering.md
├── 08-VPC-Endpoints.md
├── screenshots/
└── projects/
```

---

## Learning Goals

* Understand AWS Networking Fundamentals
* Build Secure Cloud Networks
* Design Public and Private Architectures
* Implement Network Security Controls
* Prepare for AWS and Cloud Engineering Roles

---

## Author

### Zahrah Mukarram

**Aspiring AWS Cloud & DevOps Engineer**

Currently learning:

* Amazon Web Services (AWS)
* Linux Administration
* Networking
* Python
* Git & GitHub
* DevOps Fundamentals

---

*"A strong cloud foundation starts with understanding networking, security, and connectivity inside a VPC."*
