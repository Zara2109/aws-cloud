# Security Groups in AWS

## What is a Security Group?

A Security Group acts as a virtual firewall for your EC2 instance. It controls inbound and outbound traffic.

## Key Features

- Instance-level firewall
- Stateful
- Allows only permitted traffic
- Can have multiple rules

## Inbound Rules

Inbound rules control traffic coming into the EC2 instance.

Examples:
- HTTP (Port 80)
- HTTPS (Port 443)
- SSH (Port 22)

## Outbound Rules

Outbound rules control traffic leaving the EC2 instance.

By default, all outbound traffic is allowed.

## Common Ports

| Port | Protocol | Purpose |
|--------|----------|----------|
| 22 | SSH | Remote Login |
| 80 | HTTP | Web Traffic |
| 443 | HTTPS | Secure Web Traffic |

## Example

To access an EC2 instance through SSH:

- Protocol: TCP
- Port: 22
- Source: Your IP Address

## Summary

Security Groups help protect EC2 instances by controlling network traffic and are an essential part of AWS security.
