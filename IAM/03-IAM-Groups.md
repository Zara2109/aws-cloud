# IAM Groups

## Introduction

An IAM Group is a collection of IAM Users.

Groups are used to simplify permission management by assigning permissions to a group instead of individual users.

When a user is added to a group, they automatically inherit all permissions assigned to that group.

---

## Why Use IAM Groups?

Managing permissions individually becomes difficult as the number of users increases.

IAM Groups help:

* Simplify permission management
* Reduce administrative effort
* Ensure consistent access control
* Improve security management

---

## How IAM Groups Work

```text id="iamgrp1"
Developers Group
        │
 ┌──────┼──────┐
 │      │      │
Ali   Sara   Ahmed
```

If the Developers Group has access to EC2 and S3, all users in that group receive the same permissions.

---

## Creating an IAM Group

### Using AWS Management Console

1. Open AWS Management Console
2. Navigate to IAM
3. Select User Groups
4. Click Create Group
5. Enter Group Name
6. Attach Policies
7. Create Group

---

## Common IAM Groups

### Administrators

Permissions:

```text id="iamgrp2"
Full AWS Access
```

Example Policy:

```text id="iamgrp3"
AdministratorAccess
```

---

### Developers

Permissions:

```text id="iamgrp4"
EC2 Access
S3 Access
CloudWatch Access
```

---

### Support Team

Permissions:

```text id="iamgrp5"
Read-Only Access
```

Example Policy:

```text id="iamgrp6"
ReadOnlyAccess
```

---

## Adding Users to a Group

Example:

```text id="iamgrp7"
Group: Developers

Users:
- Ali
- Sara
- Ahmed
```

All users automatically receive the permissions assigned to the Developers Group.

---

## IAM Group Permissions

Permissions are assigned through IAM Policies.

Example:

```text id="iamgrp8"
Developers Group
       ↓
AmazonEC2FullAccess
AmazonS3ReadOnlyAccess
```

Every user in the group inherits these permissions.

---

## Group-Based Access Management

Instead of:

```text id="iamgrp9"
Ali → EC2 Access
Sara → EC2 Access
Ahmed → EC2 Access
```

You can create:

```text id="iamgrp10"
Developers Group
      ↓
EC2 Access
```

Then add users to the group.

This approach is easier to manage.

---

## Benefits of IAM Groups

* Centralized permission management
* Easier user administration
* Consistent access control
* Reduced configuration errors
* Better scalability

---

## IAM Users vs IAM Groups

| Feature                            | IAM User | IAM Group |
| ---------------------------------- | -------- | --------- |
| Represents a person or application | Yes      | No        |
| Stores credentials                 | Yes      | No        |
| Can have permissions               | Yes      | Yes       |
| Used for permission management     | Limited  | Yes       |

---

## Best Practices

### Use Groups Instead of Individual Permissions

Recommended:

```text id="iamgrp11"
Developers Group
Administrators Group
Support Group
```

Avoid assigning the same permissions individually to multiple users.

---

### Follow Least Privilege

Grant only the permissions required to perform tasks.

---

### Organize Users by Role

Example:

```text id="iamgrp12"
Developers
Administrators
Security Team
Support Team
```

This improves access management and security.

---

## Real-World Example

A company has:

```text id="iamgrp13"
5 Developers
3 Administrators
2 Support Engineers
```

Instead of assigning permissions to each user separately:

* Create a Developers Group
* Create an Administrators Group
* Create a Support Group

Attach policies to each group and add users accordingly.

This reduces management overhead and ensures consistent permissions.

---

## Summary

* IAM Groups are collections of IAM Users.
* Groups simplify permission management.
* Users inherit permissions from the groups they belong to.
* Policies are attached to groups to control access.
* Using groups improves security, scalability, and administration.
