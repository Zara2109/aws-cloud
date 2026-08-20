# Route Tables

## Introduction

A Route Table is a set of rules that determines where network traffic is directed within a VPC.

Every subnet in a VPC must be associated with a route table.

Route tables help AWS decide how traffic moves between:

* Subnets
* Internet
* NAT Gateway
* VPC Peering Connections
* VPC Endpoints

---

## Why Are Route Tables Important?

Route tables control traffic flow inside and outside a VPC.

They help:

* Connect resources to the internet
* Enable communication between networks
* Control network traffic
* Build secure architectures

---

## How Route Tables Work

```text id="route1"
EC2 Instance
      ↓
Route Table
      ↓
Destination
```

When traffic leaves a resource, AWS checks the route table and forwards the traffic according to the matching rule.

---

## Components of a Route Table

Every route contains:

### Destination

The IP range where traffic is going.

Example:

```text id="route2"
0.0.0.0/0
10.0.0.0/16
```

---

### Target

The destination resource where traffic should be sent.

Examples:

```text id="route3"
Internet Gateway
NAT Gateway
Local
VPC Peering Connection
```

---

## Default Route Table

When a VPC is created, AWS automatically creates a default route table.

Example:

```text id="route4"
Destination     Target

10.0.0.0/16     Local
```

The "Local" route allows communication between resources inside the same VPC.

---

## Local Route

Every route table contains a local route.

Example:

```text id="route5"
Destination: 10.0.0.0/16
Target: Local
```

Purpose:

* Enables communication between subnets inside the VPC.

---

## Public Route Table

A Public Route Table includes a route to the Internet Gateway.

Example:

```text id="route6"
Destination     Target

10.0.0.0/16     Local
0.0.0.0/0       Internet Gateway
```

Meaning:

```text id="route7"
Traffic to VPC → Local

Traffic to Internet → Internet Gateway
```

---

## Public Subnet Architecture

```text id="route8"
Internet
    │
Internet Gateway
    │
Route Table
    │
Public Subnet
    │
EC2 Instance
```

This allows internet access.

---

## Private Route Table

A Private Route Table does not have a direct route to the Internet Gateway.

Example:

```text id="route9"
Destination     Target

10.0.0.0/16     Local
```

Resources remain isolated from the internet.

---

## Private Subnet with NAT Gateway

```text id="route10"
Destination     Target

10.0.0.0/16     Local
0.0.0.0/0       NAT Gateway
```

This allows outbound internet access without exposing resources publicly.

---

## Route Table Associations

A route table must be associated with one or more subnets.

Example:

```text id="route11"
Public Subnet
      ↓
Public Route Table

Private Subnet
      ↓
Private Route Table
```

Different subnets can use different route tables.

---

## Public vs Private Route Table

| Feature                  | Public Route Table | Private Route Table |
| ------------------------ | ------------------ | ------------------- |
| Internet Gateway Route   | Yes                | No                  |
| Direct Internet Access   | Yes                | No                  |
| Suitable for Web Servers | Yes                | No                  |
| Suitable for Databases   | No                 | Yes                 |

---

## Real-World Example

A company hosts:

```text id="route12"
Web Server
Application Server
Database Server
```

Architecture:

```text id="route13"
Internet
    │
Internet Gateway
    │
Public Route Table
    │
Web Server

Private Route Table
    │
Application Server

Private Route Table
    │
Database Server
```

Benefits:

* Web server accessible from the internet
* Application and database servers protected
* Better security

---

## Best Practices

### Separate Public and Private Resources

Use different route tables for public and private subnets.

---

### Use NAT Gateway for Private Resources

Allow outbound internet access without exposing servers publicly.

---

### Keep Databases Private

Never place databases in publicly accessible subnets.

---

### Use Meaningful Names

Examples:

```text id="route14"
Public-RT
Private-RT
Database-RT
```

---

## Summary

* Route Tables control network traffic within a VPC.
* Every subnet must be associated with a route table.
* Routes consist of a destination and a target.
* Public route tables use an Internet Gateway.
* Private route tables typically use a NAT Gateway.
* Route tables are essential for building secure AWS network architectures.
