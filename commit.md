# Recommendations of Commit Hooks 

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  28-07-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |

![image](https://github.com/user-attachments/assets/0c9ff608-1d67-4d20-9cd9-01415c68fdaa)


## Purpose 
This document explains the different types of commit hooks, how they work, and when to use them. It also gives recommendations on which commit hooks are most useful. By reading this, you will understand which commit hooks are best for your project and why they matter in the development process.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Types of Commit Hooks Overview](#types-of-commit-hooks-overview)
   - [Client-Side Commit Hooks](#client-side-commit-hooks)
   - [Server-Side Commit Hooks](#server-side-commit-hooks)
3. [Recommendations for Using Hooks](#recommendations-for-using-hooks)
   - [Pre-Commit Hook](#pre-commit-hook)
   - [Post-Commit Hook](#post-commit-hooks)
4. [Conclusion](#conclusion)
5. [Contact Information](#contact-information)
6. [References](#references)
   
## Introduction
Commit hooks are Git hooks triggered during the commit process to enforce code quality and standards. They check code formatting, validate commit messages, detect sensitive data, run tests, and ensure compliance. Integrating commit hooks helps catch errors early, reduces manual reviews, and maintains code integrity.

## Types of Commit Hooks Overview
![image](https://github.com/user-attachments/assets/e1cf3d43-ac2f-40ed-9410-eb905c3046b1)

Please refer this  [link](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-104-deepak/VCS/Commit-Hooks/Introduction/README.md) for more about commit hooks

---
### Recommendations for Using Hooks

### 1. Pre-Commit Hook

**What it does:**  
This hook runs **before** a commit is made. It checks your code to catch any problems early.

**Why use it:**  
A pre-commit hook helps maintain **clean and error-free code**. It checks for:
- Proper formatting  
- Coding mistakes (linting)  
- Basic test results  
- Dependency issues  

Using it means:
- Fewer bugs in the code  
- Consistent code style  
- Quick feedback while coding  

**Recommended Pre-Commit Checks:**

| Hook Type         | What it Checks                            | Why it’s Useful                                 |
|-------------------|--------------------------------------------|-------------------------------------------------|
| Code Formatting   | Formats code to follow team style          | Keeps code clean and consistent                 |
| Linting           | Looks for possible coding errors           | Catches issues before they go into the codebase |
| Basic Tests       | Runs small tests to check if code works    | Blocks broken code from being committed         |
| Dependency Checks | Verifies required packages or libraries    | Avoids missing or outdated package problems     |

---

### 2. Post-Commit Hook

**What it does:**  
This hook runs **after** a commit is successfully made. It handles follow-up tasks.

**Why use it:**  
A post-commit hook helps **automate tasks** like:
- Sending notifications  
- Logging changes  
- Starting CI/CD pipelines  
- Running scripts that depend on the commit  

This saves time, keeps the team informed, and improves collaboration.

**Recommended Post-Commit Tasks:**

| Hook Type           | What it Does                               | Why it’s Useful                              |
|---------------------|---------------------------------------------|----------------------------------------------|
| Notifications       | Sends commit info to team channels          | Keeps everyone up-to-date                    |
| Log Management      | Adds commit info to logs                    | Helps track changes and history              |
| CI/CD Triggers      | Starts build/deploy pipelines               | Automates testing and deployment             |
| Post-Commit Scripts | Runs tools that need a completed commit     | Useful for integrations or reporting         |


## Conclusion

Using **pre-commit** and **post-commit** hooks is important for keeping your code clean and your development process smooth.

- **Pre-commit hooks** help catch issues early by checking code formatting, running linters, and basic tests. This makes sure only high-quality code is committed.
- **Post-commit hooks** automate tasks after a commit, like sending notifications, triggering CI/CD pipelines, and updating other systems.

Together, they improve code quality, save time, and support better teamwork.


## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

| Title | Links|
|------|---------------------|
|  **Unstop** |https://unstop.com/blog/git-hooks |
| **Medium** |https://tinyurl.com/3822mhpr|
| **Commit Hook detailed doc**|https://tinyurl.com/4xby7m9s|
