# AWS IAM & SSM Role-Based Access Control Implementation


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

<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/435357e4-8ab1-41be-9ba6-3b302849e087" />

---
# 4. Create inline policy for assume role and atttach to the groups

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

<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/e892bf03-c219-4831-b96c-57fe8028609c" />

---

for developer group

---
```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": "sts:AssumeRole",
			"Resource": "arn:aws:iam::101936531064:role/DeveloperRole"
		}
	]
}
```
<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/c2462205-eaf3-4af5-a1d1-df0d7929e03b" />

---

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


# 6. EC2 Tag Restriction

Add tag to EC2:

Key: Access  
Value: abhishek  

---

# 7.create  SSM Custom Session Documents

## DevOps Session
enter docunment name select session-
name=SSM-DevOps-Session 
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


name=SSM-Developer-Session 

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

<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/374a9b21-aef2-48ce-8321-e0054346994e" />
<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/762bf39e-6124-4619-abae-a6885db76b23" />




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
Set default user: dev1  for by default least privilage 

<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/f2270ccf-72f4-4039-b308-0f25ac2f6389" />


---

# 10. Login Flow

## Developer

Switch Role → DeveloperRole  
Session manager-start instance-select target instance -click on next-costume doc name-next -session started


<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/ab453f10-f753-47ab-8087-840f956dfa24" />
<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/f690c50c-a19f-4363-aa62-fec9d0d712e7" />
<img width="1847" height="965" alt="image" src="https://github.com/user-attachments/assets/81cb719a-0889-4064-998a-11e53ce5f18b" />

