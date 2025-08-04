
# ScyllaDB POC

<div align="left">
  <img src="https://github.com/user-attachments/assets/061ec917-3bf8-4038-a70c-5ef6963fc00f" alt="scy" width="450" height="800" />
</div>


---
## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek Saini  |  28-07-2025        | V 1.0            | 28-07-2025       |  Prashant        |  Priyanka     |     -   |   - |
| Abhishek Saini  |  28-07-2025        | V 1.1            |  04-08-2025       |  Prashant          | Priyanka    |     -   |   - |
---
## Table of Contents

 - [Objective](#objective)
 - [Pre-requisites](#pre-requisites)
   - [System Requirements](#system-requirements)
   - [Dependencies](#dependencies)
   - [Important Ports](#important-ports)
- [Step-by-step installation of ScyllaDB](#step-by-step-installation-of-scylladb)
-  [Basic Operations](#basic-operations)
-  [Troubleshooting](#troubleshooting)
- [Contact Information](#contact-information)
- [References](#references)

---

## Objective

The purpose of this Proof of Concept (POC) is to demonstrate the standalone installation, configuration, and basic usage of ScyllaDB on an Ubuntu system. It aims to help users understand the key architectural concepts, setup process, authentication mechanisms, and basic CQL operations involved in working with ScyllaDB. This document serves as a practical reference for deploying a single-node ScyllaDB instance for testing, learning, or development use cases.

---

## Pre-requisites

### System Requirements

| Hardware Specifications | Minimum Recommendation |
|-------------------------|------------------------|
| Processor               | 2 cores                |
| RAM                     | 4GB                    |
| Disk                    | 15GB SSD               |
| OS                      | Ubuntu 22.04 LTS       |

### Dependencies

#### Run time Dependency

| Name    | Version | Description                                    |
|---------|---------|------------------------------------------------|
| Java    | 11      | For running ScyllaDB driver and sample scripts |

### Important Ports

| Inbound Traffic | Description                    |
|-----------------|--------------------------------|
| 9042            | CQL native transport port      |

---
### Before proceeding, it is strongly recommended that you review the ScyllaDB documentation.

**Please follow the steps outlined here:**  
[ScyllaDB Documentation](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-78-deepak/OT-Microservices/Softwares/Scylladb/Introduction/README.md)

---

## Architecture

ScyllaDB follows a distributed architecture where data is automatically replicated across multiple nodes for fault tolerance and high availability.

<img width="1203" height="475" alt="Screenshot from 2025-07-29 13-17-25" src="https://github.com/user-attachments/assets/d8189815-b468-42aa-871a-5f5be65c1a71" />



### Left Side – Token Ring (Consistent Hashing)

* This diagram shows the **token ring** structure.
* Numbers **1 to 12** represent **data token ranges** (or partitions).
* ScyllaDB, like Cassandra, uses **consistent hashing** to evenly distribute data across nodes.
* Each token's data is **replicated on multiple nodes** to ensure **fault tolerance** and reliability.


### Right Side – Node, Rack, and Token Mapping

* The cluster consists of **3 nodes**, each located in a different **rack or availability zone**:
  - **Node X** → Rack 1 / Zone A  
  - **Node Y** → Rack 2 / Zone B  
  - **Node Z** → Rack 3 / Zone C  

* Each node is responsible for handling **specific tokens**.
* Each token is stored on **2 nodes** – one as the **primary copy**, and one as the **replica**.
* The setup uses a **replication factor (RF) of 2**, with replicas placed across **different zones** to provide **high availability** and fault isolation.

---

## Step-by-step installation of ScyllaDB

### Step 1: Create a repo file in your system
```bash
sudo mkdir -p /etc/apt/keyrings
```
### Step 2: Add ScyllaDB repository

```bash
sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 491c93b9de7496a7
sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-6.1.list
```
<img width="1859" height="624" alt="Screenshot from 2025-07-29 00-46-01" src="https://github.com/user-attachments/assets/2770a450-7f52-4c11-aa09-a4c6d8521767" />


### Step 3: Update package cache
```bash
sudo apt update
```
### Step 4:  Install java 11 
```bash
sudo apt install openjdk-11-jdk -y
```
### Step 5: Install ScyllaDB
```bash
sudo apt-get install scylla
```
<img width="1859" height="624" alt="Screenshot from 2025-07-29 00-48-11" src="https://github.com/user-attachments/assets/27ccb010-3aa4-45f3-952c-ad0ffac30bb9" />


### step 6: Configuring ScyllaDB I/O Scheduler
```bash
sudo scylla_io_setup
```
<img width="1848" height="400" alt="Screenshot from 2025-07-29 00-54-43" src="https://github.com/user-attachments/assets/1c1f32b8-8a8c-4caf-9764-8156484edcad" />


### Step 7: Start ScyllaDB service and check its status

##### Start the ScyllaDB service:

```bash
sudo systemctl start scylla-server
```
##### Check the status of the ScyllaDB service

```bash
sudo systemctl status scylla-server
```
<img width="1851" height="494" alt="Screenshot from 2025-07-29 00-55-06" src="https://github.com/user-attachments/assets/b830c3a5-4d2e-446c-9317-4aa8551aec07" />


### Step 8: Verify ScyllaDB Installation

```
 Use nodetool to check the status of your ScyllaDB nodes
```
```bash
nodetool status
```
<img width="1851" height="287" alt="Screenshot from 2025-07-29 01-32-28" src="https://github.com/user-attachments/assets/25d6a57c-0e1b-4b16-87ad-5de35afd5940" />


### Step 9. Configure user Scylla 
```bash
sudo nano /etc/scylla/scylla.yaml
```
##### After entering, Edit these entries for security purpose
```bash
authenticator: PasswordAuthenticator
authorizer: CassandraAuthorizer
```
---

## Authentication and Authorization in ScyllaDB

#### `authenticator: PasswordAuthenticator`
- **Purpose**: Specifies the method used for authentication in ScyllaDB.
- **Description**: The `PasswordAuthenticator` setting means that users must provide a username and password to authenticate. It uses a password-based authentication method, where credentials are checked against the stored user data.

#### `authorizer: CassandraAuthorizer`
- **Purpose**: Defines the authorization method used in ScyllaDB.
- **Description**: The `CassandraAuthorizer` setting allows you to control access to database resources using roles and permissions. It is similar to how Apache Cassandra manages authorization and helps in defining who can access what data and perform what operations.

<img width="1851" height="496" alt="Screenshot from 2025-07-29 01-38-13" src="https://github.com/user-attachments/assets/54476820-d3e5-44cc-b648-edf09ee78696" />

---

## Basic Operations

| Step | Description                              | Command(s)                                                                                              |
|------|------------------------------------------|----------------------------------------------------------------------------------------------------------|
| 1    | Connect to ScyllaDB using `cqlsh`         | `cqlsh <private-ip> -u scylladb -p password`                                                             |
| 2    | Create a Keyspace `employee_db`           | `CREATE KEYSPACE employee_db WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};`   |
| 3    | Use the Keyspace                          | `USE employee_db;`                                                                                       |
| 4    | Create a Table `employee_salary`          | `CREATE TABLE employee_salary ( emp_id UUID PRIMARY KEY, name TEXT, salary INT );`                       |
| 5    | Insert an Entry                           | `INSERT INTO employee_salary (emp_id, name, salary) VALUES (uuid(), 'Abhishek', 50000);`                 |
| 6    | Verify the Entry                          | `SELECT * FROM employee_salary;`                                                                         |


<img width="1848" height="494" alt="Screenshot from 2025-07-29 11-02-31" src="https://github.com/user-attachments/assets/a789a186-80f5-4aca-8992-51154277b69a" />

---

## Troubleshooting

| Issue                   | Solution                                                                                  | Command(s)                                                                 |
|-------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| ScyllaDB Not Starting   | Check the service logs for details                                                        | `sudo journalctl -u scylla-server`                                         |
| Performance Issues      | Use the `nodetool` utility to check cluster status and performance metrics                | `nodetool status`                                                         |
| Can't Connect?          | Make sure the ScyllaDB service is running                                                 | `sudo systemctl status scylla-server`                                      |

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek Saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| Links                                                | Descriptions                             |
|------------------------------------------------------|------------------------------------------|
| [ScyllaDB Documentation](https://docs.scylladb.com/) | Official ScyllaDB documentation          |
| [ScyllaDB Installation Guide](https://docs.scylladb.com/stable/operating-scylla/procedures/install/install-ubuntu.html) | Official installation guide for Ubuntu |
| [ScyllaDB University](https://university.scylladb.com/) | Free online courses on ScyllaDB       |
