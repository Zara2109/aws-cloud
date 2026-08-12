# Elastic IP (EIP)

## What is an Elastic IP?

An Elastic IP is a static public IPv4 address provided by AWS.

Unlike normal public IPs, an Elastic IP remains the same even if the instance is stopped and started.

## Why Use Elastic IP?

- Static public address
- Easy failover
- Consistent DNS mapping
- Suitable for production workloads

## How Elastic IP Works

1. Allocate an Elastic IP
2. Associate it with an EC2 instance
3. Traffic is routed through the Elastic IP

## Use Cases

- Hosting websites
- Public-facing applications
- Bastion hosts
- Disaster recovery

## Important Notes

- AWS charges for unused Elastic IPs
- One Elastic IP can be associated with only one resource at a time

## Summary

Elastic IPs provide static public addresses for AWS resources and help maintain consistent connectivity.
