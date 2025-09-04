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

The **ScyllaDB Ansible Role** automates the installation and configuration of ScyllaDB nodes and clusters.  
It handles package setup, configuration files, cluster bootstrapping, and service management, ensuring consistent and repeatable deployments across environments

---

## Purpose

The purpose of this document is to provide a clear reference for deploying and managing ScyllaDB using Ansible.  
It explains the role structure, variables, tasks, and usage examples, enabling teams to achieve consistent, automated, and error-free ScyllaDB setups across different environments.



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

## File/Folder Structure Description

This role follows the standard Ansible role layout, with each component dedicated to a specific aspect of ScyllaDB deployment and configuration.

### **defaults/main.yml**
- Provides default configuration parameters for ScyllaDB.  
- These values apply to all environments unless explicitly overridden.  
- Typical defaults:
  - `scylla_version: 6.0`  
  - `scylla_service: scylla-server`  
  - `scylla_data_dir: /var/lib/scylla`  

---

### **vars/main.yml**
- Stores environment-specific or cluster-level variables.  
- Higher precedence than `defaults/`.  
- Example variables:
  - `scylla_cluster_name: production-cluster`  
  - `seed_nodes: ["10.0.0.1", "10.0.0.2"]`  
  - `listen_address: "{{ ansible_host }}"`  
  - `rpc_address: 0.0.0.0`  

---

### **tasks/main.yml**
- Defines the main workflow for ScyllaDB installation and configuration.  
- Key responsibilities:
  1. Configure ScyllaDB package repositories.  
  2. Install `scylla` and `scylla-tools`.  
  3. Generate `/etc/scylla/scylla.yaml` from templates.  
  4. Apply tuning via `scylla_setup`.  
  5. Enable and start the `scylla-server` service.  
  6. Validate cluster membership with `nodetool status`.  

---

### **handlers/main.yml**
- Contains handlers that are triggered by task notifications.  
- Used primarily for:
  - Restarting `scylla-server` when configuration changes.  
  - Reloading systemd if unit definitions are updated.  

---

### **templates/**  
- Holds Jinja2 templates for dynamic configuration files.  
- Typical templates:
  - `scylla.yaml.j2` → core ScyllaDB configuration (cluster, seeds, addresses).  
  - `scylla-env.sh.j2` → environment and JVM tuning settings.  
  - `scylla-server.service.j2` → optional systemd unit customization.  

---

### **files/**  
- Stores static files required by the role.  
- Examples:
  - Repository GPG keys.  
  - Pre-defined `cassandra-rackdc.properties` for rack/DC awareness.  
  - Helper scripts used during deployment.  

---

### **meta/main.yml**
- Provides metadata about the role.  
- Declares:
  - Supported platforms (Ubuntu 20.04+, CentOS 7/8).  
  - Minimum Ansible version required.  
  - Dependencies on other roles, if any.  

---

### **tests/**  
- Contains test cases to validate the role.  
- Typically includes:
  - `test.yml` → sample playbook for installing ScyllaDB with defaults.  
  - `inventory` → example host inventory for Scylla nodes.  


---

## Conclusion

This Ansible role simplifies the deployment and management of ScyllaDB by automating installation, configuration, and cluster setup.  
By using this role, teams can ensure reliable, consistent, and repeatable ScyllaDB environments across development, staging, and production.


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
|  ScyllaDB-Manual Setup | **[Link](https://docs.scylladb.com/manual/master/getting-started/install-scylla/index.html)** |
| [ScyllaDB Installation Guide]**[Link](https://docs.scylladb.com/manual/master/using-scylla/integrations/integration-ansible.html)**|


