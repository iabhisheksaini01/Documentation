# AWS IAM & SSM Role-Based Access Control Implementation

---

## Document Information

| Field | Value |
|-------|--------|
| Document Title | IAM & SSM Role-Based Access Control Setup |
| Version | 1.0 |
| Region | ap-south-1 |
| Account ID | 101936531064 |

---

# Table of Contents

1. Objective  
2. Architecture Overview  
3. IAM Group Configuration  
4. IAM Role Configuration  
5. Policy Configuration  
6. EC2 Tag-Based Restriction  
7. SSM Custom Session Documents  
8. Linux OS User Configuration  
9. Session Manager Preferences  
10. Login Flow  
11. Security Summary  

---

# 1. Objective

This document describes:

- IAM Group segregation (Developer & DevOps)
- Role-based access control using AssumeRole
- Tag-based EC2 restriction
- Custom SSM Session Documents
- OS-level least privilege enforcement
- Secure login using AWS Session Manager

---

# 2. Architecture Overview

Access Flow:

IAM User → IAM Group → Assume Role → SSM Session → EC2 Instance → OS User

| User Type | IAM Group | IAM Role | OS User | Privilege |
|------------|------------|------------|------------|------------|
| Developer | DeveloperGroup | DeveloperRole | dev1 | Non-Sudo |
| DevOps | DevOpsGroup | DevopsRole | devops1 | Sudo |

---

# 3. IAM Group Configuration

## Create DeveloperGroup

1. IAM → User Groups → Create Group  
2. Name: DeveloperGroup  

## Create DevOpsGroup

1. IAM → User Groups → Create Group  
2. Name: DevOpsGroup  

Add users accordingly.

---
# 5. Create inline policy for assume role and atttach to the groups

for Devops group
```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": "sts:AssumeRole",
			"Resource": "arn:aws:iam::101936531064:role/DevOpsRole"
		}
	]
}
```
for developer group

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": "sts:AssumeRole",
			"Resource": "arn:aws:iam::101936531064:role/DeveloperRole"
		},
		{
			"Effect": "Allow",
			"Action": "ssm:StartSession",
			"Resource": [
				"arn:aws:ssm:*:*:document/SSM-RunAs-dev1",
				"arn:aws:ec2:*:*:instance/*"
			]
		}
	]
}
```


# 4. IAM Role Configuration

## DeveloperRole

1. IAM → Roles → Create Role  
2. Trusted Entity: AWS Account  
3. Attach custom policy  
  

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"ec2:DescribeInstances",
				"ec2:DescribeInstanceStatus",
				"ssm:DescribeInstanceInformation",
				"ssm:DescribeInstanceProperties",
				"ssm:DescribeSessions",
				"ssm:GetConnectionStatus"
			],
			"Resource": "*"
		},
		{
			"Effect": "Allow",
			"Action": "ssm:StartSession",
			"Resource": "arn:aws:ec2:ap-south-1:101936531064:instance/*",
			"Condition": {
				"StringEquals": {
					"ssm:resourceTag/Access": "abhishek"
				}
			}
		},
		{
			"Effect": "Allow",
			"Action": "ssm:StartSession",
			"Resource": [
				"arn:aws:ssm:ap-south-1::document/SSM-SessionManagerRunShell",
				"arn:aws:ssm:ap-south-1:101936531064:document/SSM-Developer-Session"
			]
		},
		{
			"Effect": "Allow",
			"Action": [
				"ssm:TerminateSession",
				"ssm:ResumeSession"
			],
			"Resource": "arn:aws:ssm:ap-south-1:101936531064:session/${aws:username}-*"
		}
	]
}

```
## DevopsRole

Repeat same steps.  
Role Name: DevopsRole  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeInstanceStatus",
                "ssm:DescribeInstanceInformation",
                "ssm:DescribeInstanceProperties",
                "ssm:DescribeSessions",
                "ssm:GetConnectionStatus"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "ssm:StartSession",
            "Resource": "arn:aws:ec2:ap-south-1:101936531064:instance/*",
            "Condition": {
                "StringEquals": {
                    "ssm:resourceTag/Access": "abhishek"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "ssm:StartSession",
            "Resource": [
                "arn:aws:ssm:ap-south-1::document/SSM-SessionManagerRunShell",
                "arn:aws:ssm:ap-south-1:101936531064:document/SSM-DevOps-Session"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "ssm:TerminateSession",
                "ssm:ResumeSession"
            ],
            "Resource": "arn:aws:ssm:ap-south-1:101936531064:session/${aws:username}-*"
        }
    ]
}
```

---

# 5. Policy Configuration

Attach this policy to both roles:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:DescribeInstanceStatus",
                "ssm:DescribeInstanceInformation",
                "ssm:DescribeInstanceProperties",
                "ssm:DescribeSessions",
                "ssm:GetConnectionStatus"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "ssm:StartSession",
            "Resource": "arn:aws:ec2:ap-south-1:101936531064:instance/*",
            "Condition": {
                "StringEquals": {
                    "ssm:resourceTag/Access": "abhishek"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "ssm:StartSession",
            "Resource": [
                "arn:aws:ssm:ap-south-1::document/SSM-SessionManagerRunShell",
                "arn:aws:ssm:ap-south-1:101936531064:document/SSM-Developer-Session"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "ssm:TerminateSession",
                "ssm:ResumeSession"
            ],
            "Resource": "arn:aws:ssm:ap-south-1:101936531064:session/${aws:username}-*"
        }
    ]
}
```

---

# 6. EC2 Tag Restriction

Add tag to EC2:

Key: Access  
Value: abhishek  

---

# 7. SSM Custom Session Documents

## DevOps Session

```json
{
  "schemaVersion": "1.0",
  "description": "DevOps SSM Session",
  "sessionType": "Standard_Stream",
  "inputs": {
    "runAsEnabled": true,
    "runAsDefaultUser": "devops1"
  }
}
```

## Developer Session

```json
{
  "schemaVersion": "1.0",
  "description": "Developer SSM Session",
  "sessionType": "Standard_Stream",
  "inputs": {
    "runAsEnabled": true,
    "runAsDefaultUser": "dev1"
  }
}
```

---

# 8. Linux OS Configuration

## DevOps User (Sudo)

sudo useradd devops1  
sudo passwd devops1  
sudo usermod -aG wheel devops1  

Grant sudo in visudo:

devops1 ALL=(ALL) NOPASSWD:ALL  

## Developer User (Non-Sudo)

sudo useradd dev1  
sudo passwd dev1  

---

# 9. Session Manager Preferences

Enable Run As support  
Set default user: dev1  

---

# 10. Login Flow

## Developer

Switch Role → DeveloperRole  
Session Mana
