# AWS IAM Notes

This repository contains my learning notes and hands-on practice for AWS Identity and Access Management (IAM).

IAM is the foundation of AWS security and is used to manage authentication, authorization, and access control for AWS resources.

## Topics Covered

* Introduction to IAM
* IAM Users
* IAM Groups
* IAM Policies
* IAM Roles
* Multi-Factor Authentication (MFA)
* IAM Best Practices

## Key Concepts Learned

### Identity Management

* Creating IAM Users
* Managing User Credentials
* User Authentication

### Access Management

* IAM Groups
* Permission Assignment
* Least Privilege Principle

### Authorization

* IAM Policies
* JSON Policy Structure
* Allow and Deny Permissions

### Temporary Access

* IAM Roles
* Role Assumption
* Cross-Service Access

### Security

* Multi-Factor Authentication (MFA)
* Strong Password Policies
* Access Key Management

## Hands-On Activities

* Created IAM Users
* Created IAM Groups
* Attached Managed Policies
* Created Custom Policies
* Assigned IAM Roles
* Configured MFA
* Tested Permission-Based Access

## Real-World Use Cases

### Developers

Access EC2, S3, and CloudWatch resources required for application development.

### Administrators

Manage AWS services and user permissions.

### AWS Services

Allow EC2, Lambda, and other AWS services to securely access resources using IAM Roles.

## Security Best Practices

* Enable MFA for privileged accounts
* Avoid using the Root User for daily tasks
* Follow the Principle of Least Privilege
* Rotate Access Keys regularly
* Use IAM Roles instead of sharing credentials
* Review permissions periodically

## Repository Structure

```text
IAM/
├── README.md
├── 01-Introduction-to-IAM.md
├── 02-IAM-Users.md
├── 03-IAM-Groups.md
├── 04-IAM-Policies.md
├── 05-IAM-Roles.md
├── 06-MFA.md
├── 07-IAM-Best-Practices.md
├── screenshots/
└── projects/
```

## Skills Practiced

* AWS Identity Management
* Access Control
* Permission Management
* Security Implementation
* Authentication and Authorization
* AWS Governance

## Author

**Zahrah Mukarram**

Aspiring AWS Cloud & DevOps Engineer

Building hands-on expertise in AWS, Linux, Networking, Python, and DevOps technologies.
