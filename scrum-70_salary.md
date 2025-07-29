## Documentation Of Salary Api

<img src="https://github.com/user-attachments/assets/9485facc-f520-412e-b936-d1f82e9d479d" alt="Salary API Logo" width="300"/>

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  29-07-2025        | V 1.0            |     29-07-2025    |  Prashant          |  -      |      -  |  - |

---

##  Table of Contents
- [Introduction](#introduction)
- [Why need this application?](#why-need-this-application)  
- [What problems does it resolve?](#what-problems-does-it-resolve)  
- [Pre-requisites](#pre-requisites)  
    - [System Requirements](#system-requirements)  
-  [Dependencies](#dependencies)  
    - [Build Time Dependency](#build-time-dependency)  
    - [Run Time Dependency](#run-time-dependency)  
    - [Important Ports](#important-ports)  
-  [Architecture](#architecture)  
-  [Dataflow Diagram](#dataflow-diagram)  
-  [Step-by-step installation of Application](#step-by-step-installation-of-application)  
-  [Troubleshooting](#troubleshooting)
-  [Endpoints](#endpoints) 
-  [Contact Information](#contact-information)  
-  [References](#references)  

---

## Introduction
The Salary API is a microservice built using Java. It manages all tasks related to salary processing and keeping salary records. This service is part of the OT-Microservices system. It is designed to work on any operating system as long as Java Runtime Environment (JRE) is installed, making it platform-independent. Its main job is to handle payroll operations accurately and efficiently, and it works well with other microservices in the system.



---

## Why need this application?
A separate service for salary work is important in a microservices system. It keeps salary data in one place, makes it easier to manage, and helps connect it smoothly with other services.

---
## What problems does it resolve?
- Eliminates salary data duplication across services

- Provides consistent APIs for salary operations

- Makes it easier to update and manage salary-related code

- Keeps track of any changes made to salary data

- Makes it easier to connect with other systems like attendance and leave tracking

---

## Pre-requisites

| Hardware Specifications | Minimum Recommendation |
|-------------------------|------------------------|
| Disk Space              | 20GB                  |
| OS                      | Ubuntu(22.04)         |

---

## Dependencies

### Build Time Dependency

|Name    |	Version	|Description|
|--------|----------|------------|
|Maven	 |3.8+       |	Java build automation tool|
|OpenJDK	|17+	    |Java development environment|
|Make|4.3+|It runs the default target in a Linux-unix environment|
|Jq | 1.6| To manipulate JSON file|

### Run Time Dependency

|Name    |	Version	|Description|
|--------|----------|------------|
|ScyllaDB	 |4.6+	      |	Distributed NoSQL DB|
|Redis		|6.0+    |No sql Db|

---
### Important Ports

| Important ports         | Description |
|-------------------------|------------------------|
| 8080          | Used by Spring Boot embedded server           |
| 9042          | 	ScyllaDB port          |
| 6379          | 	Redis port          |

---

### Architecture

![Screenshot 2025-05-02 123839](https://github.com/user-attachments/assets/36f728a3-601c-48ac-b4c6-1d84dcdfe32c)

---
### Dataflow Diagram

**1.User/API Client → Salary API**

A request for salary-related data is made.

**2.Salary API → Redis Cache**

The Salary API first checks Redis to find the requested data (cache lookup).

**3.Redis Cache**

If cache hit → returns the data directly to Salary API.

If cache miss → Redis queries ScyllaDB for the data.

**4.ScyllaDB → Redis Cache**

ScyllaDB send the data 

**5.Redis Cache → Salary API**

Redis returns the fresh data back to the Salary API.

**6.Salary API → User/API Client**

Salary API sends the final response.

---

## Step-by-step for Salary API

  Please follow step here  git repo

---
## Troubleshooting

| **Issue** | **Possible Cause** | **Solution** |
|----------|---------------------|----------------|
| **Can't connect to ScyllaDB** | ScyllaDB is not running or the wrong address/port is used | Make sure ScyllaDB is installed and running (`nodetool status`) <br> Check if the right address and port are set in `application.properties` |
| **Redis port is wrong** | The app is using the wrong port (default is `6379`) | Set the correct port in the app config <br> Check if Redis is listening using `ss -tuln | grep 6379` |
| **App can't connect to Redis/ScyllaDB on EC2** | EC2 firewall (Security Group) is blocking the ports | Go to EC2 Console and edit inbound rules <br> Allow ports `6379` (Redis) and `9042` (ScyllaDB) from trusted IPs |
| **Redis not storing cache** | Cache code has issues or Redis is down | Check Redis logs for errors <br> Use `redis-cli KEYS *` to see if data is there <br> Make sure caching is correctly written in code |
| **Port 8080 already in use** | Some other app is already using port 8080 | Run `lsof -i :8080` to find the process <br> Stop that process or use another port in your app config |

---

## Endpoint Information

| **Endpoint**                   | **Method** | **Description**                                                                               |
|--------------------------------|------------|-----------------------------------------------------------------------------------------------|
| `/api/v1/salary/create/record` | POST       | Data creation endpoint which accepts certain JSON body to add salary information in database  |
| `/api/v1/salary/search`        | GET        | Endpoint for searching data information using the params in the URL                           |
| `/api/v1/salary/search/all`    | GET        | Endpoint for searching all information across the system                                      |
| `/actuator/prometheus`         | GET        | Application healthcheck and performance metrics are available on this endpoint                |
| `/actuator/health`             | GET        | Endpoint for providing shallow healthcheck information about application health and readiness |



## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| Reference               | Link                                                                           |
|-------------------------|--------------------------------------------------------------------------------|
| ScyllaDB Installation documentation    | [Click here](https://docs.github.com)                             |
| Redis Installation Guide              |                             |
| Maven                   | [Click here](https://maven.apache.org/what-is-maven.html)                                           |
