# Multi-Factor Authentication (MFA)

## Introduction

Multi-Factor Authentication (MFA) is an additional layer of security used to protect AWS accounts and IAM users.

With MFA enabled, users must provide:

1. Username and Password
2. A temporary verification code

This significantly reduces the risk of unauthorized access.

---

## Why MFA is Important

Passwords can be:

* Weak
* Stolen
* Leaked
* Reused across multiple platforms

MFA adds a second verification factor, making it much harder for attackers to access an account.

---

## How MFA Works

```text id="mfa1"
Username + Password
          ↓
MFA Code
          ↓
Access Granted
```

Even if an attacker knows the password, they still need the MFA code.

---

## Types of MFA Devices

### Virtual MFA Device

Applications that generate one-time passwords.

Examples:

```text id="mfa2"
Google Authenticator
Microsoft Authenticator
Authy
```

---

### Hardware MFA Device

Physical devices that generate verification codes.

Example:

```text id="mfa3"
Hardware Security Key
```

---

## Enabling MFA for an IAM User

1. Open AWS Management Console
2. Navigate to IAM
3. Select Users
4. Choose the User
5. Open Security Credentials
6. Assign MFA Device
7. Configure Authenticator App
8. Verify Authentication Codes

---

## MFA for Root User

AWS strongly recommends enabling MFA for the Root User.

Benefits:

* Protects the AWS account
* Prevents unauthorized account access
* Improves overall security

---

## Benefits of MFA

* Enhanced account security
* Protection against stolen passwords
* Reduced risk of unauthorized access
* Compliance with security best practices

---

## Best Practices

### Enable MFA for Root User

Always enable MFA on the AWS Root Account.

---

### Enable MFA for Administrators

Administrative users should always use MFA.

---

### Use Authenticator Applications

Virtual MFA devices provide strong security and are easy to manage.

---

## Real-World Example

A company administrator logs into AWS.

Without MFA:

```text id="mfa4"
Username + Password
```

With MFA:

```text id="mfa5"
Username + Password
      +
Authenticator Code
```

Even if the password is compromised, attackers cannot access the account without the MFA code.

---

## Summary

* MFA adds an extra layer of security.
* Users must provide a password and a verification code.
* MFA protects IAM Users and Root Users.
* AWS recommends enabling MFA for all privileged accounts.
* MFA significantly reduces the risk of unauthorized access.
