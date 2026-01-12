# Least-Privilege Third-Party Access using AWS Systems Manager (SSM)

<img width="2000" height="824" alt="ssm" src="https://github.com/user-attachments/assets/c93da149-1295-462b-8a14-e3631b46e00c" />


## Table of Contents
- [Introduction](#introduction)
- [Why Third-Party Access Needs a Secure Model](#why-third-party-access-needs-a-secure-model)
- [How AWS SSM Enables Secure Third-Party Access](#how-aws-ssm-enables-secure-third-party-access)
- [Architecture for Least-Privilege Third-Party Access](#architecture-for-least-privilege-third-party-access)
- [EC2 Instance Configuration](#ec2-instance-configuration)
- [Third-Party IAM Access Control](#third-party-iam-access-control)
- [How Third-Party Access Works](#how-third-party-access-works)
- [Monitoring and Auditing](#monitoring-and-auditing)
- [Access Revocation](#access-revocation)
- [Security Benefits](#security-benefits)
- [Conclusion](#conclusion)

---

## Introduction  

This section explains how third-party vendors, support engineers, or external teams can be given secure and controlled access to private EC2 instances using AWS Systems Manager (SSM).  
It describes how AWS SSM enables organizations to grant least-privilege, time-bound, and fully audited access without exposing EC2 instances to the internet or sharing SSH keys.

---

## Why Third-Party Access Needs a Secure Model  

In traditional environments, giving a third-party access usually requires opening port 22, assigning a public IP, and sharing SSH keys.  
This creates multiple security risks:

- Servers become publicly reachable  
- SSH keys can be copied or misused  
- There is no visibility into user activity  
- Access is difficult to revoke  

This approach does not follow modern security or compliance standards.

---

## How AWS SSM Enables Secure Third-Party Access  

AWS Systems Manager removes the need for network-based access and replaces it with identity-based access.

With SSM:
- EC2 instances do not require public IPs  
- No inbound ports are opened  
- No SSH keys are shared  
- Access is controlled by IAM  

SSM creates a secure, encrypted tunnel between the user and the EC2 instance after verifying IAM permissions.

---

## Architecture for Least-Privilege Third-Party Access  

| Component | Purpose |
|--------|--------|
| EC2 IAM Role | Allows the instance to register with AWS SSM |
| IAM User / Role (Third-Party) | Defines who can access which EC2 instance |
| AWS Systems Manager | Manages sessions, security, and logging |

---

## EC2 Instance Configuration  

Each EC2 instance that should be accessed through SSM must have the IAM role:

```text
AmazonSSMManagedInstanceCore
```

This role allows the EC2 instance to:

Communicate with AWS SSM

Accept session requests

Send logs and status information

# Third-Party IAM Access Control using AWS Systems Manager (SSM)

## Third-Party IAM Access Control

Third-party users or roles are granted a dedicated IAM policy that allows only the minimum permissions required to access EC2 through AWS Systems Manager.

The policy allows:

- `ssm:StartSession`  
- `ssm:DescribeSessions`  
- `ssm:TerminateSession`  

These permissions are scoped to **only the required EC2 instance** using resource-level restrictions.  
The third-party user cannot access any other EC2 instance or AWS service.

This enforces a strict **least-privilege access model**.

---

## How Third-Party Access Works

When a third-party user starts a session, the following flow occurs:

1. The user authenticates with AWS using their IAM identity  
2. AWS evaluates the attached IAM policy  
3. AWS Systems Manager creates a secure, encrypted tunnel  
4. The SSM Agent on the EC2 instance accepts the connection  
5. The user receives shell access to the instance  

At no point is the EC2 instance exposed to the public internet.

No inbound ports, no SSH keys, and no public IP addresses are required.

---

## Monitoring and Auditing

All third-party activity is fully logged and auditable.

- **AWS CloudTrail** records:
  - Who started the session  
  - When it was started  
  - Which instance was accessed  

- **CloudWatch Logs or Amazon S3** store:
  - Session command history  
  - Terminal input and output  

This provides complete visibility, traceability, and compliance evidence.

---

## Access Revocation

Third-party access can be revoked instantly by:

- Removing or modifying the IAM policy  
- Deleting the IAM user or role  

Once access is revoked, the user cannot start new SSM sessions.

No credentials, keys, or server-side changes are required.

---

## Security Benefits

| Feature | Benefit |
|--------|---------|
| No public IP | EC2 instances remain private |
| No SSH keys | No credential leakage |
| IAM based access | Precise and controlled permissions |
| Encrypted sessions | Secure communication |
| Full logging | Complete audit trail |

---

## Conclusion

Using AWS Systems Manager for third-party access ensures that EC2 instances remain secure, private, and compliant while still allowing external teams to perform their required tasks in a controlled and auditable way.

This model replaces risky network-based access with identity-based, zero-trust access control.

