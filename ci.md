
# CI Workflow Guide for Ansible Roles

<img width="266" height="190" alt="download" src="https://github.com/user-attachments/assets/348c87d9-5583-436a-9b64-bbe559adb9d4" />


## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  16-07-2025        | V 1.0            |     18-07-2025    |  Prashant          |  Priyanka      |      Rishabh sharma   |   piyush upadhyay |


---

##  Table of Contents

1. [Introduction](#introduction)  
2. [Why CI for Ansible Roles?](#why-ci-for-ansible-roles)  
3. [Overview of CI Workflow](#overview-of-ci-workflow)  
4. [Prerequisites](#prerequisites)  
5. [Recommended Directory Layout](#recommended-directory-layout)  
6. [Workflow Breakdown](#workflow-breakdown)  
7. [Sample GitLab CI Configuration](#sample-gitlab-ci-configuration)  
8. [Recommended Practices](#recommended-practices)  
9. [Common Issues & Fixes](#common-issues--fixes)  
10. [Useful Resources](#useful-resources)  
11. [Contact Info](#contact-info)  
12. [Summary](#summary)

---

## Introduction <a id="introduction"></a>

This document provides a structured guide to implement **Continuous Integration (CI)** for **Ansible roles**, with a focus on automating testing, linting, and validation using GitLab CI pipelines.

---

##  Why CI for Ansible Roles? <a id="why-ci-for-ansible-roles"></a>

-  Automates validation and testing for every commit  
-  Detects issues (syntax, logic) early in the pipeline  
-  Promotes cleaner, standardized role development  
-  Reduces manual verification overhead  
-  Facilitates rapid and safe iteration through Molecule testing  

---

##  Overview of CI Workflow <a id="overview-of-ci-workflow"></a>

A typical CI pipeline for Ansible roles includes the following steps:

- 🔸 **Linting** with `ansible-lint`  
- 🔸 **Syntax validation** using `ansible-playbook --syntax-check`  
- 🔸 **Molecule test execution** using Docker or Podman  
- 🔸 **Scenario-based validation** (e.g., idempotency check)  
- 🔸 **Artifact/report generation** (optional)  

---

##  Prerequisites <a id="prerequisites"></a>

Make sure the following tools and setup are ready:

- GitLab/GitHub/Bitbucket CI runner  
- Docker or Podman installed on runner  
- Python packages: `ansible`, `molecule`, `ansible-lint`  
- Role should follow [Ansible Galaxy](https://galaxy.ansible.com/) standard layout  

---

##  Recommended Directory Layout <a id="recommended-directory-layout"></a>

```bash
ansible-role-name/
├── defaults/
│   └── main.yml
├── handlers/
│   └── main.yml
├── tasks/
│   └── main.yml
├── molecule/
│   └── default/
│       ├── converge.yml
│       └── molecule.yml
├── meta/
│   └── main.yml
├── tests/
├── .gitlab-ci.yml
└── README.md
```

---

## Workflow Breakdown <a id="workflow-breakdown"></a>

### CI Pipeline Breakdown

1. **Dependency Installation**  
   Install `ansible`, `molecule`, `ansible-lint`, and `docker` via `pip`.

2. **Lint Check**  
   Run `ansible-lint` to ensure code hygiene and compliance.

3. **Syntax Validation**  
   Validate the syntax using a local `ansible-playbook --syntax-check`.

4. **Molecule Test**  
   Launch test containers and run the `converge.yml`.

5. **Idempotency Validation**  
   Verify that reapplying the role doesn't make changes.

6. **Cleanup Phase**  
   Destroy the Molecule environment and release resources.

---

##  Sample GitLab CI Configuration <a id="sample-gitlab-ci-configuration"></a>

```yaml
stages:
  - lint
  - syntax
  - test

variables:
  ANSIBLE_FORCE_COLOR: "true"

before_script:
  - pip install ansible ansible-lint molecule docker

lint:
  stage: lint
  script:
    - ansible-lint .

syntax-check:
  stage: syntax
  script:
    - ansible-playbook -i localhost, -c local molecule/default/converge.yml --syntax-check

molecule-test:
  stage: test
  script:
    - molecule test
```

---

##  Recommended Practices <a id="recommended-practices"></a>

- 🔸 Keep test cases simple and reproducible  
- 🔸 Validate **idempotency** in each scenario  
- 🔸 Always maintain an up-to-date `README.md`  
- 🔸 Follow naming conventions aligned with Ansible Galaxy  
- 🔸 Isolate variables and avoid hardcoding  

---

## 🛠Common Issues & Fixes <a id="common-issues--fixes"></a>

| Issue                         | Suggestion                                                                 |
|------------------------------|----------------------------------------------------------------------------|
| Docker permission denied     | Ensure CI runner has access to Docker socket (`/var/run/docker.sock`)     |
| Molecule cleanup failure     | Use `--destroy=never` to retain containers for debugging                   |
| Lint rule violations         | Avoid hardcoded paths and use proper task tags                            |
| CI pipeline timeout          | Use optimized base images and reduce network dependencies                  |

---

## Useful Resources <a id="useful-resources"></a>

- []()  
-    
-  

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| **Link**                                                                 | **Description**                                   |
|--------------------------------------------------------------------------|---------------------------------------------------|
| [Ansible Lint Docs ](https://ansible-lint.readthedocs.io) | Document format followed from this link.          |
| [Molecule Testing](https://molecule.readthedocs.io) | Document format followed from this link.          |
| [GitLab CI Documentation](https://docs.gitlab.com/ee/ci/) | Document format followed from this link.          |
---

##  Summary <a id="summary"></a>

Adopting CI pipelines for Ansible roles not only improves code reliability but also enhances team collaboration and delivery speed. This guide provides a detailed blueprint to implement and maintain a CI pipeline using `ansible-lint`, `molecule`, and GitLab CI. Following this approach will help ensure consistent, high-quality infrastructure automation.
