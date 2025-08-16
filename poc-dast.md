# DAST Using OWASP ZAP

---

<p align="center">
  <img src="https://github.com/user-attachments/assets/eff63252-035b-4517-bda6-cca9578d4366" width="800" height="450" alt="resize" />
</p>


---

## Author Information

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  12-08-2025        | V 1.0            |    |  Prashant          |  -      |      -  |  - |

---

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Step-by-Step Installation Guide](#step-by-step-installation-guide)

   * [Step 1: Update Your OS](#step-1-update-your-os)
   * [Step 2: Install OWASP ZAP](#step-2-install-owasp-zap)
   * [Step 3: Launch OWASP ZAP](#step-3-launch-owasp-zap)
   * [Step 4: Enter the API URL](#step-4-enter-the-api-url)
   * [Step 5: Wait for Results](#step-5-wait-for-results)
   * [Step 6: View Results](#step-6-view-results)
   * [Step 7: Generate Report](#step-7-generate-report)
4. [Conclusion](#conclusion)
5. [Contact Information](#contact-information)
6. [References](#references)

## Introduction

This guide provides a concise walkthrough for setting up and using OWASP ZAP for identifying vulnerabilities in web applications and APIs. It covers installation, usage, and reporting to help you secure your applications effectively.

## Prerequisites

## Requirements

| Requirement            | Description                                  |
|-------------------------|----------------------------------------------|
| **Java**               | Minimum version: Java 17                    |
| **Running Application or API** | Target application or API must be active |


---

## Step-by-Step Installation Guide

### Step 1: Update Your OS

> Before installing OWASP ZAP, ensure your system is up-to-date:
>Follow the [STEP 3](https://github.com/snaatak-Downtime-Crew/Documentation/blob/main/common_stack/operating_system/ubuntu/sop/commoncommands/README.md) here.

---

### Step 2: Install OWASP ZAP

Install OWASP ZAP using Snap:

```bash
sudo snap install zaproxy --classic
```

![image](https://github.com/duggu7055/Snaatak/blob/main/imgs/z4.PNG?raw=true)

---

### Step 3: Launch OWASP ZAP

Launch the application using the following command:

```bash
zaproxy
```

Ensure that your application or API is running before starting the scan.
![image](https://github.com/duggu7055/Snaatak/blob/main/imgs/z5.PNG?raw=true)

---

### Step 4: Enter the API URL

Enter the URL of the API you want to scan into the 'Attack' input field:
![image](https://github.com/duggu7055/Snaatak/blob/main/imgs/z1.PNG?raw=true)

---

### Step 5: Wait for Results

Allow the scan to complete. The time taken will depend on the complexity of the target application or API.
![image](https://github.com/duggu7055/Snaatak/blob/main/imgs/z3.PNG?raw=true)

---

### Step 6: View Results

Review the detailed findings provided by OWASP ZAP:
![image](https://github.com/user-attachments/assets/3fac393c-5c80-4bfb-af4e-58c12c0d3096)

---



## Conclusion

OWASP ZAP provides a powerful, user-friendly tool for dynamic application security testing (DAST). By following this guide, you can effectively identify vulnerabilities in your application or API and enhance its security posture.

---

## **Contact Information**
| **Name**           | **Email Address**                              |
|---------------------|-----------------------------------------------|
| Durgesh Sharma      | durgesh.sharma.snaatak@mygurukulam.co         |

---



## References

| Topic                       | Link                                                                                 |
|-----------------------------|--------------------------------------------------------------------------------------|
| **OWASP ZAP Documentation** | [OWASP ZAP Official Documentation](https://www.zaproxy.org/docs/)                   |
| **Java ci  tools**      | [Documentation]([https://snapcraft.io/docs](https://github.com/duggu7055/Snaatak/blob/main/Sprint2/Java-ci/doc/Readme.md))                                     |

