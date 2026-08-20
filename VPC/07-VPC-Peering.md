# VPC Peering

## Introduction

VPC Peering is a networking connection between two VPCs that enables them to communicate privately using their private IP addresses.

The communication does not pass through:

* Internet Gateway
* NAT Gateway
* VPN Connection

This provides secure and efficient communication between VPCs.

---

## Why Use VPC Peering?

Organizations often create multiple VPCs for different applications, environments, or departments.

Examples:

```text id="peer1"
Production VPC

Development VPC

Testing VPC
```

VPC Peering allows these VPCs to communicate securely.

---

## How VPC Peering Works

```text id="peer2"
VPC-A
10.0.0.0/16
     │
     │ Peering Connection
     │
VPC-B
192.168.0.0/16
```

Resources in both VPCs can communicate using private IP addresses.

---

## Benefits of VPC Peering

### Private Communication

Traffic remains within the AWS network.

---

### Improved Security

No internet exposure.

---

### Low Latency

Traffic travels through AWS's private infrastructure.

---

### Easy Connectivity

Simple way to connect multiple VPCs.

---

## Types of VPC Peering

### Same Region Peering

Both VPCs are located in the same AWS Region.

Example:

```text id="peer3"
Mumbai VPC
      ↔
Mumbai VPC
```

---

### Cross-Region Peering

VPCs are located in different AWS Regions.

Example:

```text id="peer4"
Mumbai VPC
      ↔
Singapore VPC
```

---

## Creating a VPC Peering Connection

### Step 1

Create two VPCs.

Example:

```text id="peer5"
VPC-A
10.0.0.0/16

VPC-B
192.168.0.0/16
```

---

### Step 2

Create a Peering Connection.

```text id="peer6"
Requester VPC
       ↓
Accepter VPC
```

---

### Step 3

Accept the Peering Request.

---

### Step 4

Update Route Tables.

Example:

```text id="peer7"
VPC-A Route Table

Destination     Target

192.168.0.0/16  Peering Connection
```

---

```text id="peer8"
VPC-B Route Table

Destination     Target

10.0.0.0/16     Peering Connection
```

---

### Step 5

Update Security Groups if required.

Allow traffic from the peer VPC CIDR block.

---

## VPC Peering Architecture

```text id="peer9"
┌─────────────┐
│   VPC-A     │
│10.0.0.0/16  │
└──────┬──────┘
       │
       │ Peering Connection
       │
┌──────┴──────┐
│   VPC-B     │
│192.168.0.0/16
└─────────────┘
```

---

## Important Requirements

### Non-Overlapping CIDR Blocks

Peered VPCs must not have overlapping IP ranges.

Valid:

```text id="peer10"
VPC-A → 10.0.0.0/16

VPC-B → 192.168.0.0/16
```

Invalid:

```text id="peer11"
VPC-A → 10.0.0.0/16

VPC-B → 10.0.0.0/16
```

---

## VPC Peering Limitations

### No Transitive Peering

Example:

```text id="peer12"
VPC-A ↔ VPC-B

VPC-B ↔ VPC-C
```

Does NOT mean:

```text id="peer13"
VPC-A ↔ VPC-C
```

A separate peering connection is required.

---

### CIDR Overlap Not Allowed

Overlapping IP ranges prevent peering.

---

## Real-World Example

A company separates environments:

```text id="peer14"
Production VPC

Development VPC
```

Developers need secure access to specific production services.

Using VPC Peering:

```text id="peer15"
Development VPC
        ↔
Production VPC
```

Resources communicate privately without internet exposure.

---

## Best Practices

### Use Non-Overlapping CIDR Blocks

Plan IP ranges carefully before creating VPCs.

---

### Update Route Tables Properly

Both VPCs require routes pointing to the peering connection.

---

### Restrict Security Group Access

Allow only required traffic between VPCs.

---

### Monitor Connectivity

Use VPC Flow Logs and CloudWatch for troubleshooting.

---

## Common Interview Questions

### Does VPC Peering Use the Internet?

Answer:

```text id="peer16"
No
```

Traffic remains on AWS's private network.

---

### Can Peered VPCs Have the Same CIDR Block?

Answer:

```text id="peer17"
No
```

CIDR ranges must not overlap.

---

### Is VPC Peering Transitive?

Answer:

```text id="peer18"
No
```

Each VPC requires a direct peering connection.

---

## Summary

* VPC Peering connects two VPCs privately.
* Communication uses private IP addresses.
* Internet Gateway and NAT Gateway are not required.
* Route tables must be updated on both sides.
* Overlapping CIDR blocks are not allowed.
* VPC Peering is not transitive.
* It provides secure, low-latency communication between VPCs.
