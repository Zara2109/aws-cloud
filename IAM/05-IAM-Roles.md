# IAM Roles

## Introduction

An IAM Role is an AWS identity that provides temporary permissions to users, applications, or AWS services.

Unlike IAM Users, IAM Roles do not have:

* Username
* Password
* Access Keys

Instead, roles are assumed when access is required.

---

## Why Use IAM Roles?

IAM Roles provide temporary credentials and eliminate the need to store long-term access keys.

Benefits:

* Improved security
* Temporary permissions
* Easier access management
* Reduced credential exposure

---

## How IAM Roles Work

```text id="role1"
User / Service
       ↓
Assume Role
       ↓
Temporary Credentials
       ↓
Access AWS Resources
```

The role grants permissions only while it is being used.

---

## IAM User vs IAM Role

| Feature                       | IAM User | IAM Role |
| ----------------------------- | -------- | -------- |
| Permanent Identity            | Yes      | No       |
| Username                      | Yes      | No       |
| Password                      | Yes      | No       |
| Access Keys                   | Yes      | No       |
| Temporary Credentials         | No       | Yes      |
| Commonly Used By AWS Services | No       | Yes      |

---

## Components of an IAM Role

### Trusted Entity

Defines who can assume the role.

Examples:

```text id="role2"
EC2
Lambda
Another AWS Account
IAM User
```

---

### Permissions Policy

Defines what actions are allowed.

Example:

```text id="role3"
Read objects from S3
Write logs to CloudWatch
Access DynamoDB
```

---

## Common IAM Role Use Cases

### 1. EC2 Accessing S3

Instead of storing AWS Access Keys inside an EC2 instance:

```text id="role4"
EC2 Instance
      ↓
IAM Role
      ↓
Amazon S3
```

AWS automatically provides temporary credentials.

---

### 2. Lambda Accessing DynamoDB

```text id="role5"
Lambda Function
       ↓
IAM Role
       ↓
DynamoDB
```

The Lambda function uses the role to access the database securely.

---

### 3. Cross-Account Access

A user from one AWS account can assume a role in another AWS account.

```text id="role6"
Account A
      ↓
Assume Role
      ↓
Account B
```

Useful for multi-account environments.

---

## Creating an IAM Role

1. Open AWS Management Console
2. Navigate to IAM
3. Select Roles
4. Click Create Role
5. Select Trusted Entity
6. Attach Permissions
7. Name the Role
8. Create Role

---

## Example: EC2 Role for S3 Access

### Step 1

Create a role.

Trusted Entity:

```text id="role7"
AWS Service
EC2
```

### Step 2

Attach policy:

```text id="role8"
AmazonS3ReadOnlyAccess
```

### Step 3

Attach the role to an EC2 instance.

The instance can now access S3 without storing access keys.

---

## Benefits of IAM Roles

* No long-term credentials
* Improved security
* Temporary permissions
* Easy integration with AWS services
* Supports cross-account access

---

## Best Practices

### Use Roles Instead of Access Keys

Recommended:

```text id="role9"
EC2 → IAM Role → S3
```

Avoid:

```text id="role10"
EC2 → Stored Access Keys → S3
```

---

### Follow Least Privilege

Grant only required permissions.

---

### Rotate Permissions Regularly

Review and update role permissions periodically.

---

## Real-World Example

A company hosts an application on EC2.

The application needs access to files stored in an S3 bucket.

Instead of storing AWS credentials on the server:

```text id="role11"
EC2 Instance
      ↓
IAM Role
      ↓
Amazon S3
```

The EC2 instance receives temporary credentials automatically and securely accesses the bucket.

---

## Summary

* IAM Roles provide temporary AWS permissions.
* Roles do not have usernames, passwords, or access keys.
* AWS services commonly use roles to access resources securely.
* Roles improve security by eliminating long-term credentials.
* EC2, Lambda, and cross-account access are common IAM Role use cases.
