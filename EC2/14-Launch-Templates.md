# Launch Templates

## Introduction

A Launch Template is a feature in Amazon EC2 that allows you to save the configuration required to launch an EC2 instance.

Instead of manually selecting settings every time, you can create a template and reuse it whenever you need to launch new instances.

Launch Templates are commonly used with:

* Auto Scaling Groups (ASG)
* EC2 Fleet
* Spot Instances
* Automated Deployments

---

## Why Use Launch Templates?

Without a Launch Template, every new EC2 instance must be configured manually.

A Launch Template helps by:

* Reducing manual work
* Maintaining consistency
* Supporting automation
* Simplifying large-scale deployments

---

## Components of a Launch Template

A Launch Template can store the following settings:

### 1. Amazon Machine Image (AMI)

Defines the operating system and software configuration.

Examples:

* Amazon Linux 2023
* Ubuntu 24.04
* Red Hat Enterprise Linux

---

### 2. Instance Type

Defines the hardware resources.

Examples:

```text
t2.micro
t3.micro
t3.small
```

---

### 3. Key Pair

Used for secure SSH access to the EC2 instance.

Example:

```text
zahrah-key.pem
```

---

### 4. Security Groups

Defines inbound and outbound traffic rules.

Example:

```text
SSH (22)
HTTP (80)
HTTPS (443)
```

---

### 5. Storage Configuration

Defines EBS volume settings.

Example:

```text
Volume Type: gp3
Size: 20 GB
```

---

### 6. User Data

Shell scripts that run automatically when the instance launches.

Example:

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
```

---

## How Launch Templates Work

```text
Launch Template
       ↓
Auto Scaling Group
       ↓
EC2 Instance 1
EC2 Instance 2
EC2 Instance 3
```

Every instance launched from the template uses the same configuration.

---

## Creating a Launch Template

1. Open AWS Management Console
2. Navigate to EC2
3. Select Launch Templates
4. Click Create Launch Template
5. Enter a template name
6. Configure:

   * AMI
   * Instance Type
   * Key Pair
   * Security Group
   * Storage
   * User Data
7. Save the template

---

## Launch Template vs Manual Launch

| Feature                  | Manual Launch | Launch Template |
| ------------------------ | ------------- | --------------- |
| Reusable                 | No            | Yes             |
| Consistent Configuration | No            | Yes             |
| Automation Support       | Limited       | Excellent       |
| Auto Scaling Integration | No            | Yes             |

---

## Benefits of Launch Templates

* Faster EC2 deployment
* Standardized configurations
* Easy integration with Auto Scaling
* Reduced human error
* Improved scalability

---

## Real-World Example

A company runs a web application behind an Application Load Balancer.

During high traffic periods, Auto Scaling launches additional EC2 instances.

Instead of manually configuring each instance, Auto Scaling uses a Launch Template to automatically create new servers with the required settings.

---

## Summary

* Launch Templates store EC2 configuration settings.
* They help automate and standardize deployments.
* Launch Templates are commonly used with Auto Scaling Groups.
* They include AMI, Instance Type, Security Groups, Storage, Key Pairs, and User Data.
* Using Launch Templates reduces manual effort and improves scalability.
