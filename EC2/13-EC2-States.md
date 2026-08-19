# EC2 Instance States

## Introduction

Every Amazon EC2 instance goes through a series of states during its lifecycle. Understanding these states helps administrators monitor, manage, and troubleshoot EC2 instances effectively.

---

## EC2 Instance Lifecycle

```text
Pending → Running → Stopping → Stopped
                 ↓
             Rebooting
                 ↓
            Terminated
```

---

## 1. Pending State

When an EC2 instance is launched, AWS prepares the required resources.

### Activities Performed

* Allocates compute resources
* Attaches storage volumes
* Configures networking
* Initializes the operating system

### Characteristics

* Temporary state
* User cannot access the instance yet

---

## 2. Running State

The instance is fully operational and ready for use.

### Characteristics

* Applications can run
* SSH or RDP access is available
* Billing is active

### Common Activities

* Deploy applications
* Host websites
* Run databases

---

## 3. Stopping State

The instance is in the process of shutting down.

### Characteristics

* Temporary state
* AWS saves the instance configuration
* Billing for compute resources stops after the instance is fully stopped

---

## 4. Stopped State

The instance is powered off but still exists.

### Characteristics

* Data on EBS volumes remains available
* Compute charges stop
* Storage charges continue

### Common Uses

* Cost optimization
* Temporary shutdown of development environments

---

## 5. Rebooting State

A reboot restarts the operating system without stopping the instance.

### Characteristics

* Instance ID remains the same
* Public and private IP addresses remain unchanged
* Faster than stopping and starting

### Use Cases

* Applying updates
* Restarting services

---

## 6. Terminated State

The instance is permanently deleted.

### Characteristics

* Instance cannot be restarted
* Instance ID is lost
* Attached storage may be deleted depending on configuration

### Use Cases

* Removing unused resources
* Cost management

---

## State Transitions

| State      | Description                  |
| ---------- | ---------------------------- |
| Pending    | Instance is launching        |
| Running    | Instance is active           |
| Stopping   | Instance is shutting down    |
| Stopped    | Instance is powered off      |
| Rebooting  | Operating system restart     |
| Terminated | Instance permanently deleted |

---

## Important Notes

* Stopping an instance preserves EBS data.
* Terminating an instance permanently removes the instance.
* Rebooting does not change the instance ID.
* Only EBS-backed instances can be stopped and restarted.

---

## Summary

* EC2 instances move through different lifecycle states.
* Running instances are active and billable.
* Stopped instances save costs while preserving data.
* Rebooting restarts the operating system without deleting resources.
* Terminated instances cannot be recovered.
