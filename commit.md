# Recommendations of Commit Hooks 

<p align="center">
  <img src="https://github.com/user-attachments/assets/071536d8-7b76-4cb5-abd1-13c90d3f8acd" width="500" height="300" />
</p>

---


## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  28-07-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |

---


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


### 3. Commit-msg Hook

**What it does:**  
This hook runs **after** you write a commit message but **before** the commit is finalized. It checks the message format and content.

**Why use it:**  
A commit-msg hook ensures that every commit message follows a **consistent and meaningful format**, which is helpful for:
- Easier understanding of commit history  
- Linking commits to issues (e.g., JIRA or GitHub)  
- Generating changelogs or release notes  
- Automating CI/CD processes

Using it means:
- Uniform commit messages across the team  
- Easier tracking and debugging  
- Better integration with project management tools

**Recommended Commit-msg Checks:**

| Hook Type          | What it Checks                                     | Why it’s Useful                                      |
|--------------------|-----------------------------------------------------|------------------------------------------------------|
| Format Validation  | Ensures message follows pattern (e.g., `type: msg`) | Keeps messages consistent for history or changelog   |
| Issue ID Presence  | Checks for ticket ID like `SCRUM-1234:`             | Links commits to tasks or bugs in tools like JIRA    |
| Message Length     | Enforces minimum and maximum character limits       | Avoids vague or overly long commit messages          |
| No Empty Messages  | Blocks commits without a valid message              | Ensures commit log is always informative             |

---

## Conclusion

Implementing Git commit hooks improves the quality, consistency, and automation of your development process.

- **Pre-commit hooks** catch formatting errors, linting issues, and failing tests before code enters the repository.
- **Post-commit hooks** automate tasks like logging, notifications, and CI/CD pipeline triggers.
- **Commit-msg hooks** ensure that commit messages follow a standard format and include necessary details like ticket IDs.

By using these hooks together, teams can maintain cleaner codebases, reduce manual review effort, and enforce best practices automatically.

---
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
