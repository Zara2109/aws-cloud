# Security Groups vs Network ACLs (NACLs)

## Introduction

Security Groups and Network Access Control Lists (NACLs) are AWS security mechanisms used to control network traffic within a VPC.

Both help secure AWS resources, but they operate at different levels and behave differently.

---

## What is a Security Group?

A Security Group acts as a virtual firewall for an EC2 instance.

It controls:

* Inbound Traffic
* Outbound Traffic

Security Groups are attached directly to AWS resources such as:

```text id="sg1"
EC2 Instances
Load Balancers
RDS Databases
```

---

## Security Group Architecture

```text id="sg2"
Internet
    │
Security Group
    │
EC2 Instance
```

All traffic reaching the instance is checked against Security Group rules.

---

## Example Security Group Rules

### Inbound Rules

```text id="sg3"
HTTP  → Port 80
HTTPS → Port 443
SSH   → Port 22
```

---

### Outbound Rules

```text id="sg4"
Allow All Traffic
```

---

## What is a Network ACL (NACL)?

A Network ACL is a firewall that operates at the subnet level.

It controls traffic entering and leaving an entire subnet.

---

## NACL Architecture

```text id="nacl1"
Internet
    │
Network ACL
    │
Subnet
    │
EC2 Instance
```

Every resource inside the subnet is affected by the NACL.

---

## NACL Rules

NACLs support:

```text id="nacl2"
Allow Rules
Deny Rules
```

Example:

```text id="nacl3"
Allow HTTP
Allow HTTPS
Deny Specific IP Address
```

---

## Stateful vs Stateless

### Security Groups are Stateful

If inbound traffic is allowed:

```text id="sg5"
Client
   ↓
EC2 Instance
```

The response is automatically allowed.

No additional outbound rule is required.

---

### NACLs are Stateless

Both inbound and outbound rules must be configured.

Example:

```text id="nacl4"
Inbound Rule  → Allow HTTP

Outbound Rule → Allow Response Traffic
```

If outbound rules are missing, communication fails.

---

## Security Group vs NACL

| Feature              | Security Group               | Network ACL       |
| -------------------- | ---------------------------- | ----------------- |
| Applied To           | EC2 Instance                 | Subnet            |
| Stateful             | Yes                          | No                |
| Supports Allow Rules | Yes                          | Yes               |
| Supports Deny Rules  | No                           | Yes               |
| Operates At          | Instance Level               | Subnet Level      |
| Default Behavior     | Deny Inbound, Allow Outbound | Allow All Traffic |

---

## Traffic Flow Example

```text id="flow1"
Internet
    │
NACL
    │
Subnet
    │
Security Group
    │
EC2 Instance
```

Traffic must pass through:

1. NACL
2. Security Group

before reaching the instance.

---

## Default Security Group

AWS automatically creates a default Security Group.

Characteristics:

```text id="sg6"
Allow Traffic from Same Security Group
Allow All Outbound Traffic
Deny Other Inbound Traffic
```

---

## Default NACL

AWS automatically creates a default NACL.

Characteristics:

```text id="nacl5"
Allow All Inbound Traffic
Allow All Outbound Traffic
```

Until customized, it permits all traffic.

---

## Real-World Example

A company hosts a web application.

### Security Group

```text id="real1"
Allow HTTP (80)
Allow HTTPS (443)
Allow SSH (22)
```

---

### NACL

```text id="real2"
Allow Web Traffic
Block Suspicious IP Ranges
```

Together they provide layered security.

---

## Best Practices

### Use Security Groups as Primary Protection

Security Groups should be the first line of defense.

---

### Use NACLs for Additional Security

Use NACLs to:

* Block unwanted IP addresses
* Apply subnet-wide restrictions

---

### Follow Least Privilege

Only allow required traffic.

Example:

```text id="real3"
Allow:
80
443
22

Block Everything Else
```

---

### Regularly Review Rules

Remove unused rules to reduce security risks.

---

## Common Interview Questions

### Can a Security Group Deny Traffic?

Answer:

```text id="ans1"
No
```

Security Groups only support Allow rules.

---

### Can a NACL Deny Traffic?

Answer:

```text id="ans2"
Yes
```

NACLs support both Allow and Deny rules.

---

### Which is Stateful?

Answer:

```text id="ans3"
Security Group
```

---

### Which is Stateless?

Answer:

```text id="ans4"
Network ACL
```

---

## Quick Memory Trick

```text id="memory1"
Security Group
=
Instance Level
=
Stateful

NACL
=
Subnet Level
=
Stateless
```

---

## Summary

* Security Groups operate at the instance level.
* NACLs operate at the subnet level.
* Security Groups are stateful.
* NACLs are stateless.
* Security Groups support only Allow rules.
* NACLs support both Allow and Deny rules.
* Together they provide layered network security in AWS.
