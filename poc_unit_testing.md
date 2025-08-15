## Proof of Concept (POC) for Java Unit Testing

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  11-08-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |


---

## Table of Contents

- [Introduction](#introduction)
- [Pre-requisites](#pre-requisites)
- [System Requirements](#system-requirements)
- [Testing Framework](#testing-framework)
- [JUnit Setup and Test Execution](#junit-setup-and-test-execution)
- [POC Conclusion](#poc-conclusion)
- [Contact Information](#contact-information)
- [References](#references)

---

## Introduction
Unit testing in Java ensures that each part of your code works correctly. This guide explains how to set up and run unit tests using the **JUnit** framework.

#### NOTE:  
 We are using **SalaryAPI** for Java Unit testing.  
 The **salary microservice** already has unit tests written by the developer:

---

## Prerequisites
- Java 17 – as specified in `pom.xml`
- Maven – for managing dependencies and building the project
- JUnit – library for writing and running unit tests

### System Requirements
Please refer this link [Salary DOCunmentation](https://github.com/Snaatak-Cloudops-Crew/documentation/tree/scrum-70-abhishek-saini/0T-Microservices/Applications/Salary-Api/Introduction)

---

## Testing Framework

Unit testing checks if individual parts of your Java code work correctly. **JUnit** is a widely used and popular framework for Java unit testing, and we are using it in this project to write, organize, and run our tests efficiently.

---

## JUnit Setup and Test Execution
 
##### For complete steps, refer to the official POC documentation: [Salary API POC](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-69-deepak/OT-Microservices/Applications/Salary-API/POC/README.md)

### Step 1. Clean the project

##### This removes any previously compiled files or cached test results.

<img width="725" height="342" alt="Screenshot from 2025-08-15 11-55-50" src="https://github.com/user-attachments/assets/07b2512e-ccb8-4420-871f-479e635fe38d" />

### Step 2. 

#### Ensure JUnit Dependency to ```pom.xml```
Ensure that the JUnit dependency is added to your ```pom.xml``` file if not add :
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```
<img width="985" height="591" alt="Screenshot from 2025-08-15 12-27-01" src="https://github.com/user-attachments/assets/72f73e21-c80c-42c8-84e1-255bf72be01c" />


#### Maven Plugin in ```pom.xml```
Add the Maven compiler plugin to your ```pom.xml``` file for compiling your Java project if not present:
```
<<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
    <configuration>
        <excludes>
            <exclude>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
            </exclude>
        </excludes>
    </configuration>
</plugin>


```
<img width="945" height="301" alt="Screenshot from 2025-08-15 12-37-37" src="https://github.com/user-attachments/assets/183e0f8c-eb10-4786-97cb-e5d7ed279d8c" />


### Step 3. Execute Java Unit Tests

<img width="1211" height="840" alt="Screenshot from 2025-08-15 13-04-16" src="https://github.com/user-attachments/assets/a024b64a-5b20-4cba-84f5-95ef504f6577" />


<img width="1102" height="677" alt="Screenshot from 2025-08-15 13-06-13" src="https://github.com/user-attachments/assets/8f33eeb1-da99-4d84-bf0e-28b2f131f8e9" />

---

## POC Conclusion
This POC shows that using JUnit and Maven for unit testing improves code reliability, detects bugs early, and ensures maintainability. Automated tests within a continuous integration setup help prevent new changes from breaking existing functionality, making the software more robust and dependable.


---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References 
|links | Description |
|-------|-----------|
|https://www.browserstack.com/guide/unit-testing-java | Unit Testing |
| https://www.baeldung.com/java-unit-testing-best-practices | Best Practices for Unit Testing |
