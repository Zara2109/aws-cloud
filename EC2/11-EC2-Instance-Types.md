# EC2 Instance Types

## What are EC2 Instance Types?

Amazon EC2 Instance Types define the hardware configuration of an EC2 instance. They determine the amount of CPU, memory, storage, and networking capacity available for your application.

AWS provides different instance families designed for specific workloads.

---

## Why Instance Types Matter

Choosing the right instance type helps:

* Optimize performance
* Reduce costs
* Match workload requirements
* Improve scalability

---

## Naming Convention

Example:

```text
t2.micro
```

Where:

* **t** = Instance family
* **2** = Generation
* **micro** = Instance size

---

## Common EC2 Instance Families

### 1. General Purpose Instances

Balanced compute, memory, and networking.

Examples:

* t2.micro
* t3.micro
* t3.small

Use Cases:

* Web servers
* Small databases
* Development environments
* Testing applications

---

### 2. Compute Optimized Instances

Designed for CPU-intensive workloads.

Examples:

* C5
* C6i

Use Cases:

* High-performance web servers
* Gaming servers
* Scientific computations
* Batch processing

---

### 3. Memory Optimized Instances

Designed for memory-intensive applications.

Examples:

* R5
* R6i

Use Cases:

* In-memory databases
* Big data analytics
* Real-time processing

---

### 4. Storage Optimized Instances

Designed for high-speed local storage.

Examples:

* I3
* D2

Use Cases:

* Data warehousing
* Log processing
* Large-scale databases

---

## Instance Sizes

AWS provides multiple sizes within each family.

Example:

```text
t3.nano
t3.micro
t3.small
t3.medium
t3.large
```

As size increases:

* More CPU
* More RAM
* Higher network performance

---

## Free Tier Instance

AWS Free Tier includes:

```text
t2.micro
```

or

```text
t3.micro
```

(depending on AWS region and account eligibility)

These are commonly used for learning and practice.

---

## How to Select an Instance Type

When launching an EC2 instance:

1. Open EC2 Dashboard
2. Click Launch Instance
3. Select an AMI
4. Choose an Instance Type
5. Configure storage and networking
6. Launch the instance

---

## Summary

* EC2 Instance Types define compute resources.
* Different families are optimized for different workloads.
* General Purpose instances are best for beginners.
* Compute, Memory, and Storage Optimized instances are designed for specialized applications.
* Selecting the correct instance type improves both performance and cost efficiency.
