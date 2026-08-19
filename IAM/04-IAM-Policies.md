# IAM Policies

## Introduction

IAM Policies are JSON documents that define permissions in AWS.

They determine:

* What actions are allowed or denied
* Which AWS resources can be accessed
* Under what conditions access is granted

Policies are attached to:

* IAM Users
* IAM Groups
* IAM Roles

---

## Why IAM Policies are Important

IAM Policies help enforce security and access control by defining exactly what a user or service can do within an AWS environment.

Example:

```text
Developer:
✓ Launch EC2 Instances
✓ View S3 Buckets

✗ Delete IAM Users
✗ Access Billing Information
```

---

## Policy Structure

IAM Policies are written in JSON format.

Example:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "*"
    }
  ]
}
```

---

## Main Components of a Policy

### Version

Specifies the policy language version.

Example:

```json
"Version": "2012-10-17"
```

---

### Effect

Determines whether access is allowed or denied.

Values:

```text
Allow
Deny
```

Example:

```json
"Effect": "Allow"
```

---

### Action

Specifies what action can be performed.

Examples:

```text
ec2:StartInstances
ec2:StopInstances
s3:ListBucket
s3:GetObject
```

---

### Resource

Specifies the AWS resource affected by the policy.

Example:

```json
"Resource": "*"
```

or

```json
"Resource": "arn:aws:s3:::my-bucket"
```

---

## Types of IAM Policies

### 1. AWS Managed Policies

Created and maintained by AWS.

Examples:

```text
AdministratorAccess
AmazonS3ReadOnlyAccess
AmazonEC2FullAccess
```

Benefits:

* Easy to use
* Automatically updated by AWS

---

### 2. Customer Managed Policies

Created and managed by AWS customers.

Benefits:

* Custom permissions
* Greater control

Example:

```text
Allow EC2 Access Only
```

---

### 3. Inline Policies

Policies embedded directly into a User, Group, or Role.

Characteristics:

* One-to-one relationship
* Deleted with the identity

Use Cases:

* Special permissions for a single user

---

## Policy Evaluation Logic

AWS evaluates all applicable policies before granting access.

### Access Allowed

```text
User
 ↓
Policy
 ↓
Allow
 ↓
Access Granted
```

---

### Access Denied

```text
User
 ↓
Policy
 ↓
Deny
 ↓
Access Denied
```

---

## Explicit Deny vs Allow

AWS always prioritizes:

```text
Explicit Deny > Allow
```

Example:

```text
Policy A → Allow S3 Access

Policy B → Deny S3 Access
```

Result:

```text
Access Denied
```

---

## Example Policy: Read-Only Access to S3

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:ListBucket"
      ],
      "Resource": "*"
    }
  ]
}
```

---

## Example Policy: Start and Stop EC2 Instances

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:StartInstances",
        "ec2:StopInstances"
      ],
      "Resource": "*"
    }
  ]
}
```

---

## Best Practices

### Follow Least Privilege

Grant only required permissions.

---

### Use Groups

Attach policies to groups instead of individual users whenever possible.

---

### Prefer Managed Policies

Use AWS Managed Policies when suitable.

---

### Review Permissions Regularly

Remove unused permissions to reduce security risks.

---

## Real-World Example

A company has a development team that needs:

```text
✓ Launch EC2 Instances
✓ Access S3 Buckets

✗ Delete IAM Users
✗ Manage Billing
```

An IAM Policy is created and attached to the Developers Group.

All developers inherit the required permissions while maintaining security.

---

## Summary

* IAM Policies define permissions in AWS.
* Policies are written in JSON format.
* Policies can be attached to Users, Groups, and Roles.
* AWS supports Managed, Customer Managed, and Inline Policies.
* Explicit Deny always overrides Allow.
* Following least privilege improves AWS security.
