# Internet Gateway (IGW)

## Introduction

An Internet Gateway (IGW) is a VPC component that enables communication between resources inside a VPC and the internet.

Without an Internet Gateway, resources in a VPC cannot directly send or receive internet traffic.

---

## Why Do We Need an Internet Gateway?

An Internet Gateway allows:

* Inbound internet traffic
* Outbound internet traffic
* Public access to AWS resources

Common examples:

```text id="igw1"
Web Servers
Load Balancers
Public Applications
```

---

## How Internet Gateway Works

```text id="igw2"
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

The Internet Gateway acts as a bridge between the VPC and the internet.

---

## Key Features of Internet Gateway

### Highly Available

Internet Gateways are highly available and managed by AWS.

---

### Horizontally Scalable

AWS automatically scales the Internet Gateway according to network traffic requirements.

---

### Free to Use

There is no additional charge for creating an Internet Gateway.

---

## Creating an Internet Gateway

1. Open AWS Management Console
2. Navigate to VPC
3. Select Internet Gateways
4. Click Create Internet Gateway
5. Provide a Name
6. Create Internet Gateway
7. Attach it to a VPC

---

## Attaching an Internet Gateway

```text id="igw3"
VPC
 │
 └── Internet Gateway
```

A VPC can have only one attached Internet Gateway at a time.

---

## Route Table Configuration

Creating an Internet Gateway alone is not enough.

You must also add a route:

```text id="igw4"
Destination      Target

0.0.0.0/0        Internet Gateway
```

This route directs internet-bound traffic to the Internet Gateway.

---

## Public Subnet Requirements

For a subnet to be considered public:

### Requirement 1

The subnet must be associated with a route table containing:

```text id="igw5"
0.0.0.0/0 → Internet Gateway
```

### Requirement 2

The EC2 instance must have:

```text id="igw6"
Public IP Address
```

---

## Internet Gateway Architecture

```text id="igw7"
Internet
    │
Internet Gateway
    │
Public Route Table
    │
Public Subnet
    │
EC2 Instance
```

Users can access the EC2 instance through its public IP address.

---

## Without Internet Gateway

```text id="igw8"
Internet
    ✖
No Connection

VPC
 │
 EC2
```

Resources inside the VPC cannot communicate with the internet.

---

## Internet Gateway vs NAT Gateway

| Feature                   | Internet Gateway | NAT Gateway   |
| ------------------------- | ---------------- | ------------- |
| Internet Access           | Yes              | Outbound Only |
| Inbound Traffic           | Yes              | No            |
| Public Subnet Required    | Yes              | Yes           |
| Used By Public Resources  | Yes              | No            |
| Used By Private Resources | No               | Yes           |

---

## Real-World Example

A company hosts a public website.

Architecture:

```text id="igw9"
Internet
    │
Internet Gateway
    │
Load Balancer
    │
Web Server
```

The Internet Gateway allows users worldwide to access the website.

---

## Best Practices

### Use Internet Gateway Only for Public Resources

Examples:

```text id="igw10"
Web Servers
Load Balancers
Bastion Hosts
```

---

### Keep Databases Private

Databases should remain in private subnets without direct internet access.

---

### Configure Security Groups

Even with an Internet Gateway, Security Groups should restrict unnecessary traffic.

---

### Verify Route Tables

Ensure public subnets have the correct route:

```text id="igw11"
0.0.0.0/0 → Internet Gateway
```

---

## Summary

* An Internet Gateway (IGW) connects a VPC to the internet.
* It enables inbound and outbound internet communication.
* Public subnets require a route to the Internet Gateway.
* EC2 instances need a public IP address to be accessible from the internet.
* Internet Gateways are highly available, scalable, and managed by AWS.
* They are essential for hosting public-facing applications in AWS.
