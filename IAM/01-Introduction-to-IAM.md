# Introduction to IAM

## What is IAM?

AWS Identity and Access Management (IAM) is a service that helps you securely manage access to AWS resources.

IAM allows you to control:

* Who can access AWS resources
* What actions they can perform
* Which AWS services they can use

IAM is a global AWS service and is provided at no additional cost.

---

## Why IAM is Important

Without IAM, every user would need to share the AWS Root Account credentials.

This creates security risks and makes access management difficult.

IAM helps organizations:

* Improve security
* Follow the principle of least privilege
* Manage multiple users efficiently
* Control access to AWS resources

---

## Key Components of IAM

### Users

An IAM User represents a person or application that needs access to AWS.

Examples:

```text id="iamu1"
Admin User
Developer User
Application User
```

---

### Groups

A Group is a collection of IAM users.

Permissions can be assigned to the group instead of individual users.

Example:

```text id="iamg1"
Developers Group
Administrators Group
Support Team Group
```

---

### Policies

Policies are JSON documents that define permissions.

They specify:

* Allowed actions
* AWS resources
* Access conditions

Example:

```text id="iamp1"
Allow access to Amazon S3

Deny access to EC2
```

---

### Roles

IAM Roles provide temporary permissions to AWS services or users.

Common examples:

```text id="iamr1"
EC2 accessing S3

Lambda accessing DynamoDB
```

---

## IAM Authentication Methods

AWS supports:

### Username and Password

Used for AWS Management Console access.

### Access Keys

Used for:

* AWS CLI
* SDKs
* Programmatic Access

Example:

```text id="iamk1"
Access Key ID

Secret Access Key
```

---

## Root User vs IAM User

| Feature                            | Root User | IAM User                  |
| ---------------------------------- | --------- | ------------------------- |
| Created when AWS account is opened | Yes       | No                        |
| Full AWS access                    | Yes       | Only assigned permissions |
| Recommended for daily use          | No        | Yes                       |
| Can create IAM users               | Yes       | With permissions          |

---

## Principle of Least Privilege

Users should only receive permissions required to perform their tasks.

Example:

```text id="iamlp1"
Developer

Can:
- Launch EC2
- View S3 Buckets

Cannot:
- Delete AWS Account
- Modify Billing Settings
```

This improves security and reduces risk.

---

## Benefits of IAM

* Secure access management
* Fine-grained permissions
* Multi-user support
* Integration with AWS services
* Improved compliance and security

---

## Real-World Example

A company has three teams:

```text id="iamreal1"
Administrators
Developers
Support Engineers
```

Using IAM:

* Administrators receive full access
* Developers receive EC2 and S3 permissions
* Support Engineers receive read-only access

This ensures users only access resources relevant to their job roles.

---

## Summary

* IAM stands for Identity and Access Management.
* IAM controls authentication and authorization in AWS.
* Core IAM components include Users, Groups, Policies, and Roles.
* IAM helps secure AWS environments through controlled access.
* Following the principle of least privilege improves security and governance.
