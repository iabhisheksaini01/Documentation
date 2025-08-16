## Documentation of DAST (Dynamic Application Security Testing) in Java CI Checks

<p align="center">
  <img src="https://github.com/user-attachments/assets/59c8d98d-eba7-4899-9c5b-60efca18185b" width="800" height="600" />
</p>


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


## Workflow of DAST

 ![image](https://xebia.com/wp-content/uploads/2023/02/HowDastWorks-1024x386.png.webp)

---

## Different Tools Used in DAST

| **Tool Name**   | **Description**                           | **Key Features**                                         |
|-----------------|-------------------------------------------|---------------------------------------------------------|
| **OWASP ZAP**    | Free and open-source security tool.       | Automated vulnerability scanning, active & passive tests, easy integration with CI/CD. |
| **Burp Suite**   | Widely used web security platform.        | Intercept and analyze web traffic, vulnerability scanning, supports plugins for customization. |
| **Acunetix**     | Commercial automated web scanner.         | Detects SQL injection, XSS, weak passwords, and other common vulnerabilities. |
| **AppSpider**    | Enterprise DAST tool for web applications.| Scans multiple web frameworks, detects Java-specific vulnerabilities, generates detailed reports. |

---
## Tool Comparison

| **Tool Name**   | **Cost**      | **Ease of Use** | **Key Features**               | **Customization**   |
|-----------------|---------------|----------------|--------------------------------|--------------------|
| **OWASP ZAP**   | Free          | Moderate       | Automated scans, finds common vulnerabilities | High – supports scripts and CI/CD integration |
| **Burp Suite**  | Paid          | Easy-Moderate  | Full web security testing, intercept traffic, scan vulnerabilities | High – plugins and extensions available |
| **Acunetix**    | Paid          | Easy           | Detects SQLi, XSS, weak passwords, broad vulnerability coverage | Moderate – limited customization |
| **AppSpider**   | Paid/High     | Moderate       | Focused on Java apps, automated scans, detailed reports | High – supports enterprise-level customization |


---

## Advantages of DAST

| **Advantage**                 | **Description**                                                             |
|-------------------------------|-----------------------------------------------------------------------------|
| **Detects vulnerabilities at runtime** | Finds security issues while the application is running.                 |
| **Simulates real attacks**            | Tests the app like a hacker would to reveal weaknesses.                  |
| **CI/CD friendly**                   | Can be integrated into pipelines for continuous security checks.        |
| **Reduces risk**                      | Lowers chances of breaches and helps meet security standards.           |


## POC: DAST Using OWASP ZAP

---
>
>Here is the Proof of Concept (PoC) document for your reference : [document](https://github.com/duggu7055/Snaatak/blob/main/Sprint2/Java-ci/poc/Readme.md)


---

## Best Practices

| **Best Practice**                 | **Description**                                                        |
|----------------------------------|------------------------------------------------------------------------|
| **Set clear testing scope**       | Focus testing only on relevant parts of the application.              |
| **Integrate with CI/CD**          | Automate security checks for consistent and continuous testing.       |
| **Keep tools updated**            | Use the latest versions to handle new vulnerabilities.                |
| **Test in staging environments**  | Run scans on non-production environments to avoid downtime.           |
| **Combine with other AST methods**| Use SAST and IAST along with DAST for full security coverage.         |

---

## Recommendation and Conclusion

**OWASP ZAP** is a strong choice for DAST because it is free, open-source, and supported by a large community. It works well with Java applications and provides essential security testing features, making it suitable for both initial assessments and continuous testing.

---

## Contact Information


| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| **Link** | **Description** |
|----------|-----------------|
| [Black Duck - What is DAST?](https://www.blackduck.com/glossary/what-is-dast.html) | Overview of DAST and how it works |
| [OWASP - Dynamic Application Security Testing](https://owasp.org/www-project-devsecops-guideline/latest/02b-Dynamic-Application-Security-Testing) | Detailed explanation of DAST and its black-box testing approach |

