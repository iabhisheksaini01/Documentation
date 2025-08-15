# Sonarqube AWS Infrastructure 

<div align="center">
  <img src="https://github.com/user-attachments/assets/54861347-0bdb-4f49-aeb5-5dc559dc27f3" width="600" height="500" alt="image">
</div>



## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  14-08-2025        | V 1.0            |    |  Prashant          |  -      |      -  |  - |

---

## Table of Contents

- [Introduction](#introduction)
- [Architecture Overview](#architecture-overview)
- [Infrastructure Diagram](#infrastructure-diagram)
- [Network Design](#network-design)
- [Infrastructure Diagram](#infrastructure-diagram)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)


## Introduction
This document describes the high availability and secure deployment of SonarQube on AWS using a multi-AZ architecture with Application Load Balancer (ALB), Auto Scaling Group (ASG), Bastion Host, NAT Gateway, and Network ACLs.  
The design ensures fault tolerance, scalability, and controlled access.

---
## AWS SonarQube Deployment Architecture

The SonarQube environment is deployed within a VPC in AWS Mumbai Region (ap-south-1), designed for high availability, scalability, and security. The architecture includes the following key components:

---

#### 1. Public Subnets
- **Bastion Host:** Provides secure SSH access to instances in private subnets.  
- **NAT Gateway:** Enables outbound internet connectivity for private resources while keeping them isolated from direct internet access.

#### 2. Private Subnets
- Hosts SonarQube application instances.  
- Isolated from the internet to ensure enhanced security.

#### 3. Multi-AZ Deployment
- Instances are spread across multiple Availability Zones for fault tolerance and high availability.

#### 4. Auto Scaling Group (ASG)
- Automatically scales the SonarQube EC2 instances based on traffic and load, ensuring optimal resource utilization.

#### 5. Application Load Balancer (ALB) & Target Group
- Distributes incoming traffic evenly across SonarQube instances.  
- Improves performance, fault tolerance, and availability

#### 6. Security & Connectivity
- Bastion Host: Central point for secure SSH management of private instances.  
- NAT Gateway: Allows private instances to access the internet without exposing them directly.

> This architecture ensures a secure, scalable, and highly available SonarQube deployment in AWS.

---

## Network Design

#### VPC
- **CIDR:**:10.0.0.0/24
- **Region:**:ap-south-1

#### Subnets

| Subnet Type      | CIDR            | Availability Zone | Purpose                               |
|------------------|-----------------|-------------------|---------------------------------------|
| Public Subnet 1  | `10.0.0.0/26`   | ap-south-1a       | Bastion Host, NAT Gateway, ALB        |
| Private Subnet 1 | `10.0.0.128/26` | ap-south-1a       | SonarQube EC2 instance (via ASG)      |
| Private Subnet 2 | `10.0.0.192/26` | ap-south-1b       | SonarQube EC2 instance (via ASG)      |

---

## Infrastructure Diagram

![sonarqube](https://github.com/user-attachments/assets/4eb20994-6ec1-486f-9a9e-662369cb5c1c)

---

## Conclusion

The SonarQube infrastructure is highly available, scalable, and secure, using ASG-backed EC2 instances behind an ALB. It ensures fault tolerance, smooth traffic distribution, and network isolation while supporting automated code quality analysis for CI/CD pipelines. This setup provides a robust and future-ready foundation for maintaining code quality and developer productivity.

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| Source                                                                                  | Description                              |
|-----------------------------------------------------------------------------------------|------------------------------------------|
| [SonarQube Official Docs](https://docs.sonarqube.org/)                                  | Main SonarQube Documentation             |
| [SonarQube Installation Guide](https://docs.sonarqube.org/latest/setup/install-server/) | Step-by-step guide to install SonarQube |
