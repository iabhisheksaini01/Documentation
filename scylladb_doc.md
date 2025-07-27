
# ScyllaDB Proof of Concept

<p align="center">
<img width="654" alt="image" src="https://github.com/user-attachments/assets/b0c4bcb6-39a5-4095-8e29-afb3ac50ffb5" />
</p>

##  **Author Information**
| Created     | Version | Author        | Last Updated       | Comment          | Reviewer         |
|-------------|---------|---------------|--------------------|------------------|------------------|
| 26-04-2025  | v1      | Adil Nawaz    | 28-04-2025        | Internal Reviewer| Pritam        |
| 26-05-2025  | v2.1   | Adil Nawaz    |  05-05-2025       | L0 Reviewer      | Shreya           |
| 26-05-2025  | v3    | Adil Nawaz    |  05-05-2025        | L1 Reviewer      | Abhiskek V         |
| 26-05-2025  | v4    | Adil Nawaz    |  05-05-2025        | L2 Reviewer      | Abhiskek D         |

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

> Before proceeding, it's **highly recommended** to follow the installation instructions from the documentation.  
> 👉 **Follow Steps here**: [ScyllaDb Installation Steps](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-88-Adil/common_stack/software/scylladb/installation/README.md)


> Before proceeding, it's highly recommended that you follow the configuration setup for setting up ScyllaDB.  
> 👉 **Follow Steps here**: [ScyllaDb Setup ](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-88-Adil/common_stack/software/scylladb/configuration/README.md)











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


| Name         | Email Address                                 |
|--------------|-----------------------------------------------|
| Adil Nawaz | adil.nawaz.snaatak@mygurukulam.co           |

## References

| Links                                                | Descriptions                             |
|------------------------------------------------------|------------------------------------------|
| [ScyllaDB Documentation](https://docs.scylladb.com/) | Official ScyllaDB documentation          |
| [ScyllaDB Installation Guide](https://docs.scylladb.com/stable/operating-scylla/procedures/install/install-ubuntu.html) | Official installation guide for Ubuntu |
| [ScyllaDB University](https://university.scylladb.com/) | Free online courses on ScyllaDB       |
| [ScyllaDB Installation](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-88-Adil/common_stack/software/scylladb/installation/README.md) | ScyllaDB Installation |
| [Scylla Setup](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-88-Adil/common_stack/software/scylladb/configuration/README.md) | Scylla Configuration Setup |
