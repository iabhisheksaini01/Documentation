<img width="218" height="231" alt="image" src="https://github.com/user-attachments/assets/8cf5884b-1b15-4052-89cb-5303666389b0" />

##  Proof of Concept (POC) for Code Compilation for Golang
---

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  31-07-2025        | V 1.0            |    04-08-2025   |  Sahil          |      |         |   - |


---

##  Table of Contents
- [Introduction](#introduction)  
- [Pre-Requisites](#pre-requisites)  
- [System Requirements](#system-requirements)   
- [Step-by-step Installation](#step-by-step-installation)  
- [Contact Information](#contact-information)  
- [References](#references)  

---

## Introduction

This document provides a **Proof of Concept (PoC)** for compiling and running a Go (Golang) application. It demonstrates the full workflow from setting up Go, cloning the project, compiling the source code into an executable binary, to running the application ensuring dependencies and runtime requirements are properly managed.

>**Note:**  
For this Proof of Concept (PoC) on Go code compilation, the source code from the **Employee API** project will be used. This demonstrates compiling a real Go application into an executable binary to validate the build process and ensure the service runs correctly.
 
---

##  Pre-Requisites
- **Go Installed**: Go compiler must be installed on your system (preferably Go 1.20 or later).
---

##  System Requirements

>For detailed system requirements, please refer this link:  
[Employee Documentation](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-68-Ashutosh/OT-Microservices/Applications/Employee-API/Introduction/README.md)

---
 
##  Step-by-step Installation
###  Step 1: Check the Go version
>Run the following command to verify if Go is installed on your system and to check its version:
```bash
go version
```

###  Step 2: If not installed, install Go
>If Go is not already installed, follow the installation guide provided in the documentation:  
[Go Installation Guide](https://github.com/Snaatak-Cloudops-Crew/documentation/tree/scrum-34-sonal/Softwares/Installation/Manual) 
<img width="1062" height="599" alt="Screenshot from 2025-08-15 20-04-01" src="https://github.com/user-attachments/assets/f41b44c0-c9ad-4c68-a5d8-8766ee3089f7" />

###  Step 3: Clone the Git Repository
>Use the following command to clone the Employee API project repository to your local system:
```bash
git clone https://github.com/OT-MICROSERVICES/employee-api.git
```
<img width="982" height="431" alt="Screenshot from 2025-08-15 20-06-31" src="https://github.com/user-attachments/assets/ba14a301-65bd-4e67-893c-0cd4cc5adfaa" />

### Step 4: Change Directory
>Navigate into the cloned repository folder using:
```bash
cd employee-api
```
<img width="1281" height="374" alt="Screenshot from 2025-08-15 20-09-06" src="https://github.com/user-attachments/assets/d00e2a68-2a59-4f0f-9f4c-64e45b4fa70f" />


### Step 5: Code Compilation
>Use the `go build` command to compile the Go source code in the current directory, generating an executable binary named `employee-api`.  
<img width="1077" height="906" alt="Screenshot from 2025-08-15 20-24-39" src="https://github.com/user-attachments/assets/0427b554-2d3d-43fd-bc22-5ce5421f62d4" />

### Step 6: Run the Binary
>After successful compilation, execute the binary using:
```bash
./employee-api
```
>Running this command starts the employee API service, making it ready to handle requests.


<img width="1210" height="406" alt="Screenshot from 2025-08-15 20-29-57" src="https://github.com/user-attachments/assets/e501c878-0b03-4304-b6ac-9edad0ea12fc" />
 


## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

##  References
| Description | Links|
|------|---------------------|
| Document|[Link](https://github.com/mygurukulam-p10/Documention/blob/main/Application%20CI%20Design/GoLang%20CI%20Checks/Code%20compilation%20Doc/readme.md)|
