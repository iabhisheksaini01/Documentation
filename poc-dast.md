# DAST Using OWASP ZAP

![1651183851472](https://github.com/user-attachments/assets/67632032-2160-4dea-bce6-70816c5ad9e6)

---

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  12-08-2025        | V 1.0            |    |  Prashant          |  -      |      -  |  - |

---
## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [OWASP ZAP: Step-by-Step Installation and API Testing Guide](#owasp-zap-step-by-step-installation-and-api-testing-guide)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)


## Introduction

This guide provides a concise walkthrough for setting up and using OWASP ZAP for identifying vulnerabilities in web applications and APIs. It covers installation, usage, and reporting to help you secure your applications effectively.

---
## Prerequisites

| Requirement            | Description                                  |
|-------------------------|----------------------------------------------|
| **Java**               | Minimum version: Java 17                    |
| **Running Application or API** | Target application or API must be active |


---

## OWASP ZAP: Step-by-Step Installation and API Testing Guide


### Step 1: Update Your OS
> Before installing OWASP ZAP, ensure your system is up-to-date. Updating your OS ensures that all dependencies and libraries required by ZAP are current, minimizing compatibility issues.

##### Run the following command on Ubuntu:
```bash
sudo apt update && sudo apt upgrade -y
```
### Step 2: Install OWASP ZAP
> After updating your OS, install OWASP ZAP, a web security testing tool, using Snap.

##### Run the following command on Ubuntu:
```bash
sudo snap install zaproxy --classic
```
<img width="679" height="328" alt="Screenshot from 2025-08-17 20-50-20" src="https://github.com/user-attachments/assets/6ca3af0a-bc58-48b3-8a0d-1bfa5e837dc8" />


---
### Step 3: Launch OWASP ZAP
> Start OWASP ZAP to begin testing your web application or API.

##### Run the following command on Ubuntu:
```bash
zaproxy
```
<img width="1050" height="535" alt="Screenshot from 2025-08-17 20-52-30" src="https://github.com/user-attachments/assets/5fcd758e-fbfe-45be-a249-11dc4b8802c4" />

---

### Step 4: Enter the API URL
> Input the URL of the API or web application you want to test in the 'Attack' field of OWASP ZAP.  
> This tells ZAP which target to scan for vulnerabilities.


### Step 5: Wait for Results
> Allow the scan to complete.  
> The time taken will depend on the complexity of the target application or API.

![image](https://github.com/duggu7055/Snaatak/blob/main/imgs/z3.PNG?raw=true)


### Step 6: View Results

Review the detailed findings provided by OWASP ZAP:
![image](https://github.com/user-attachments/assets/3fac393c-5c80-4bfb-af4e-58c12c0d3096)


---

## Conclusion

OWASP ZAP is an easy-to-use tool that helps find security issues in your application or API and improve its overall safety.

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| Topic                       | Link                                                                                 |
|-----------------------------|--------------------------------------------------------------------------------------|
| **OWASP ZAP Documentation** | [OWASP ZAP Official Documentation](https://www.zaproxy.org/docs/)                   |                               |

