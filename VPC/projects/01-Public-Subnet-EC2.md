# Project 1: Launch EC2 in a Public Subnet

## Objective

Deploy an Amazon EC2 instance in a Public Subnet and host a simple web page accessible from the internet.

---

## Architecture

Internet
    │
Internet Gateway
    │
Route Table
    │
Public Subnet
    │
EC2 Instance

---

## AWS Services Used

- VPC
- Subnet
- Internet Gateway
- Route Table
- Security Group
- EC2
- Apache Web Server

---

## Steps Performed

### 1. Created a VPC

CIDR Block:

10.0.0.0/16

---

### 2. Created a Public Subnet

CIDR:

10.0.1.0/24

---

### 3. Created and Attached an Internet Gateway

Attached IGW to the VPC.

---

### 4. Created Route Table

Added route:

0.0.0.0/0 → Internet Gateway

Associated the route table with the Public Subnet.

---

### 5. Enabled Auto Public IP

Enabled auto-assign public IPv4 address.

---

### 6. Launched EC2 Instance

Configuration:

- Amazon Linux 2023
- t2.micro
- Public Subnet
- Public IP Enabled

---

### 7. Installed Apache

```bash
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

### 8. Hosted a Web Page

Created a custom HTML page and accessed it using the instance's public IP.

---

## Screenshots


### EC2 Running
![alt text](<instance public subnet.png>)

### Website Output
![alt text](<public webserver.png>)

---

## Outcome

Successfully deployed a public-facing EC2 instance and hosted a website accessible through the internet.