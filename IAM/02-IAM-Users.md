# IAM Users

## Introduction

An IAM User is an identity created within AWS that represents a person or application requiring access to AWS resources.

Each IAM User has its own credentials and permissions, allowing secure access to AWS services without sharing the Root Account credentials.

---

## Why Use IAM Users?

Instead of using the AWS Root User for daily tasks, organizations create IAM Users for administrators, developers, and other team members.

Benefits include:

* Improved security
* Individual accountability
* Controlled permissions
* Easier access management

---

## IAM User Credentials

An IAM User can have one or both of the following credential types:

### 1. Management Console Access

Used to sign in to the AWS Management Console.

Requirements:

* Username
* Password

Example:

```text
Username: developer1
Password: ********
```

---

### 2. Programmatic Access

Used for AWS CLI, SDKs, and automation tools.

Credentials:

```text
Access Key ID
Secret Access Key
```

Example Use Cases:

* AWS CLI
* Terraform
* Python Boto3
* Automation Scripts

---

## Creating an IAM User

### Using AWS Management Console

1. Open AWS Console
2. Navigate to IAM
3. Select Users
4. Click Create User
5. Enter User Name
6. Choose Access Type
7. Assign Permissions
8. Review and Create User

---

## Assigning Permissions

Permissions can be assigned using:

### Direct Policies

Attach policies directly to the user.

Example:

```text
AmazonS3ReadOnlyAccess
```

---

### Group Membership

Add users to groups that already have permissions.

Example:

```text
Developers Group
Administrators Group
```

This is the recommended approach.

---

## IAM User Example

A company has two employees:

```text
Ali
Sara
```

Create:

```text
IAM User: Ali
IAM User: Sara
```

Assign permissions based on their job responsibilities.

---

## IAM User vs Root User

| Feature                   | Root User | IAM User |
| ------------------------- | --------- | -------- |
| Full AWS Access           | Yes       | No       |
| Recommended for Daily Use | No        | Yes      |
| Can Be Restricted         | No        | Yes      |
| Created Automatically     | Yes       | No       |

---

## Security Best Practices

### Enable MFA

Enable Multi-Factor Authentication for all IAM users.

---

### Follow Least Privilege

Grant only the permissions required for the job.

Example:

```text
Developer:
✓ Launch EC2
✓ Access S3

✗ Delete AWS Account
✗ Modify Billing Settings
```

---

### Rotate Access Keys

Regularly update access keys to improve security.

---

### Avoid Sharing Credentials

Each user should have their own IAM account.

Never share:

```text
Passwords
Access Keys
Secret Keys
```

---

## Real-World Example

A DevOps team consists of:

```text
Admin Team
Developers
Support Engineers
```

Each team receives its own IAM Users and permissions.

This ensures secure and controlled access to AWS resources.

---

## Benefits of IAM Users

* Secure access management
* Individual user tracking
* Permission control
* Better compliance
* Improved accountability

---

## Summary

* IAM Users represent individuals or applications that require AWS access.
* Each user has unique credentials and permissions.
* IAM Users should be used instead of the Root User for daily tasks.
* Permissions can be assigned directly or through groups.
* Following security best practices helps protect AWS resources.
