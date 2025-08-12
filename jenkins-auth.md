#  Documentation: Jenkins Authentication & Authorization

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  12-08-2025        | V 1.0            |    |  Prashant          |  -      |      -  |  - |

---

##  Table of Contents

1. [Introduction](#introduction)
2. [What is Jenkins](#what-is-jenkins)
3. [What is Authentication and Authorization?](#what-is-authentication-and-authorization)
4. [Why Use Authentication and Authorization in Jenkins?](#why-use-authentication-and-authorization-in-jenkins)
5. [Jenkins Authn & Authz Workflow](#jenkins-authn--authz-workflow)
6. [Authentication Strategies in Jenkins](#authentication-strategies-in-jenkins)
7. [Authorization Strategies in Jenkins](#authorization-strategies-in-jenkins)
8. [Authentication Method Comparison](#comparison-table)
9. [Best Practices](#best-practices)
10. [Conclusion](#conclusion)
11. [Contact Information](#contact-information)
12. [References](#references)



##  Introduction

This document provides an overview of Jenkins' authentication and authorization mechanisms, focusing on securing access and managing user permissions.

## What is Jenkins

Jenkins is a crucial part of CI/CD pipelines, often handling sensitive information such as source code, credentials, and deployment configurations. Securing Jenkins ensures that only authorized users can access these critical assets, protecting the integrity of the development and deployment processes.


##  What is Authentication and Authorization?

| Concept         | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| **Authentication (AuthN)** | Process of verifying the identity of users accessing Jenkins.           |
| **Authorization (AuthZ)** | Process of assigning access permissions to authenticated users.        |

---

##  Why Use Authentication and Authorization in Jenkins?

| Purpose                      | Reason                                                                 |
|------------------------------|------------------------------------------------------------------------|
|  **Secure Access**             | Prevent unauthorized access to Jenkins and its resources.              |
|  **Role Management**           | Control user access based on roles and responsibilities.               |
|  **Audit & Compliance**        | Track who did what and ensure compliance with organizational policies. |
|  **Safe Environment**           | Protect build/test pipelines from tampering.                           |

---

##  Jenkins AuthN & AuthZ Workflow

```plaintext
        [User Request Access]
                |
        [Authentication Method]
        (Jenkins DB / LDAP / SSO / GitHub)
                |
                V
       [User Identity Verified]
                |
        [Authorization Strategy]
        (Matrix / Role / Project-based)
                |
                V
       [Access Granted or Denied]
```

---

##  Authentication Strategies in Jenkins

| Method            | Description                                                  | Use Case                                |
|------------------|--------------------------------------------------------------|-----------------------------------------|
| **Jenkins Internal Database** | Default method, manages users within Jenkins itself.     | Small teams or testing environments     |
| **LDAP**          | Integrates with corporate directories (e.g., Active Directory).| Enterprises using centralized identity  |
| **SSO (Single Sign-On)** | Uses providers like SAML or OIDC to allow single sign-on. | Organizations with centralized auth     |
| **GitHub/GitLab** | Authenticates users via OAuth using their GitHub/GitLab accounts. | Developer-focused teams                 |

---

##  Authorization Strategies in Jenkins

| Strategy               | Description                                                             | Suitable For                  |
|------------------------|-------------------------------------------------------------------------|-------------------------------|
| **Anyone Can Do Anything** | No restrictions — everyone is admin.                                    | Not recommended               |
| **Legacy Matrix**         | Fine-grained permissions assigned to users/groups.                    | Medium to large teams         |
| **Project-based Matrix**  | Matrix-based plus per-job permissions.                                | Teams with job-specific roles |
| **Role-Based Strategy**   | Roles assigned at global/item level via plugin.                       | Enterprises, multi-team setups|
| **Logged-in Users Can Do Anything** | Only logged-in users have full access.                          | Small internal teams          |

---

##  Comparison Table

| Feature                        | Jenkins DB                  | LDAP                                | GitHub OAuth                         | SSO (SAML/OIDC)                      |
|-------------------------------|-----------------------------|--------------------------------------|--------------------------------------|--------------------------------------|
| **Built-in**                  | Yes, comes pre-installed    | No, requires configuration           | No, needs plugin and setup           | No, needs plugin and setup           |
| **External Identity Source**  | No, uses internal database  | Yes, connects to directory services | Yes, authenticates via GitHub        | Yes, integrates with identity providers |
| **Requires Plugin**           | No plugin needed            | Yes, LDAP plugin required            | Yes, GitHub OAuth plugin required    | Yes, SAML or OIDC plugin required    |
| **Fine-grained Access Control** | Yes, supports roles/groups | Yes, supports group-based access     | Yes, can map teams to roles          | Yes, supports detailed role mapping  |
| **Enterprise Ready**          | Basic only, limited scaling | Yes, widely used in enterprises      | Yes, scalable for GitHub users       | Yes, ideal for large organizations   |

---



##  Best Practices

| Security Best Practice               | Description                                                           |
| ------------------------------------ | --------------------------------------------------------------------- |
| **Use authentication**               | Always enable authentication; never leave Jenkins open to the public. |
| **Enable CSRF protection**           | Turn on CSRF protection in Jenkins security settings.                 |
| **Role-Based Access Control (RBAC)** | Use RBAC for fine-grained permission handling.                        |
| **Limit anonymous access**           | Restrict anonymous users to read-only or no access.                   |
| **Use HTTPS**                        | Secure all authentication traffic using HTTPS.                        |
| **Audit regularly**                  | Review user permissions and build logs frequently.                    |

---

## Conclusion

- For **small teams**, internal Jenkins DB with matrix strategy may be sufficient.
- For **enterprise or production**, integrate Jenkins with **LDAP/SSO** and enable **role-based authorization**.
- Combine **authentication** with **monitoring/logging plugins** to maintain traceability.
- Keep Jenkins and plugins **updated** to avoid security vulnerabilities.

---
## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---
##  References

| Title                              | Link                                                                 |
|------------------------------------|----------------------------------------------------------------------|
| Jenkins Security Documentation     | [Link](https://www.jenkins.io/doc/book/security/)                   |
| Role Strategy Plugin               | [Link](https://plugins.jenkins.io/role-strategy/)                            |
| GitHub OAuth Plugin for Jenkins    | [Link](https://plugins.jenkins.io/github-oauth/)                             |
| LDAP Plugin                        | [Link](https://plugins.jenkins.io/ldap/)                                    |

---
