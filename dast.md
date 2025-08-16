## Documentation and POC of DAST (Dynamic Application Security Testing) in Java CI Checks

![image](https://github.com/user-attachments/assets/4aa0c132-1fbb-45bc-ad5f-2a631586676a)

---
  
## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  12-08-2025        | V 1.0            |    |  Prashant          |  -      |      -  |  - |

---

## **Table of Contents**

- [Introduction](#introduction)  
- [What is DAST?](#what-is-dast)  
- [Why DAST?](#why-dast)  
- [Workflow of DAST](#workflow-of-dast)  
- [Different Tools Used in DAST](#different-tools-used-in-dast)  
- [Tool Comparison](#tool-comparison)  
- [Advantages of DAST](#advantages-of-dast)  
- [POC: DAST Using OWASP ZAP](#poc-dast-using-owasp-zap)  
- [Best Practices](#best-practices)  
- [Recommendation and Conclusion](#recommendation-and-conclusion)  
- [Contact Information](#contact-information)  
- [References](#references)  


---

## Introduction

Dynamic Application Security Testing (DAST) identifies security vulnerabilities in running web applications by simulating real-world attacks. This document provides an overview of DAST, including what it is,Why DAST, its workflow, commonly used tools, key advantages, a Proof of Concept (PoC), and best practices.


---

## What is DAST

Dynamic Application Security Testing (DAST) is a method to find security weaknesses in a running web application by simulating real hacker attacks. It tests the application from the outside, just like an attacker would, to discover vulnerabilities that could be exploited.


---

## Why DAST?

| **Reason**                         | **Explanation**                                                           |
|-----------------------------------|---------------------------------------------------------------------------|
| **Finds security issues early**    | Helps developers detect vulnerabilities during development.               |
| **Saves cost**                     | Fixing problems early is cheaper than after deployment.                  |
| **Prevents breaches**              | Reduces the risk of data leaks and financial loss.                        |
| **Protects reputation**            | Avoids damage to company image due to security issues.                    |
| **Reduces human errors**           | Automated testing helps catch mistakes that might be missed manually.     |

---

## Workflow of DAST

 ![image](https://xebia.com/wp-content/uploads/2023/02/HowDastWorks-1024x386.png.webp)

---

## **Different Tools Used in DAST**
| **Tool Name**                | **Description**                                                                 | **Features**                                                  |
|------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------|
| **OWASP ZAP**                 | Open-source security testing tool.                                              | Automated scanners, vulnerability detection, active and passive scanning. |
| **Burp Suite**                | Comprehensive platform for web application security testing.                    | Intercepting proxy, vulnerability scanning, custom extensions.   |
| **Acunetix**                  | Automated security scanner for web applications.                                | Detects SQL injection, XSS, and other vulnerabilities.            |
| **AppSpider**                 | Dynamic application security testing tool.                                      | Scanning for Java frameworks, automated vulnerability discovery. |

---

## Tool Comparison
| **Tool Name**   | **Cost**      | **Ease of Use** | **Features**               | **Customization**   |
|-----------------|---------------|-----------------|----------------------------|----------------------|
| OWASP ZAP       | Free          | Moderate        | Basic and essential scans  | High                 |
| Burp Suite      | Expensive     | High            | Comprehensive tools        | High                 |
| Acunetix        | Expensive     | Easy            | Broad vulnerability scans  | Moderate             |
| AppSpider       | High          | Moderate        | Java-specific capabilities | High                 |

---

## Advantages of DAST
| **Advantage**                 | **Description**                                                              |
|-------------------------------|------------------------------------------------------------------------------|
| **Real-time vulnerability detection** | Identifies issues during the application’s runtime.                          |
| **Simulates real-world attacks**       | Mimics hacker techniques to expose weaknesses.                              |
| **Supports CI/CD integration**         | Integrates with pipelines to ensure ongoing security.                      |
| **Risk reduction**                     | Reduces the likelihood of breaches and ensures compliance with standards.  |

## **POC: DAST Using OWASP ZAP**

---
>
>Here is the Proof of Concept (PoC) document for your reference : [document](https://github.com/duggu7055/Snaatak/blob/main/Sprint2/Java-ci/poc/Readme.md)


---

## Best Practices
| **Best Practice**                         | **Description**                                                                |
|------------------------------------------|--------------------------------------------------------------------------------|
| **Define clear testing scope**            | Ensure only relevant parts of the application are tested.                     |
| **Integrate into CI/CD pipelines**        | Automate security testing for consistent evaluations.                         |
| **Regularly update tools**                | Use the latest updates to address emerging threats.                           |
| **Test in staging environments**          | Avoid disrupting production with security scans.                              |
| **Combine with other AST techniques**     | Use SAST and IAST along with DAST for comprehensive security coverage.        |

---

## Recommendation and Conclusion
For this project, **OWASP ZAP** is recommended due to its open-source nature, extensive community support, and suitability for Java applications. Its features and cost-effectiveness make it an ideal choice for initial and ongoing security testing.

---

## Contact Information


| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## **References**
| **Link** | **Description** |
|------------------------------------------------------|------------------|
| https://www.ibm.com/topics/dynamic-application-security-testing| DAST and types |
| https://www.techmagic.co/blog/dast| DAST tool |
