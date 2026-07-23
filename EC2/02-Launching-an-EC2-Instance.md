# 🚀 Launching an Amazon EC2 Instance

## Objective

Learn how to launch and configure an Amazon EC2 instance using the AWS Management Console.

---

# Prerequisites

- AWS Account
- AWS Management Console Access
- Basic understanding of EC2

---

# Steps to Launch an EC2 Instance

## Step 1: Sign in to AWS

Log in to the AWS Management Console and search for **EC2**.

---

## Step 2: Launch Instance

Click **Launch Instance**.

---

## Step 3: Enter Instance Name

Example:

```
WebServer
```

---

## Step 4: Choose an Amazon Machine Image (AMI)

Common options:

- Ubuntu Server
- Amazon Linux
- Red Hat Enterprise Linux
- Debian
- Windows Server

The AMI determines the operating system installed on the instance.

---

## Step 5: Choose an Instance Type

Example:

```
t2.micro
```

The instance type defines the CPU, memory, and networking capacity.

---

## Step 6: Create or Select a Key Pair

A Key Pair is required to securely connect to the EC2 instance using SSH.

Example:

```
zahrah-key.pem
```

---

## Step 7: Configure Security Group

Allow the required inbound traffic.

| Type | Port | Source |
|------|------|--------|
| SSH | 22 | My IP |
| HTTP | 80 | Anywhere (0.0.0.0/0) |

---

## Step 8: Configure Storage

Use the default EBS volume or customize storage as required.

---

## Step 9: Launch the Instance

Click **Launch Instance**.

The instance state changes:

Pending → Running

---

# Instance States

- Pending
- Running
- Stopping
- Stopped
- Rebooting
- Terminated

---

# Important Components

- AMI
- Instance Type
- Key Pair
- Security Group
- EBS Volume
- Public IP
- Private IP

---

# Common Mistakes

- Forgetting to create a Key Pair
- SSH Port (22) blocked
- HTTP Port (80) blocked
- Using the wrong username (ubuntu vs ec2-user)
- Using the Private IP instead of the Public IP

---

# Key Takeaways

- Every EC2 instance requires an AMI.
- A Security Group acts as a virtual firewall.
- A Key Pair is required for SSH access.
- A Public IP is required for internet access.

---

# Interview Questions

1. What is an AMI?

2. What is an Instance Type?

3. What is a Key Pair?

4. Why is a Security Group required?

5. Difference between Stop and Terminate?

6. Can an EC2 instance run without an AMI?

7. Which instance type is included in the AWS Free Tier?
