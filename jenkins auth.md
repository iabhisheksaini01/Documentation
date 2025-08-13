# Jenkins Authentication and Authorization Documentation

<p align="center">
  <img src="https://www.jenkins.io/images/logos/jenkins/jenkins.png" width="400" height="400" alt="Jenkins Logo" />
</p>

---

## Author Information

| Created by      | Created on         | Version          | Last updated On   | Pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek Saini  |  12-08-2025        | V 1.0            |      |  Sahil          |      |         |   - |

---

## Table of Contents

- [Introduction](#introduction)
- [What is Jenkins Authentication and Authorization?](#what-is-jenkins-authentication-and-authorization)
- [Why Use Authentication and Authorization in Jenkins?](#why-use-authentication-and-authorization-in-jenkins)
- [Workflow](#workflow)
- [Types of Authentication and Authorization](#types-of-authentication-and-authorization)
- [Comparison Table](#comparison-table)
- [Best Practices](#best-practices)
- [Recommendation & Conclusion](#recommendation--conclusion)
- [Contact Information](#contact-information)
- [References](#references)

---

## Introduction

Jenkins is a popular tool for automating software builds, tests, and deployments. Because Jenkins can control important parts of your software and infrastructure, it’s very important to keep it secure. This guide explains, in simple terms, how Jenkins checks who you are (authentication) and what you’re allowed to do (authorization), and how you can set these up to keep your system safe.

---

## What is Jenkins Authentication and Authorization?

### Authentication
Authentication ensures only valid users can access Jenkins by verifying their identity using methods like username/password, LDAP, SAML, or OAuth.

### Authorization
Authorization defines user access levels and actions within SonarQube through roles and permissions.
Together, these mechanisms ensure that only trusted users can access Jenkins and that their actions are controlled according to organizational policies.

---

## Why Use Authentication and Authorization in Jenkins?

| Aspect           | Description                                              |
|------------------|----------------------------------------------------------|
| **Security**     | Protect sensitive data from unauthorized access.         |
| **Compliance**   | Meet regulatory requirements for software development.   |
| **Separation of Duties**    | Ensures users only have permissions necessary for their roles.                  |
| **User Management** | Define granular access controls for different teams.      |
| **Auditability** | Maintain detailed logs for accountability and tracking.   |


---

## Workflow

![Jenkins Auth Workflow](https://user-images.githubusercontent.com/123456789/jenkins-auth-workflow.png)

**Workflow Steps:**
1. **User Access:** User attempts to access Jenkins UI or API.
2. **Authentication:** Jenkins verifies user identity (via internal DB, LDAP, SSO, etc.).
3. **Authorization:** Jenkins checks user permissions based on configured strategy.
4. **Action Execution:** If permitted, user can perform the requested action; otherwise, access is denied.
5. **Audit Logging:** All access and actions are logged for traceability.

---

## Types of Authentication and Authorization

### Authentication Methods

| **Methods**                  | **Description**                                                                 |
|----------------------------|-----------------------------------------------------------------------------------|
| **Jenkins’ Own Users**     | Users are created and managed **inside Jenkins**. You set their usernames and passwords. |
| **LDAP / Active Directory**| Uses your **company’s login system** (like Windows Active Directory or Google Workspace) to sign in. |
| **Single Sign-On (SSO)**  | Lets you **log in using accounts from other services** like Google, GitHub, or GitLab. |
| **API Token**              | A **special password for scripts and tools**, not for humans to log in directly. |



### Authorization Strategies

| **Strategy**                 | **Description**                                              |
|-------------------------------|---------------------------------------------------------------|
| **Matrix-based Security**     | You can give each user or group specific permissions.        |
| **Project-based Matrix**      | You can give different permissions for each project/job.     |
| **Logged-in Users Can Do Anything** | Any user who logs in can do everything.                     |
| **Anyone Can Do Anything**    | Everyone can access and change Jenkins, no login needed.     |
| **Role-based Strategy (Plugin)** | Create roles (like admin, developer) and give them permissions. |

---

## Comparison Table

| **Feature**               | **Jenkins Users** | **LDAP / AD** | **SSO** | **Matrix Security** | **Role-based** |
|---------------------------|:----------------:|:-------------:|:------:|:-----------------:|:--------------:|
| Manage Users Easily        |       No         |      Yes      |   Yes  |        N/A        |       N/A      |
| Control What Users Can Do  |       N/A        |      N/A      |   N/A  |        Yes        |       Yes      |
| Easy to Set Up             |       Yes        |      No       |   No   |        Yes        |       Yes      |
| Works Well for Large Teams  |       No         |      Yes      |   Yes  |        Yes        |       Yes      |
| Can Use Groups             |       No         |      Yes      |   Yes  |        Yes        |       Yes      |
| Safe for Production        |       No         |      Yes      |   Yes  |        Yes        |       Yes      |


---

## Best Practices

| **Practice**                        | **Description**                                                                 |
|--------------------------------------|---------------------------------------------------------------------------------|
| **Disable Anonymous Access**         | Prevents unauthenticated users from accessing Jenkins.                          |
| **Use External Authentication**      | Integrate with LDAP, SSO, or SCM providers for centralized identity.            |
| **Apply Least Privilege Principle**  | Grant users only the permissions they need.                                     |
| **Use Matrix/Role-based Authorization** | Enables fine-grained access control.                                         |
| **Regularly Review Permissions**     | Audit user roles and permissions periodically.                                  |
| **Enable Audit Logging**             | Track all access and changes for compliance.                                    |
| **Rotate API Tokens/Passwords**      | Regularly update credentials and tokens.                                        |
| **Keep Jenkins and Plugins Updated** | Patch vulnerabilities by updating Jenkins core and plugins.                     |

---

## Recommendation & Conclusion

For secure and scalable Jenkins deployments:

- **Use external authentication** (LDAP/AD or SSO) for centralized user management.
- **Implement matrix-based or role-based authorization** for fine-grained access control.
- **Disable anonymous access** and enforce strong password policies.
- **Regularly audit** user permissions and review logs.
- **Keep Jenkins and all plugins up to date** to mitigate security risks.

By following these practices, organizations can ensure that their Jenkins environments are secure, compliant, and resilient against unauthorized access.

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek Saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| **Resource**                        | **Link**                                               |
|-------------------------------------|--------------------------------------------------------|
| Jenkins Security Documentation      | [Visit](https://www.jenkins.io/doc/book/security/)     |
| Jenkins Matrix Authorization Plugin | [Visit](https://plugins.jenkins.io/matrix-auth/)       |
| Jenkins Role Strategy Plugin        | [Visit](https://plugins.jenkins.io/role-strategy/)     |
| Jenkins Authentication Methods      | [Visit](https://www.jenkins.io/doc/book/security/authentication/) |
| Jenkins Best Practices              | [Visit](https://www.jenkins.io/doc/book/best-practices/) |
