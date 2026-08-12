# AWS Key Pairs

## What is a Key Pair?

A Key Pair is a set of security credentials used to securely connect to an EC2 instance.

A key pair consists of:

- Public Key
- Private Key

AWS stores the public key on the EC2 instance, while the private key is downloaded and kept by the user.

## Why are Key Pairs Important?

Key Pairs provide secure authentication when connecting to Linux EC2 instances using SSH.

## Creating a Key Pair

1. Open AWS Console
2. Navigate to EC2
3. Select Key Pairs
4. Click Create Key Pair
5. Enter a name
6. Choose PEM format
7. Download the private key

## Connecting to EC2 Using SSH

Example command:

```bash
ssh -i my-key.pem ec2-user@<public-ip>
```

## Best Practices

- Never share your private key
- Store keys securely
- Create separate keys for different environments
- Rotate keys periodically

## Summary

Key Pairs provide secure access to EC2 instances and are an essential part of AWS security.