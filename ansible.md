# Ansible Role to setup Scylla-DB

<img width="281" height="180" alt="download" src="https://github.com/user-attachments/assets/1055b208-9e8d-44d9-a7ff-c80a2ba8378c" />



## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  11-08-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |


---


# Table of Contents

- [Overview](#overview)  
- [Role Purpose](#role-purpose)  
- [Directory Structure](#directory-structure)  
- [Role Variables](#role-variables)  
- [Tasks Description](#tasks-description)  
- [Handlers](#handlers)  
- [Templates & Files](#templates--files)  
- [Meta Information](#meta-information)  
- [Example Playbook](#example-playbook)  
- [Flow Diagram](#flow-diagram)  
- [Testing](#testing)  

---

## Introduction 

The **ScyllaDB Ansible Role** is designed to automate the deployment, configuration, and management of ScyllaDB clusters across Linux servers.  
It ensures idempotency and can be reused across multiple environments. 

---


## Role Purpose
This role handles:

- Installing the specified ScyllaDB version  
- Configuring ScyllaDB settings (`scylla.yaml`)  
- Managing the ScyllaDB service lifecycle (start, stop, restart)  
- Verifying that ScyllaDB service is running  

---


## Directory Structure

> <img width="734" height="479" alt="Screenshot from 2025-09-03 01-41-13" src="https://github.com/user-attachments/assets/0aab2d16-6ac8-407b-8d47-7682576fde33" />

---

## File/Folder Overview
- **defaults/main.yml:** Contains default variables for the role.  
- **vars/main.yml:** Holds environment- or host-specific variables.  
- **tasks/main.yml:** Core tasks for installation, configuration, and validation.  
- **handlers/main.yml:** Defines actions like service restart triggered by tasks.  
- **templates/:** Jinja2 templates for dynamic configurations.  
- **files/:** Static files to be copied to target hosts.  
- **meta/main.yml:** Role metadata, including dependencies.  
- **tests/:** Sample playbooks and inventories for testing the role.

---



# Conclusion

This guide demonstrates how to automate the setup of ScyllaDB in a development environment using Ansible. By following these steps, you can efficiently provision and configure ScyllaDB on your AWS infrastructure.

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

# Resources and References 

| Description | Source |
| ---- | -------------- |
|  Setting up Ansible AWS Dynamic Inventory | **[Link](https://devopscube.com/setup-ansible-aws-dynamic-inventory/)** |
|  ScyllaDB-Manual Setup | **[Link](https://github.com/avengers-p7/Documentation/tree/main/OT%20Micro%20Services/Software/ScyllaDB)** |
| [ScyllaDB Installation Guide](https://opensource.docs.scylladb.com/stable/getting-started/install-scylla/install-on-linux.html) | Comprehensive guide for installing ScyllaDB on Linux. |
| [ScyllaDB Configuration Guide](https://www.scylladb.com/download/?platform=ubuntu-22.04&version=scylla-5.2#open-source) | Step-by-step instructions for configuring ScyllaDB. |
| [Documentation Template](https://github.com/OT-MICROSERVICES/documentation-template/wiki/Software-Template) | Format inspiration for the document obtained from this repository. |
