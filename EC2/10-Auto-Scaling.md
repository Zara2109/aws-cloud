# AWS Auto Scaling

## What is Auto Scaling?

Auto Scaling automatically adds or removes EC2 instances based on application demand.

It helps maintain performance while reducing costs.

## Benefits

- High Availability
- Cost Optimization
- Improved Performance
- Automatic Scaling

## Key Components

### Launch Template

Defines:

- AMI
- Instance Type
- Security Groups
- Storage

### Auto Scaling Group (ASG)

Manages a collection of EC2 instances.

### Scaling Policies

Determine when instances are added or removed.

## Scaling Types

### Dynamic Scaling

Automatically adjusts capacity based on metrics.

Example:

- CPU > 70% → Add Instance
- CPU < 30% → Remove Instance

### Scheduled Scaling

Scale resources at specific times.

Example:

- Increase capacity during business hours.

## Example Architecture

Internet
↓
Load Balancer
↓
Auto Scaling Group
↓
EC2 Instances

## Summary

Auto Scaling ensures applications remain responsive while minimizing infrastructure costs.