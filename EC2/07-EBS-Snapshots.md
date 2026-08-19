# EBS Snapshots

## Introduction

An EBS Snapshot is a backup of an Amazon Elastic Block Store (EBS) volume.

Snapshots are stored in Amazon S3 and can be used to restore data, create new volumes, or recover from accidental data loss.

They provide a simple and reliable way to protect data stored on EBS volumes.

---

## Why Use EBS Snapshots?

EBS Snapshots help:

* Backup important data
* Recover deleted or corrupted data
* Create duplicate environments
* Migrate data between regions
* Improve disaster recovery

---

## How EBS Snapshots Work

```text
EBS Volume
     ↓
Create Snapshot
     ↓
Stored in Amazon S3
     ↓
Restore when needed
```

Snapshots capture the data stored on an EBS volume at a specific point in time.

---

## Incremental Snapshots

EBS Snapshots are incremental.

This means:

* The first snapshot copies all data.
* Subsequent snapshots only save blocks that have changed since the previous snapshot.

### Example

```text
Snapshot 1 → 100 GB

Snapshot 2 → Only changed blocks

Snapshot 3 → Only changed blocks
```

### Benefits

* Faster backups
* Reduced storage costs
* Efficient data protection

---

## Creating an EBS Snapshot

### Using AWS Management Console

1. Open the EC2 Dashboard
2. Select Volumes
3. Choose the EBS Volume
4. Click Actions
5. Select Create Snapshot
6. Enter a description
7. Create Snapshot

---

## Restoring a Snapshot

A snapshot cannot be attached directly to an EC2 instance.

Instead:

1. Open Snapshots
2. Select the Snapshot
3. Click Create Volume
4. Choose Availability Zone
5. Create Volume
6. Attach the new volume to an EC2 instance

---

## Copying Snapshots

AWS allows snapshots to be copied between regions.

### Use Cases

* Disaster Recovery
* Multi-region backup
* Data migration

Example:

```text
Mumbai Region
      ↓
Copy Snapshot
      ↓
Singapore Region
```

---

## Snapshot Lifecycle

```text
Create Volume
      ↓
Store Data
      ↓
Create Snapshot
      ↓
Modify Data
      ↓
Create New Snapshot
      ↓
Restore if Required
```

---

## Snapshot Pricing

AWS charges for:

* Snapshot storage used
* Additional changed data blocks

Because snapshots are incremental, only changed blocks consume extra storage.

This helps reduce backup costs.

---

## Real-World Example

A company hosts a web application on an EC2 instance with an attached EBS volume.

Before performing a major software upgrade:

1. Create an EBS Snapshot
2. Perform the upgrade
3. If the upgrade fails, restore the snapshot
4. Continue operations with minimal downtime

This provides a reliable rollback mechanism.

---

## Benefits of EBS Snapshots

* Automatic backup solution
* Incremental storage
* Easy recovery
* Cross-region copy support
* Disaster recovery capability

---

## EBS Snapshot vs EBS Volume

| Feature     | EBS Volume               | EBS Snapshot           |
| ----------- | ------------------------ | ---------------------- |
| Purpose     | Storage Device           | Backup                 |
| Data Access | Directly Attached to EC2 | Must be Restored First |
| Location    | Availability Zone        | Amazon S3              |
| Persistence | Active Storage           | Backup Storage         |

---

## Best Practices

* Create snapshots before major changes.
* Use snapshots for disaster recovery.
* Delete unused snapshots to reduce costs.
* Copy critical snapshots to another region.
* Automate backups using AWS Backup or Lifecycle Manager.

---

## Summary

* EBS Snapshots are backups of EBS volumes.
* Snapshots are stored in Amazon S3.
* AWS uses incremental snapshots to save storage and reduce costs.
* Snapshots can be used to restore data and create new volumes.
* They are an important part of backup and disaster recovery strategies in AWS.
