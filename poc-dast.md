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
<img width="1141" height="691" alt="Screenshot from 2025-08-17 22-19-49" src="https://github.com/user-attachments/assets/6ee88a71-fbb9-44ca-af56-b48fa09b0d0c" />


### Step 5: Wait for Results
> Allow the scan to complete.  
> The time taken will depend on the complexity of the target application or API.

<img width="1383" height="305" alt="Screenshot from 2025-08-18 00-27-39" src="https://github.com/user-attachments/assets/b8a8e1f9-9fcb-4e54-afdf-91a7c9365b23" />


### Step 6: Generate Report
> After the scan, go to **Report → Generate HTML Report**, choose a filename (e.g., `~/2025-08-18-ZAP-Report/zap_report.html`), click **Save**, and open it in a browser to view results.
<img width="1414" height="794" alt="Screenshot from 2025-08-18 00-32-56" src="https://github.com/user-attachments/assets/b43f3119-7f0e-43d8-9ef2-60e7ce3699fd" />
<img width="1246" height="1048" alt="Screenshot from 2025-08-18 00-22-43" src="https://github.com/user-attachments/assets/338bac6e-3c7e-4ee0-bc7c-6e58e15eb7d2" />

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

