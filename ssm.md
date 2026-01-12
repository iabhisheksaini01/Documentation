# AWS Systems Manager (SSM) Documentation

<img width="1800" height="824" alt="ssm" src="https://github.com/user-attachments/assets/2b0055a3-ae93-4b4c-a719-0081dfbb4366" />

---

## Author Information

| Created by     | Created on  | Version | Last Updated On |
|---------------|------------|---------|-----------------|
| Abhishek Saini | 13-01-2026  | V 1.0   |  13-01-2026   |

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

This document provides an overview of AWS Systems Manager (SSM).  
It explains what SSM is, why it is used, what benefits it offers, and how it is used to securely access Amazon EC2 instances.

The document focuses on how SSM helps replace traditional SSH-based access with a more secure and controlled method.
.

---

## What is AWS SSM

AWS Systems Manager is a service that lets you securely manage and operate EC2 instances through the AWS Console, CLI, or APIs.
With Session Manager, users can open a secure terminal session directly to an EC2 instance without opening inbound ports or using SSH, where access is controlled by IAM and all activity is fully audited.

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

- The EC2 instance connects outbound to AWS SSM over HTTPS (443) using the SSM Agent.  
- The user requests access through AWS IAM.  
- AWS verifies the user’s permissions.  
- AWS creates a secure, encrypted tunnel to the instance.  
- The user gets shell access through this tunnel.  

No inbound ports or inbound connections are required.


---

## Least Privilege Access Model

Users are granted access only to the specific EC2 instances they need.  
They cannot access any other instance.

Access can be instantly removed by updating IAM policies.

---

## How to Access EC2 using SSM

### Step 1 – Prepare the EC2 Instance
Attach the IAM role: AmazonSSMManagedInstanceCore

Make sure:
- The EC2 instance has outbound internet access (via NAT Gateway or Internet Gateway)
- The SSM Agent is installed and running (most AWS AMIs have it pre-installed)

---

### Step 2 – Configure the IAM User
Create and attach an IAM policy that allows:
- ssm:StartSession  
- ssm:DescribeSessions  
- ssm:TerminateSession  
- Access only to the required EC2 instance (least-privilege)

---

### Step 3 – Connect to the Instance

```bash
aws ssm start-session --target i-xxxxxxxx
```
This opens a secure terminal session to the EC2 instance through AWS, without using SSH or opening any inbound ports.

---

## Security & Compliance

| Feature        | Benefit                     |
| -------------- | --------------------------- |
| No SSH keys    | Eliminates credential theft |
| No open ports  | EC2 not exposed to internet |
| IAM controlled | Instant access revoke       |
| Logging        | Full audit trail            |
| Encryption     | Secure communication        |


---
## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| Description                                   | References  
| --------------------------------------------  | -------------------------------------------------|
|SSM | https://aws.amazon.com/blogs/mt/how-to-grant-least-privilege-access-to-third-parties-on-your-private-ec2-instances-with-aws-systems-manager/ |
