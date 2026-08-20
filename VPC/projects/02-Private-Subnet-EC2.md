# Project 2: Launch EC2 in a Private Subnet

## Objective

Deploy an EC2 instance in a Private Subnet and provide internet access through a NAT Gateway while preventing direct public access.

---

## Architecture

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
Private EC2

---

## AWS Services Used

- VPC
- Public Subnet
- Private Subnet
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- EC2

---

## Steps Performed

### 1. Created a Private Subnet

CIDR:

10.0.2.0/24

---

### 2. Allocated Elastic IP

Used for NAT Gateway creation.

---

### 3. Created NAT Gateway

Deployed NAT Gateway in the Public Subnet.

---

### 4. Created Private Route Table

Added route:

0.0.0.0/0 → NAT Gateway

Associated it with the Private Subnet.

---

### 5. Launched Private EC2

Configuration:

- Amazon Linux 2023
- t2.micro
- Private Subnet
- No Public IP

---

### 6. Configured Bastion Host

Created a Bastion Host in the Public Subnet for secure access to the private instance.

---

### 7. Verified Internet Connectivity

Logged into the Private EC2 through the Bastion Host.

Executed:

```bash
sudo yum update -y
```

The command completed successfully, confirming internet access through the NAT Gateway.

---

## Screenshots


### Private EC2 Instance
![alt text](<private subnet instance.png>)

### Bastion Host Access
![alt text](<connecting with bastion host.png>)


---

## Outcome

Successfully deployed a private EC2 instance with outbound internet access using a NAT Gateway while keeping the instance inaccessible from the public internet.