# Amazon Elastic Block Store (EBS)

## What is EBS?

Amazon Elastic Block Store (EBS) provides persistent block storage for EC2 instances.

EBS volumes act like virtual hard disks that can be attached to EC2 instances.

## Key Features

- Persistent storage
- High availability
- Scalable
- Snapshot support
- Encryption support

## Types of EBS Volumes

### General Purpose SSD (gp3)

- Default volume type
- Good balance of performance and cost
- Suitable for most workloads

### Provisioned IOPS SSD (io2)

- High-performance workloads
- Databases
- Critical applications

### Throughput Optimized HDD (st1)

- Frequently accessed data
- Big data workloads

### Cold HDD (sc1)

- Infrequently accessed data
- Lowest cost option

## EBS Volume Lifecycle

1. Create Volume
2. Attach Volume to EC2
3. Format Volume
4. Mount Volume
5. Store Data

## Creating an EBS Volume

1. Open EC2 Console
2. Select Volumes
3. Click Create Volume
4. Choose Size and Type
5. Create Volume
6. Attach to Instance

## EBS Snapshots

Snapshots are backups of EBS volumes stored in Amazon S3.

Benefits:

- Backup and recovery
- Disaster recovery
- Migration
- AMI creation

## EBS vs Instance Store

| EBS | Instance Store |
|------|------|
| Persistent | Temporary |
| Data survives reboot | Data lost when instance stops |
| Supports snapshots | No snapshots |

## Summary

Amazon EBS provides durable and scalable block storage for EC2 instances and is widely used for operating systems, databases, and application data.