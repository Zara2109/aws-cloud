# EC2 User Data

## What is User Data?

User Data is a script that automatically runs when an EC2 instance launches.

It is commonly used for:

- Installing packages
- Configuring servers
- Deploying applications
- Automating setup tasks

## Example

```bash
#!/bin/bash

yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd

echo "<h1>Hello from EC2</h1>" > /var/www/html/index.html
```

## Benefits

- Automation
- Consistency
- Faster deployments
- Reduced manual effort

## Summary

User Data helps automate EC2 instance configuration during launch.
```