# ScyllaDB Proof of Concept

##  **Author Information**
| Created     | Last updated | Version | Author         | Comment | Reviewer |
|-------------|-----------|---------|----------------|---------|----------|
| 26-04-2025  |           | V1     | |     Internal Review    | Pritam    |

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

![Screenshot 2025-04-26 115456](https://github.com/user-attachments/assets/fce60330-38eb-49ee-bcbe-b0f72b7494d8)






## Step-by-step installation of ScyllaDB


### Step 1: Create a repo file in your system
 ```
sudo mkdir -p /etc/apt/keyrings
```


### Step 2: Add ScyllaDB repository

```bash
sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 491c93b9de7496a7
sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-6.1.list
```
![Screenshot 2025-04-26 104516](https://github.com/user-attachments/assets/96576d15-6f32-483b-a4e4-bb6327944ef4)
![Screenshot 2025-04-26 104559](https://github.com/user-attachments/assets/b57ec51a-6b76-4d30-ab4a-b96093e50ab3)


### Step 3: Update package cache

> 👉 **Follow Step-3**: [update_command](https://github.com/snaatak-Downtime-Crew/Documentation/blob/main/common_stack/operating_system/ubuntu/sop/commoncommands/README.md)


### Step 4:  Install java 11 & update

> 👉 **Follow Documentation**: [Java Installation](https://github.com/snaatak-Downtime-Crew/Documentation/blob/main/common_stack/application/java/installation/guide/README.md   )

### Step 5: Install ScyllaDB

```bash
sudo apt-get install scylla
```
![Screenshot 2025-04-26 104709](https://github.com/user-attachments/assets/e248fbb9-d75c-4567-a779-f1687f57c694)




### Step 6: Start ScyllaDB service and check its status

Start the ScyllaDB service:

```bash
sudo systemctl start scylla-server

```
Check the status of the ScyllaDB service

```bash
sudo systemctl status scylla-server

```
![Screenshot 2025-04-26 105102](https://github.com/user-attachments/assets/f303c468-c195-4a79-b2dd-4c6e9ed47f82)






### Step 7: Verify ScyllaDB Installation

```
 Use nodetool to check the status of your ScyllaDB nodes
```
```bash
nodetool status
```
### Step 8. Configure user Scylla 
```
sudo vi /etc/scylla/scylla.yaml
```
After entering, Edit these entries for security purpose
```
authenticator: PasswordAuthenticator
authorizer: CassandraAuthorizer
```
### Authentication and Authorization in ScyllaDB

#### `authenticator: PasswordAuthenticator`
- **Purpose**: Specifies the method used for authentication in ScyllaDB.
- **Description**: The `PasswordAuthenticator` setting means that users must provide a username and password to authenticate. It uses a password-based authentication method, where credentials are checked against the stored user data.

#### `authorizer: CassandraAuthorizer`
- **Purpose**: Defines the authorization method used in ScyllaDB.
- **Description**: The `CassandraAuthorizer` setting allows you to control access to database resources using roles and permissions. It is similar to how Apache Cassandra manages authorization and helps in defining who can access what data and perform what operations.



![Screenshot 2025-04-26 105617](https://github.com/user-attachments/assets/e4095ec5-c1cd-4318-8d30-dfaa7a4ac4ef)




## Basic Operations

Here are some basic CQL commands to get started with ScyllaDB:

1. Connect to ScyllaDB using cqlsh:
   ```bash
   cqlsh -u cassandra -p cassandra
   ```
![Screenshot 2025-04-26 110607](https://github.com/user-attachments/assets/4e1ca646-dd14-492d-8a31-d19a55df11d9)


2. Create a keyspace:
   ```sql
   CREATE KEYSPACE mykeyspace WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};
   ```
### `CREATE KEYSPACE` Command

The `CREATE KEYSPACE` command is used to define a new keyspace in ScyllaDB. A keyspace in ScyllaDB (and Cassandra) is a container for tables, and it defines how data is replicated across nodes in the cluster.

3. Use the keyspace:
   ```sql
   USE mykeyspace;
   ```

4. Create a table:
   ```sql
   CREATE TABLE users (
     user_id UUID PRIMARY KEY,
     username TEXT,
     email TEXT
   );
   ```

5. Insert 
   ```sql
   INSERT INTO users (user_id, username, email) 
   VALUES (uuid(), 'adil', 'adil@example.com');
   ```

6. Query 
   ```sql
   SELECT * FROM users;
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


## References

| Links                                                | Descriptions                             |
|------------------------------------------------------|------------------------------------------|
| [ScyllaDB Documentation](https://docs.scylladb.com/) | Official ScyllaDB documentation          |
| [ScyllaDB Installation Guide](https://docs.scylladb.com/stable/operating-scylla/procedures/install/install-ubuntu.html) | Official installation guide for Ubuntu |
| [ScyllaDB University](https://university.scylladb.com/) | Free online courses on ScyllaDB       |
