## AWS Systems Manager (SSM) Documentation

<img width="2000" height="824" alt="ssm" src="https://github.com/user-attachments/assets/2b0055a3-ae93-4b4c-a719-0081dfbb4366" />

---

## Author Information

| Created by     | Created on  | Version | Last Updated On |
|---------------|------------|---------|-----------------|
| Abhishek Saini | 13-01-2026  | V 1.0   |      13-01-2026            |

---

## Table of Contents
- [Introduction](#introduction)
- [What is AWS SSM](#what-is-aws-ssm)
- [Why AWS SSM](#why-aws-ssm)
- [SSM Components](#ssm-components)
- [How SSM Works](#how-ssm-works)
- [Least Privilege Access Model](#least-privilege-access-model)
- [How to Access EC2 using SSM](#how-to-access-ec2-using-ssm)
- [Security & Compliance](#security--compliance)
- [Contact Information](#contact-information)
- [References](#references)

---

## Introduction

AWS Systems Manager (SSM) is a service that enables secure and auditable access to Amazon EC2 instances without using SSH keys, public IPs, or inbound ports.  
It is designed to follow a **zero-trust and least-privilege security model**.

---

## What is AWS SSM

AWS Systems Manager is a management service that allows administrators and users to manage EC2 instances using the AWS Console, CLI, or APIs.  
Using **Session Manager**, users can open a secure terminal session directly to an EC2 instance.

---

## Why AWS SSM

Traditional EC2 access requires SSH, port 22, and key files, which introduce security risks.  
AWS SSM provides:

- No SSH keys
- No open inbound ports
- No public IP required
- Full activity logging
- IAM-based access control

---

## SSM Components

| Component | Description |
|--------|-------------|
| SSM Agent | Installed on EC2 to communicate with AWS SSM |
| Session Manager | Provides secure shell access |
| IAM Role (EC2) | Allows the instance to connect to SSM |
| IAM User Policy | Controls who can connect |
| CloudTrail / CloudWatch | Stores audit logs |

---

## How SSM Works

1. The EC2 instance connects outbound to AWS SSM over HTTPS (443).
2. The user requests access using AWS IAM.
3. AWS verifies permissions.
4. A secure encrypted tunnel is created.
5. The user gets shell access.

No inbound connection is required.

---

## Least Privilege Access Model

Users are granted access only to the specific EC2 instances they need.  
They cannot access any other instance.

Access can be instantly removed by updating IAM policies.

---

## How to Access EC2 using SSM

### Step 1 – Configure EC2
Attach IAM role: AmazonSSMManagedInstanceCore

Ensure:
- EC2 has outbound internet (NAT or IGW)
- SSM Agent is running

---

### Step 2 – Configure IAM User
Create a policy that allows:
- `ssm:StartSession`
- Only for a specific EC2 instance

---

### Step 3 – Connect

```bash
aws ssm start-session --target i-xxxxxxxx
A secure shell session opens without SSH.

---

Security & Compliance

| Feature        | Benefit                     |
| -------------- | --------------------------- |
| No SSH keys    | Eliminates credential theft |
| No open ports  | EC2 not exposed to internet |
| IAM controlled | Instant access revoke       |
| Logging        | Full audit trail            |
| Encryption     | Secure communication        |


---
