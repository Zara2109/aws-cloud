# Project 3: VPC Peering Connection

## Objective

Create a VPC Peering Connection between two VPCs and enable communication between EC2 instances using private IP addresses.

---

## Architecture

```text
VPC-A (10.0.0.0/16)
│
├── Public Subnet-A (10.0.1.0/24)
│     └── Peer-A EC2
│
└──────────────┐
               │
      VPC Peering Connection
               │
┌──────────────┘
│
VPC-B (192.168.0.0/16)
│
├── Public Subnet-B (192.168.1.0/24)
│     └── Peer-B EC2
│
```

---

## AWS Services Used

- Amazon VPC
- VPC Peering Connection
- Amazon EC2
- Route Tables
- Security Groups
- Internet Gateway

---

## Prerequisites

Before creating the peering connection:

- Created two separate VPCs
- Created subnets in each VPC
- Attached Internet Gateways
- Configured route tables
- Launched EC2 instances in both VPCs

---

## VPC Configuration

### VPC-A

| Resource | Value |
|-----------|---------|
| Name | VPC-A |
| CIDR Block | 10.0.0.0/16 |
| Public Subnet | 10.0.1.0/24 |
| EC2 Instance | Peer-A |

---

### VPC-B

| Resource | Value |
|-----------|---------|
| Name | VPC-B |
| CIDR Block | 192.168.0.0/16 |
| Public Subnet | 192.168.1.0/24 |
| EC2 Instance | Peer-B |

---

## Steps Performed

### Step 1: Created VPC-A

Created a custom VPC with CIDR:

```text
10.0.0.0/16
```

Created a public subnet:

```text
10.0.1.0/24
```

Launched EC2 instance:

```text
Peer-A
```

---

### Step 2: Created VPC-B

Created another VPC with CIDR:

```text
192.168.0.0/16
```

Created a public subnet:

```text
192.168.1.0/24
```

Launched EC2 instance:

```text
Peer-B
```

---

### Step 3: Created VPC Peering Connection

Navigated to:

```text
VPC → Peering Connections
```

Created a peering request:

```text
Requester VPC : VPC-A
Accepter VPC  : VPC-B
```

Accepted the request.

Status:

```text
Active
```

---

### Step 4: Updated Route Table of VPC-A

Added route:

```text
Destination : 192.168.0.0/16
Target      : VPC Peering Connection
```

---

### Step 5: Updated Route Table of VPC-B

Added route:

```text
Destination : 10.0.0.0/16
Target      : VPC Peering Connection
```

---

### Step 6: Associated Subnets with Route Tables

Associated:

```text
Public Subnet-A
```

with:

```text
Route Table A
```

Associated:

```text
Public Subnet-B
```

with:

```text
Route Table B
```

---

### Step 7: Configured Security Groups

Allowed:

```text
SSH (22)
```

for administration.

Allowed:

```text
ICMP
```

between VPC CIDR ranges for connectivity testing.

Example:

```text
VPC-A SG → ICMP from 192.168.0.0/16

VPC-B SG → ICMP from 10.0.0.0/16
```

---

### Step 8: Verified Connectivity

Connected to Peer-A.

Pinged Peer-B using private IP:

```bash
ping <Peer-B-Private-IP>
```

Successful replies confirmed that traffic was flowing through the peering connection.

---

## Challenges Faced

### Route Table Association Issue

Initially, SSH access to the instance failed.

Root Cause:

```text
Subnet was not associated with the correct route table.
```

Resolution:

```text
Associated the subnet with the custom route table containing the Internet Gateway route.
```

After association, SSH access worked successfully.

---

## Screenshots

### VPC-A Configuration

![alt text](<Screenshot 2026-08-21 013745.png>)

---

### VPC-B Configuration
![alt text](<Screenshot 2026-08-21 013813.png>)

---

### Peering Connection Status

![alt text](<Screenshot 2026-08-21 013901.png>)

---

### Route Table A

![alt text](<Screenshot 2026-08-21 013933.png>)

---

### Route Table B

![alt text](<Screenshot 2026-08-21 014016.png>)


---

### Successful Ping Test

![alt text](<Screenshot 2026-08-21 014047.png>)

---

## Key Learnings

- VPCs are isolated by default.
- VPC Peering enables private communication between VPCs.
- Route tables must be updated on both sides.
- Security Groups control traffic flow.
- Subnet association with route tables is critical.
- Private IP communication is more secure than public communication.

---

## Outcome

Successfully established a VPC Peering Connection between two VPCs and enabled communication between EC2 instances using private IP addresses.

This project provided hands-on experience with:

- VPC Networking
- Route Tables
- Security Groups
- EC2 Connectivity
- Troubleshooting AWS Networking Issues
- VPC Peering Architecture