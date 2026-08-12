# Amazon Machine Image (AMI)

## What is an AMI?

An Amazon Machine Image (AMI) is a pre-configured template used to launch EC2 instances.

An AMI contains:

- Operating System
- Application Server (optional)
- Applications (optional)
- Configuration Settings

## Why Use AMIs?

AMIs help you launch identical EC2 instances quickly and consistently.

Benefits:

- Faster deployment
- Consistent configuration
- Easy backup and recovery
- Reusable infrastructure

## Types of AMIs

### 1. AWS Provided AMIs
Prebuilt AMIs maintained by AWS.

Examples:
- Amazon Linux
- Ubuntu
- Windows Server

### 2. Marketplace AMIs
Created by third-party vendors.

### 3. Custom AMIs
Created by users from existing EC2 instances.

## Creating a Custom AMI

1. Select an EC2 instance
2. Click Actions
3. Select Image and Templates
4. Choose Create Image
5. Enter Image Name
6. Create AMI

## AMI vs Snapshot

| AMI | Snapshot |
|------|---------|
| Complete machine template | Backup of EBS volume |
| Used to launch instances | Used to restore storage |
| Includes OS and configuration | Stores volume data only |

## Real-World Use Case

Suppose you configure:

- Apache Web Server
- Security Settings
- Application Code

Instead of repeating the setup every time, create an AMI and launch new instances from it.

## Summary

AMIs allow rapid and consistent deployment of EC2 instances and are a key component of AWS infrastructure automation.