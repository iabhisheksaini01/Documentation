
# ScyllaDB Proof of Concept

![scy](https://github.com/user-attachments/assets/061ec917-3bf8-4038-a70c-5ef6963fc00f)

---
## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  16-07-2025        | V 1.0            |     18-07-2025    |  Prashant          |  -      |     -   |   - |

---
## Table of Contents

1. [Purpose](#purpose)
2. [Pre-requisites](#pre-requisites)
   - [System Requirements](#system-requirements)
   - [Dependencies](#dependencies)
   - [Important Ports](#important-ports)
3. [Architecture](#architecture)
4. [Step-by-step installation of ScyllaDB](#step-by-step-installation-of-scylladb)
5. [Basic Operations](#basic-operations)
6. [Troubleshooting](#troubleshooting)
7. [Contact Information](#contact-information)
8. [References](#references)
    

## Purpose

 This POC will showcase standalone ScyllaDB's installation process, basic operations.

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


## Architecture

ScyllaDB follows a distributed architecture where data is automatically replicated across multiple nodes for fault tolerance and high availability.

<img width="475" alt="image" src="https://github.com/user-attachments/assets/6447e269-e85d-4adc-8cdf-882984095090" />


###  **Left Circle – Token Ring (Consistent Hashing)**

* This is a **token ring** representation.
* Numbers **1 to 12** represent **partitions of data** (or **token ranges**).
* ScyllaDB (like Cassandra) uses **consistent hashing** to divide data into **token ranges**.
* Each token is **replicated** across multiple nodes for **fault tolerance**.


###  **Right – Node and Rack Assignment**

* The cluster has **3 nodes** (X, Y, Z), each in a different **rack or availability zone**:

  * **Node X** → Rack 1 / Zone A
  * **Node Y** → Rack 2 / Zone B
  * **Node Z** → Rack 3 / Zone C
* Each node is responsible for **specific tokens**, and **each token is stored on 3 different nodes** for replication.
* We are using **replication factor = 3**, with replicas placed in **different zones** to ensure **high availability**.

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

Start the ScyllaDB service:

```bash
sudo systemctl start scylla-server
```
Check the status of the ScyllaDB service

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
After entering, Edit these entries for security purpose
```bash
authenticator: PasswordAuthenticator
authorizer: CassandraAuthorizer
```
---

### Authentication and Authorization in ScyllaDB

#### `authenticator: PasswordAuthenticator`
- **Purpose**: Specifies the method used for authentication in ScyllaDB.
- **Description**: The `PasswordAuthenticator` setting means that users must provide a username and password to authenticate. It uses a password-based authentication method, where credentials are checked against the stored user data.

#### `authorizer: CassandraAuthorizer`
- **Purpose**: Defines the authorization method used in ScyllaDB.
- **Description**: The `CassandraAuthorizer` setting allows you to control access to database resources using roles and permissions. It is similar to how Apache Cassandra manages authorization and helps in defining who can access what data and perform what operations.

---

<img width="1851" height="496" alt="Screenshot from 2025-07-29 01-38-13" src="https://github.com/user-attachments/assets/54476820-d3e5-44cc-b648-edf09ee78696" />

---

## Basic Operations

Here are some basic CQL commands to get started with ScyllaDB:

1. Connect to ScyllaDB using cqlsh:
   ```bash
   cqlsh <private-ip> -u cassandra -p cassandra
   ```
![Screenshot 2025-04-26 110607](https://github.com/user-attachments/assets/4e1ca646-dd14-492d-8a31-d19a55df11d9)

2. Create USER
   ```
   CREATE USER scylladb WITH PASSWORD 'password' SUPERUSER;
   ```

3. Create a DB(employee_db):
   ```sql
   CREATE KEYSPACE employee_db WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};
   ```
4. USE employee_db;

5. Query:
   ```sql
   SELECT * FROM employee_salary; 
   ```

9. Describe keyspace:
   ```sql
   Describe KEYSPACES;
   ```



## Troubleshooting

- If ScyllaDB service fails to start, check the logs:
  ```bash
  sudo journalctl -u scylla-server
  ```

- For performance issues, use the `nodetool` utility to check cluster status and performance metrics:
  ```bash
  nodetool status
  ```

- If you encounter connection issues, ensure that the ScyllaDB service is running:
  ```bash
  sudo systemctl status scylla-server
  ```

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| Links                                                | Descriptions                             |
|------------------------------------------------------|------------------------------------------|
| [ScyllaDB Documentation](https://docs.scylladb.com/) | Official ScyllaDB documentation          |
| [ScyllaDB Installation Guide](https://docs.scylladb.com/stable/operating-scylla/procedures/install/install-ubuntu.html) | Official installation guide for Ubuntu |
| [ScyllaDB University](https://university.scylladb.com/) | Free online courses on ScyllaDB       |

| [Scylla Setup](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-88-Adil/common_stack/software/scylladb/configuration/README.md) | Scylla Configuration Setup |
