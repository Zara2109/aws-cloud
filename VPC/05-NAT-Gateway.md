# NAT Gateway

## Introduction

A NAT Gateway (Network Address Translation Gateway) allows resources in a private subnet to access the internet while preventing direct inbound internet access.

It is commonly used when private resources need:

* Software updates
* Security patches
* Access to AWS services
* External API communication

without being exposed to the internet.

---

## Why Do We Need a NAT Gateway?

Resources in a private subnet cannot communicate directly with the internet.

Without a NAT Gateway:

```text id="nat1"
Private Subnet
      │
      ✖
No Internet Access
```

With a NAT Gateway:

```text id="nat2"
Private Subnet
      │
NAT Gateway
      │
Internet Gateway
      │
Internet
```

Private resources can access the internet safely.

---

## How NAT Gateway Works

A NAT Gateway receives requests from resources in a private subnet and forwards them to the internet.

When responses return:

```text id="nat3"
Private EC2
     │
NAT Gateway
     │
Internet
```

The NAT Gateway forwards the response back to the private resource.

---

## Key Features of NAT Gateway

### Outbound Internet Access

Allows private resources to access the internet.

---

### No Inbound Internet Access

External users cannot directly connect to resources in a private subnet.

---

### Managed Service

AWS manages:

* Availability
* Scaling
* Maintenance

---

### High Availability

NAT Gateway is highly available within its Availability Zone.

---

## NAT Gateway Architecture

```text id="nat4"
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
EC2 Instance
```

The NAT Gateway must always be placed in a Public Subnet.

---

## Creating a NAT Gateway

### Step 1

Create a Public Subnet.

---

### Step 2

Attach an Internet Gateway to the VPC.

---

### Step 3

Allocate an Elastic IP Address.

---

### Step 4

Create a NAT Gateway inside the Public Subnet.

---

### Step 5

Update the Private Route Table.

Add:

```text id="nat5"
Destination      Target

0.0.0.0/0        NAT Gateway
```

---

## Private Route Table Example

```text id="nat6"
Destination      Target

10.0.0.0/16      Local
0.0.0.0/0        NAT Gateway
```

Meaning:

* Internal VPC traffic stays local
* Internet traffic goes through NAT Gateway

---

## Traffic Flow

```text id="nat7"
Private EC2
      │
Private Route Table
      │
NAT Gateway
      │
Internet Gateway
      │
Internet
```

Return traffic follows the same path.

---

## NAT Gateway vs Internet Gateway

| Feature                   | NAT Gateway   | Internet Gateway   |
| ------------------------- | ------------- | ------------------ |
| Internet Access           | Outbound Only | Inbound & Outbound |
| Public Subnet Required    | Yes           | Yes                |
| Used by Private Resources | Yes           | No                 |
| Used by Public Resources  | No            | Yes                |
| Direct Internet Access    | No            | Yes                |

---

## Real-World Example

A company hosts:

```text id="nat8"
Web Server
Application Server
Database Server
```

Architecture:

```text id="nat9"
Internet
    │
Internet Gateway
    │
Public Subnet
    │
Web Server
    │
NAT Gateway
    │
Private Subnet
    │
Application Server
    │
Database Server
```

Benefits:

* Web server accessible publicly
* Application and database servers remain private
* Private resources can download updates securely

---

## Best Practices

### Place NAT Gateway in a Public Subnet

A NAT Gateway must have internet connectivity.

---

### Use Elastic IP

Every NAT Gateway requires an Elastic IP Address.

---

### Keep Databases Private

Databases should never require direct internet access.

---

### Use Multiple NAT Gateways for High Availability

For production environments:

```text id="nat10"
AZ-A → NAT Gateway-A

AZ-B → NAT Gateway-B
```

This improves fault tolerance.

---

## Common Interview Question

### Can a NAT Gateway Receive Inbound Internet Traffic?

Answer:

```text id="nat11"
No
```

A NAT Gateway only allows outbound connections initiated by resources in private subnets.

External users cannot directly access private resources through a NAT Gateway.

---

## Summary

* NAT Gateway provides internet access to private subnets.
* It allows outbound traffic but blocks inbound traffic.
* NAT Gateway must be deployed in a Public Subnet.
* An Elastic IP is required for NAT Gateway creation.
* Private route tables use NAT Gateway for internet-bound traffic.
* NAT Gateway improves security by keeping private resources hidden from the internet.
