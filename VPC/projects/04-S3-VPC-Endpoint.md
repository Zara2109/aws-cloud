# AWS VPC Endpoint Project – Private S3 Access from EC2

## Project Overview

This project demonstrates how to securely access Amazon S3 from a private EC2 instance without using an Internet Gateway, NAT Gateway, or public internet access.

Using a VPC Gateway Endpoint for S3, the private EC2 instance communicates directly with S3 through the AWS network.

---

## Architecture

```text
VPC (10.0.0.0/16)
│
├── Public Subnet (10.0.1.0/24)
│   └── Bastion Host
│
├── Private Subnet (10.0.2.0/24)
│   └── Private EC2 Instance
│
├── Internet Gateway
│
└── S3 Gateway Endpoint
      │
      └── Amazon S3 Bucket
```

---

## Objectives

* Create a custom VPC.
* Deploy public and private subnets.
* Launch a Bastion Host in the public subnet.
* Launch a Private EC2 instance without a public IP.
* Create an Amazon S3 bucket.
* Configure a VPC Gateway Endpoint for S3.
* Access S3 from the private EC2 instance without internet access.

---

## Services Used

* Amazon VPC
* Amazon EC2
* Amazon S3
* IAM Roles
* VPC Gateway Endpoint

---

## Step 1: Create VPC

Created a VPC with the following configuration:

| Setting    | Value                |
| ---------- | -------------------- |
| Name       | VPC-Endpoint-Project |
| CIDR Block | 10.0.0.0/16          |

### Screenshot

![alt text](<Screenshot 2026-08-23 150634-1.png>)

---

## Step 2: Create Subnets

### Public Subnet

| Setting | Value         |
| ------- | ------------- |
| Name    | Public-Subnet |
| CIDR    | 10.0.1.0/24   |

### Private Subnet

| Setting | Value          |
| ------- | -------------- |
| Name    | Private-Subnet |
| CIDR    | 10.0.2.0/24    |

### Screenshots

![alt text](<Screenshot 2026-08-23 150854.png>)
![alt text](<Screenshot 2026-08-23 151005.png>)

---

## Step 3: Create Internet Gateway

Created and attached an Internet Gateway to the VPC.

### Screenshot

![alt text](<Screenshot 2026-08-23 151140.png>)

---

## Step 4: Configure Route Table

Created a Public Route Table and added:

| Destination | Target           |
| ----------- | ---------------- |
| 0.0.0.0/0   | Internet Gateway |

Associated the Public Subnet with the Route Table.

### Screenshot

![alt text](<Screenshot 2026-08-23 151559.png>)
---

## Step 5: Launch Bastion Host

### Configuration

| Setting       | Value             |
| ------------- | ----------------- |
| Name          | Bastion-Host      |
| AMI           | Amazon Linux 2023 |
| Instance Type | t2.micro          |
| Subnet        | Public-Subnet     |
| Public IP     | Enabled           |

### Screenshot

![alt text](<Screenshot 2026-08-23 151915.png>)

---

## Step 6: Launch Private EC2 Instance

### Configuration

| Setting       | Value             |
| ------------- | ----------------- |
| Name          | Private-EC2       |
| AMI           | Amazon Linux 2023 |
| Instance Type | t2.micro          |
| Subnet        | Private-Subnet    |
| Public IP     | Disabled          |


---

## Step 7: Create S3 Bucket

Created an S3 bucket and uploaded a sample file.

### Screenshot

![alt text](<Screenshot 2026-08-23 152141.png>)

---

## Step 8: Create IAM Role

Created an IAM Role for EC2 and attached:

```text
AmazonS3FullAccess
```

Attached the role to the Private EC2 instance.


---

## Step 9: Create S3 Gateway Endpoint

Created a Gateway Endpoint for Amazon S3.

### Configuration

| Setting       | Value                       |
| ------------- | --------------------------- |
| Service       | com.amazonaws.ap-south-1.s3 |
| Endpoint Type | Gateway                     |
| VPC           | VPC-Endpoint-Project        |

Associated the endpoint with the VPC Route Table.

### Screenshot

![alt text](<Screenshot 2026-08-21 022604.png>)
---

## Step 10: SSH into Private EC2

Connected to the Bastion Host and then SSH'd into the Private EC2 instance.

```bash
ssh -i zahrah-key.pem ec2-user@PRIVATE-IP
```

### Screenshot

![alt text](<Screenshot 2026-08-23 160732.png>)

---

## Step 11: Verify S3 Access

Verified access to Amazon S3 from the private EC2 instance.

```bash
aws s3 ls
```

Example:

```bash
2026-08-23  zahrah-vpc-endpoint-demo
```

---

## Step 12: Verify Endpoint Route

Confirmed that the route table contains a Prefix List route pointing to the VPC Endpoint.

Example:

```text
pl-xxxxxxxx → vpce-xxxxxxxx
```


---

## Key Learning Outcomes

* Understood VPC networking fundamentals.
* Implemented public and private subnet architecture.
* Configured Bastion Host access.
* Learned how Gateway Endpoints work.
* Enabled secure S3 access without internet connectivity.
* Attached IAM Roles to EC2 instances.
* Verified private communication between AWS services.

---

## Conclusion

This project demonstrates how to securely access Amazon S3 from a private EC2 instance using a VPC Gateway Endpoint. By removing internet dependency and routing traffic through AWS private networking, organizations can improve security, reduce exposure, and follow cloud networking best practices.
