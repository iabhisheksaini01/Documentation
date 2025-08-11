<p align="center">
  <img src="https://github.com/user-attachments/assets/12c81a6b-c661-46dd-996f-938c8a236448" alt="Jenkins HA Diagram">
</p>

# **Documentation of Jenkins High Availability**


## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  11-08-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |


---

## **Table of Contents**  

- [Introduction](#introduction)  
- [Why Jenkins HA?](#why-jenkins-ha)  
- [Architecture of Master-Slave](#architecture-of-master-slave)  
- [Setup Steps](#setup-steps)  
- [Active/Passive Nodes](#activepassive-nodes)  
- [Benefits](#benefits)  
- [Conclusion](#conclusion)  
- [Contact](#contact)  
- [References](#references)  

---

## **Introduction**  

Jenkins High Availability (HA) ensures continuous CI/CD execution even during failures. It minimizes downtime and supports consistent software delivery through redundancy, load distribution, and automatic failover systems.

### **HA setup options:**  
- **Active/Passive:** A standby Jenkins instance is kept ready to take over on failure.  
- **Autoscaling Group:** Utilizes cloud auto-scaling to manage Jenkins nodes dynamically.

---

## **Why Jenkins HA?**  

| **Benefit**            | **Description**  |  
|------------------------|------------------|  
| **No Downtime**        | Jenkins remains available during failures. |  
| **Scalability**        | Automatically scales based on workloads. |  
| **Load Balancing**     | Distributes job execution across nodes. |  
| **Business Continuity**| Maintains uninterrupted development pipelines. |  

---

## **Architecture of Master-Slave**  

Jenkins HA often leverages a **Master-Agent** or **Multi-Master** structure to balance loads and improve system availability.

| **Component**          | **Function**  |  
|------------------------|---------------|  
| **Jenkins Master**     | Orchestrates jobs, manages schedules, and distributes work. |  
| **Jenkins Agents**     | Run builds and offload processing from the master. |  
| **Shared Storage**     | Centralized storage for builds, configs, and logs. |  
| **Database Replication**| Synchronizes Jenkins job data and configuration. |  
| **Load Balancer**      | Routes incoming traffic between Jenkins instances. |  

### **Architecture Diagram**  
![Architecture Diagram](https://github.com/user-attachments/assets/35e42814-7367-46dc-8b67-4e50948dfb3f)

---

## **Setup Steps**  

| **Step**                      | **Action**  |  
|-------------------------------|-------------|  
| **1. Install Jenkins Master** | Deploy Jenkins on multiple machines. |  
| **2. Configure Master**       | Sync config and enable database replication. |  
| **3. Setup Load Balancer**    | Use HAProxy/Nginx or cloud load balancers. |  
| **4. Connect Agents**         | Register agents to offload builds. |  
| **5. Use Shared Storage**     | Implement NFS, EFS, or similar shared file systems. |  
| **6. Implement Backup**       | Use tools like ThinBackup for job/config backups. |  
| **7. Test Failover**          | Validate auto-failover by simulating failure. |  

---

## **Active/Passive Nodes**  

In an **Active/Passive** setup, only one master is active while the other stands by, ready to take control in case of failure.

| **Node Type**   | **Details**                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| **Active Node** | Manages builds, plugins, and handles traffic.                              |
| **Passive Node**| Stays synchronized with the active node and becomes active if a failure occurs. |

### **Active-Passive Architecture Diagram**  
![Active-Passive Diagram](https://github.com/user-attachments/assets/c5430987-ff8b-44e5-b73b-113eb1fb0d9f)

---

## **Benefits**  

| **Advantage**        | **Explanation**  |  
|----------------------|------------------|  
| **Less Downtime**    | Failover ensures minimal interruption. |  
| **Better Performance**| Agents distribute the build load. |  
| **Scalability**      | Easily scale horizontally with more nodes. |  
| **CI/CD Continuity** | Pipelines stay running even in case of failures. |  

---

## **Conclusion**

Jenkins High Availability ensures uninterrupted CI/CD workflows, boosts system resilience, and supports seamless scaling. Whether through Active/Passive setups or autoscaling, HA is essential for delivering reliable and future-ready DevOps pipelines.

---


## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## **References**  

| **Title**                          | **URL**  |  
|------------------------------------|----------|  
| Jenkins HA Setup Guide             | [Read More](https://medium.com/@priyanshigola8/setup-jenkins-ha-high-availability-with-master-slave-architecture-9b95f8b341e4) |  
| ThinBackup Plugin Guide            | [Backup & Restore Jenkins](https://medium.com/devops-technical-notes-and-manuals/jenkins-backup-and-restore-using-plugins-guide-for-junior-devops-engineers-ffd0fd41fb8e) |

---
