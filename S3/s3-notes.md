# Amazon S3 (Simple Storage Service)

## What is Amazon S3?

Amazon S3 is an object storage service that provides:

- High scalability
- High availability
- Data durability (99.999999999% - 11 Nines)
- Security
- Cost-effective storage

Amazon S3 stores data as **Objects** inside **Buckets**.

---

## Key Components

### 1. Bucket

A bucket is a container used to store objects.

**Example:**

```text
Bucket Name: zahrah-cloud-storage
```

**Bucket Naming Rules:**

- Must be globally unique
- Must be lowercase
- Length between 3 and 63 characters
- Cannot contain spaces

---

### 2. Object

An object is a file stored in S3.

Examples:

```text
resume.pdf
image.png
backup.zip
```

Each object contains:

- Data
- Metadata
- Key

---

### 3. Key

A key is the unique identifier of an object within a bucket.

**Examples:**

```text
documents/resume.pdf
images/profile.jpg
```

---

## S3 Storage Classes

### S3 Standard

- Frequently accessed data
- Low latency
- High availability

**Use Cases:**

- Websites
- Mobile applications
- Active business data

---

### S3 Standard-Infrequent Access (Standard-IA)

- Less frequently accessed data
- Lower storage cost
- Retrieval fee applies

**Use Cases:**

- Backups
- Disaster recovery

---

### S3 One Zone-IA

- Data stored in a single Availability Zone
- Lower cost than Standard-IA

**Use Cases:**

- Secondary backups
- Easily reproducible data

---

### S3 Glacier Instant Retrieval

- Archive storage
- Millisecond retrieval

**Use Cases:**

- Medical records
- Archived images

---

### S3 Glacier Flexible Retrieval

- Retrieval in minutes to hours

**Use Cases:**

- Long-term backups
- Archive data

---

### S3 Glacier Deep Archive

- Lowest-cost storage
- Retrieval in hours

**Use Cases:**

- Compliance records
- Long-term archives

---

## S3 Features

### Versioning

Stores multiple versions of an object.

**Benefits:**

- Recover deleted files
- Restore previous versions
- Protection against accidental overwrites

---

### Lifecycle Rules

Automatically move objects between storage classes.

**Example:**

```text
After 30 Days → Standard-IA
After 90 Days → Glacier
```

**Benefits:**

- Cost optimization
- Automated storage management

---

### Cross-Region Replication (CRR)

Replicates objects to another AWS Region.

**Benefits:**

- Disaster recovery
- Compliance requirements

**Requirement:**

- Versioning must be enabled

---

### Same-Region Replication (SRR)

Replicates objects within the same AWS Region.

**Benefits:**

- Log aggregation
- Data sharing

---

### Encryption

#### SSE-S3

- AWS manages encryption keys

#### SSE-KMS

- Uses AWS Key Management Service (KMS)

#### SSE-C

- Customer manages encryption keys

---

## S3 Security

### Bucket Policies

JSON-based policies attached directly to buckets.

**Example:**

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mybucket/*"
    }
  ]
}
```

---

### IAM Policies

Control access through:

- IAM Users
- IAM Groups
- IAM Roles

**Example:**

```text
Allow User → Upload Objects
Deny User → Delete Objects
```

---

### Block Public Access

AWS security feature that prevents accidental public exposure of buckets.

**Recommendation:**

```text
Enable for production workloads
```

---

## Static Website Hosting

Amazon S3 can host static websites.

**Supported Files:**

- HTML
- CSS
- JavaScript

### Steps

1. Create an S3 Bucket
2. Enable Static Website Hosting
3. Upload Website Files
4. Configure Bucket Policy
5. Access Website URL

**Example URL:**

```text
http://bucket-name.s3-website-region.amazonaws.com
```

---

## S3 Event Notifications

S3 can trigger actions when events occur.

### Supported Events

- Object Upload
- Object Delete
- Object Restore

### Targets

- AWS Lambda
- Amazon SNS
- Amazon SQS

---

## AWS CLI Commands

### Create Bucket

```bash
aws s3 mb s3://zahrah-cloud-storage
```

### List Buckets

```bash
aws s3 ls
```

### Upload File

```bash
aws s3 cp file.txt s3://zahrah-cloud-storage
```

### Download File

```bash
aws s3 cp s3://zahrah-cloud-storage/file.txt .
```

### Sync Folder

```bash
aws s3 sync ./website s3://zahrah-cloud-storage
```

### Delete File

```bash
aws s3 rm s3://zahrah-cloud-storage/file.txt
```

### Delete Bucket

```bash
aws s3 rb s3://zahrah-cloud-storage
```

---

# S3 vs EBS

| Feature | Amazon S3 | Amazon EBS |
|----------|-----------|------------|
| Storage Type | Object Storage | Block Storage |
| Attachment | Standalone Service | Attached to EC2 |
| Availability | Regional | Single AZ |
| Scalability | Unlimited | Limited by Volume Size |
| Use Case | Files, Backups, Websites | Operating Systems, Databases |

---