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
- [Step-by-step Installation](#step-by-step-installation)
- [Generate HTML Report with Surefire](#generate-html-report-with-surefire)
- [POC Conclusion](#poc-conclusion)
- [Contact Information](#contact-information)
- [References](#references)

---

## Introduction
Unit testing in Java ensures that each part of your code works correctly. This guide explains how to set up and run unit tests using the **JUnit** framework.

#### NOTE:  
 We are using **SalaryAPI** for Java Unit testing.  

---

## Prerequisites
- **Java 17** – as specified in `pom.xml`
- **Maven** – for managing dependencies and building the project
- **JUnit** – library for writing and running unit tests

### System Requirements

Please refer this link [Salary DOCunmentation](https://github.com/Snaatak-Cloudops-Crew/documentation/tree/scrum-70-abhishek-saini/0T-Microservices/Applications/Salary-Api/Introduction)

---

## Testing Framework

Unit testing checks if individual parts of your Java code work correctly. **JUnit** is a widely used and popular framework for Java unit testing, and we are using it in this project to write, organize, and run our tests efficiently.

#### Note
The **salary microservice** already has unit tests written by the developer:

---

## **Step-by-step Installation**
 
> For complete steps, refer to the official POC documentation: [Salary API POC](https://github.com/Snaatak-Cloudops-Crew/documentation/blob/SCRUM-69-deepak/OT-Microservices/Applications/Salary-API/POC/README.md)


### Step 1. Clean the project
#### This removes any previously compiled files or cached test results.
<img width="725" height="342" alt="Screenshot from 2025-08-15 11-55-50" src="https://github.com/user-attachments/assets/07b2512e-ccb8-4420-871f-479e635fe38d" />

### Step 2. 

#### Add the JUnit Dependency to ```pom.xml```
Ensure that the JUnit dependency is added to your ```pom.xml``` file:
```
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
</dependency>
```
![Screenshot from 2024-09-30 11-26-29](https://github.com/user-attachments/assets/9440f179-d1f9-49db-ad64-3bd18cddd81a)


#### Add Maven Dependency in ```pom.xml```
Add the Maven compiler plugin to your ```pom.xml``` file for compiling your Java project:
```
<dependency>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.11.0</version>
    <type>maven-plugin</type>
</dependency>
```
![Screenshot from 2024-09-30 11-25-10](https://github.com/user-attachments/assets/c5eeed17-8b8e-4d73-9e1c-a2b29954e880)

#### Update Surefire Plugin Configuration in pom.xml
To resolve compatibility issues with JUnit, you may need to uncomment and adjust the Surefire plugin configuration in the pom.xml file.
Make sure to update the Surefire plugin 3.0.0:
![Screenshot from 2024-09-30 11-23-38](https://github.com/user-attachments/assets/51c12b2b-7107-4443-8c56-0b5f77bdb976)

### Step 5. Execute Java Unit Tests
- ![Screenshot 2025-05-21 233155](https://github.com/user-attachments/assets/b8598620-795f-402d-8596-0b7cf997dcce)

- ![image](https://github.com/user-attachments/assets/fd6c8208-3f37-4b27-b8fc-f68a9f00bede)


## Generate HTML Report with Surefire
To generate an HTML report from the test execution, run the following command:
```
mvn surefire-report:report
```
Navigate to target/site to view the generated report in your browser.

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
