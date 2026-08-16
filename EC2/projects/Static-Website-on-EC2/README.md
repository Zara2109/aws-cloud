# Static Website Hosting on Amazon EC2

## Project Overview

This project demonstrates how to host a static website on an Amazon EC2 instance using Apache Web Server.

## Services Used

- Amazon EC2
- Security Groups
- Amazon Linux
- Apache HTTP Server

## Steps Performed

### 1. Launch EC2 Instance

- Selected Amazon Linux
- Configured Security Group
- Allowed HTTP and SSH traffic

### 2. Connect to EC2

```bash
ssh -i my-key.pem ec2-user@<public-ip>
```

### 3. Install Apache

```bash
sudo yum update -y
sudo yum install httpd -y
```

### 4. Start Apache

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

### 5. Create Web Page

```bash
echo "<h1>Hello from EC2</h1>" | sudo tee /var/www/html/index.html
```

### 6. Access Website

Open:

```text
http://<public-ip>
```

## Outcome

Successfully deployed and accessed a static website hosted on an EC2 instance.


# Amazon EC2

![AWS](https://img.shields.io/badge/AWS-EC2-orange)
![Linux](https://img.shields.io/badge/Linux-Administration-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

## Author

Zahrah Mukarram