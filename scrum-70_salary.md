## Documentation of Salary Api
---

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  29-07-2025        | V 1.0            |     29-07-2025    |  Prashant          |  -      |      -  |  - |

---

##  Table of Contents

1. [Introduction](#introduction)  
2. [Why need this application?](#why-need-this-application)  
3. [What problems does it resolve?](#what-problems-does-it-resolve)  
4. [Pre-requisites](#pre-requisites)  
    - [System Requirements](#system-requirements)  
5. [Dependencies](#dependencies)  
    - [Build Time Dependency](#build-time-dependency)  
    - [Run Time Dependency](#run-time-dependency)  
    - [Important Ports](#important-ports)  
6. [Architecture](#architecture)  
7. [Dataflow Diagram](#dataflow-diagram)  
8. [Step-by-step installation of Application](#step-by-step-installation-of-application)  
    - [Step 1: Installation of software Dependencies](#step1-installation-of-software-dependencies)  
    - [Step 2: Build/Artifact Generation](#step2-buildartifact-generation)  
    - [Step 3: Application Deployment](#step3-application-deployment)  
9. [Troubleshooting](#troubleshooting)
10. [Endpoints](#endpoints) 
11. [Contact Information](#contact-information)  
12. [References](#references)  

---

## Introduction
Salary API is a microservice developed in Java that handles all operations related to salary processing and record-keeping within the OT-Microservices architecture. Designed with portability in mind, this service is platform-agnostic and can operate seamlessly across different operating systems, provided a Java Runtime Environment (JRE) is available. Its core responsibility is to ensure accurate and efficient handling of payroll transactions while integrating smoothly into the broader microservice ecosystem.

---

## Why need this application?
A dedicated service for salary-related operations is crucial in a distributed microservices architecture. Centralizing this logic in a single microservice promotes modularity, simplifies payroll integration, and ensures a single source of truth for all salary data and transactions.

---
## What problems does it resolve?
--> Eliminates salary data duplication across services

--> Provides consistent APIs for salary operations

--> Enhances maintainability of payroll logic

-->Enables audit trails for salary changes

-->Simplifies integration with downstream services like attendance and leave management



---

## Prerequisites

| Hardware Specifications | Minimum Recommendation |
|-------------------------|------------------------|
| Disk                     | 20GB                  |
| OS                       | Ubuntu(22.04)         |

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


## Step-by-step for Salary API

  Please follow step here  


---
## Troubleshooting
| **Issue** | **Possible Cause** | **Solution** |
|----------|---------------------|----------------|
|  ScyllaDB Connection Failed | ScyllaDB service is not running or incorrectly configured (host/port) |  Ensure ScyllaDB is installed and running using `nodetool status`<br> Verify correct host and port are set in `application.properties` |
| Redis Port Misconfigured | Wrong port configured in the application settings (default is `6379`) |  Update to the correct port in application config<br>  Check Redis is listening using `ss -tuln | grep 6379` |
|  Application Cannot Connect to Redis/ScyllaDB on EC2 | EC2 Security Group (SG) doesn’t allow required ports |  In EC2 Console, edit SG inbound rules<br>  Add ports `6379` for Redis and `9042` for ScyllaDB from trusted sources |
|  Redis Not Caching Data | Cache logic is broken or Redis is unreachable |  Check Redis connection logs<br> Verify keys using `redis-cli KEYS *`<br>  Ensure cache logic is implemented correctly |
|  Port 8080 Already in Use | Another process is using port 8080 |  Check using `lsof -i :8080`<br> Kill the process or change the port in the app config |


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
