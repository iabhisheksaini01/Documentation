# Documentation on Java

# Table of Contents

| Section No. | Title | Description |
|-------------|-------|-------------|
| 1 | [Overview](#1-overview) | General introduction to Java and its core purpose. |
| 2 | [History of Java](#2-history-of-java) | Evolution of Java from 1991 to present. |
| 3 | [Core Features of Java](#3-core-features-of-java) | Key features like OOP, platform independence, etc. |
| 4 | [Java Architecture](#4-java-architecture) | Components like JVM, JDK, JRE, and how Java runs. |
| 5 | [Basic Syntax & Structure](#5-basic-syntax--structure) | Structure of a simple Java program. |
| 6 | [Data Types & Variables](#6-data-types--variables) | Primitive and reference data types used in Java. |
| 7 | [Control Structures](#7-control-structures) | Conditional and looping constructs in Java. |
| 8 | [Object-Oriented Programming (OOP)](#8-object-oriented-programming-oop) | Principles like inheritance, polymorphism, etc. |
| 9 | [Error Handling](#9-error-handling) | Handling exceptions with try-catch-finally. |
| 10 | [Common Java APIs](#10-common-java-apis) | Key packages and their use in Java programming. |
| 11 | [Development Tools](#11-development-tools) | IDEs, build tools, and utilities for Java development. |
| 12 | [Real-World Use Cases](#12-real-world-use-cases) | Where and how Java is used in real applications. |
| 13 | [Getting Started with Java](#13-getting-started-with-java) | Installation, setup, and basic usage instructions. |
| 14 | [Further Reading](#14-further-reading) | Recommended books and official resources. |

---

## 1. Overview
Java is a **general-purpose**, **object-oriented**, **class-based** programming language that enables developers to build **platform-independent** applications. Java programs are compiled into **bytecode**, which is executed by the **Java Virtual Machine (JVM)**. This allows Java applications to run on any system that has a compatible JVM, embodying the principle **"Write Once, Run Anywhere"**.

---

## 2. History of Java

| Year | Milestone |
|------|-----------|
| 1991 | Started as "Oak" by James Gosling at Sun Microsystems for interactive television. |
| 1995 | Renamed to **Java** and officially released with Java 1.0. |
| 1998 | Java 2 (J2SE) released, introducing the Swing GUI toolkit, Collections Framework, etc. |
| 2004 | Java 5 introduces generics, metadata annotations, enhanced for-loop. |
| 2010 | **Oracle** acquires Sun Microsystems, becoming the official maintainer of Java. |
| 2017 | Java SE 9 introduces modules (`Project Jigsaw`). |
| 2018+ | New release cadence: major versions every 6 months (Java 11, Java 17 are LTS). |

Java has grown to become the foundation for many large-scale applications, Android development, cloud services, and more.

---

## 3. Core Features of Java

### ✦ Platform Independence
Compiled Java code (`.class`) runs on any OS with a JVM. This decouples the source code from underlying hardware or OS.

### ✦ Object-Oriented Programming
Java is based on OOP concepts: **abstraction, encapsulation, inheritance, polymorphism**.

### ✦ Strong Memory Management
Includes **automatic garbage collection** and no direct pointer manipulation, reducing memory leaks.

### ✦ Multithreading Support
Enables concurrent execution using `Thread`, `Runnable`, and advanced concurrency APIs in `java.util.concurrent`.

### ✦ Secure
Features like **bytecode verification**, **security manager**, and **exception handling** make Java suitable for secure applications.

### ✦ Rich Standard API
Prebuilt packages for **data structures, networking, file I/O, math, date/time, JDBC**, etc.

### ✦ Robust and Reliable
Java performs compile-time and runtime checks, and it handles exceptions gracefully.

---

## 4. Java Architecture

```text
[.java file] → javac → [.class bytecode] → JVM → [Native Machine Code]
```

### Components:
- **JDK (Java Development Kit)**: Compiler, debugger, tools, JRE.
- **JRE (Java Runtime Environment)**: JVM + standard class libraries.
- **JVM (Java Virtual Machine)**: Executes bytecode, provides memory management, and OS abstraction.

### JVM Internals:
- **Class Loader**: Loads classes dynamically.
- **Memory Areas**:
  - Heap (objects)
  - Stack (method frames)
  - Method Area (class definitions)
  - PC Register
- **Execution Engine**: Interpreter + JIT (Just-In-Time compiler)

---

## 5. Basic Syntax & Structure

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

- `class` defines a class.
- `main()` is the entry point.
- `System.out.println()` prints output.

---

## 6. Data Types & Variables

### Primitive Types:
| Type    | Size     | Example         |
|---------|----------|------------------|
| `int`   | 4 bytes  | `int age = 30;`  |
| `double`| 8 bytes  | `double pi = 3.14;` |
| `char`  | 2 bytes  | `char c = 'A';`  |
| `boolean`| 1 bit   | `boolean flag = true;` |

### Reference Types:
Arrays, Strings, custom objects, etc.

---

## 7. Control Structures

### If-Else
```java
if (score > 90) {
    System.out.println("Excellent");
} else {
    System.out.println("Try harder");
}
```

### Loops
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

while (condition) {
    // repeat block
}

do {
    // executes at least once
} while (condition);
```

---

## 8. Object-Oriented Programming (OOP)

### Abstraction
Hide complex logic and expose essential features:
```java
abstract class Animal {
    abstract void makeSound();
}
```

### Encapsulation
Use `private` variables + `public` methods to protect internal state.

### Inheritance
```java
class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark");
    }
}
```

### Polymorphism
```java
Animal a = new Dog();
a.makeSound(); // Bark (runtime method dispatch)
```

---

## 9. Error Handling

### Try-Catch-Finally
```java
try {
    int x = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero.");
} finally {
    System.out.println("Always executes.");
}
```

### Custom Exception
```java
class InvalidAgeException extends Exception {
    public InvalidAgeException(String msg) {
        super(msg);
    }
}
```

---

## 10. Common Java APIs

| Package         | Description                              |
|------------------|------------------------------------------|
| `java.lang`      | Core types (`String`, `Math`, `Object`)  |
| `java.util`      | Collections, dates, utilities            |
| `java.io`        | File and stream handling                 |
| `java.nio`       | Non-blocking I/O                         |
| `java.net`       | Sockets, URLs, HTTP                      |
| `java.sql`       | JDBC database access                     |
| `java.util.concurrent` | Multithreading & async APIs     |

---

## 11. Development Tools

- **IDEs**: IntelliJ IDEA, Eclipse, NetBeans
- **Build Tools**: Maven, Gradle
- **Testing**: JUnit, TestNG
- **Version Control**: Git
- **Documentation**: Javadoc

---

## 12. Real-World Use Cases

### ➤ Enterprise Applications
Java EE or Jakarta EE for enterprise-scale applications with EJBs, JSP, Servlets.

### ➤ Android Development
Core language for native Android apps (superseded by Kotlin now, but still widely supported).

### ➤ Web Backends
Spring Boot for REST APIs, authentication, databases, etc.

### ➤ Big Data
Java is used in Hadoop, Apache Kafka, Spark for large-scale data processing.

### ➤ Embedded Systems
Java ME for limited-resource devices like POS terminals, embedded sensors.

### ➤ Financial Services
Banking systems use Java for security, scalability, and reliability.

### ➤ Cloud & Microservices
Spring Cloud, Quarkus, and Micronaut frameworks for containerized deployments on Kubernetes.

---

## 13. Getting Started with Java

### Install Java:
- Download JDK from [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html) or [OpenJDK](https://jdk.java.net)

### Setup:
1. Set `JAVA_HOME`
2. Add `JAVA_HOME/bin` to system PATH
3. Test with:
```bash
java -version
javac -version
```

### Compile & Run:
```bash
javac HelloWorld.java
java HelloWorld
```

### Using IntelliJ:
- Create a project → Add class → Write code → Run using the green play button.

---

## 14. Further Reading
- [Official Java Tutorials (Oracle)](https://docs.oracle.com/javase/tutorial/)
- *Effective Java* by Joshua Bloch
- *Java Concurrency in Practice* by Brian Goetz
- [Spring Boot Documentation](https://spring.io/projects/spring-boot)

---

*Prepared by Technical Documentation Writer Pro*  
*Date: 2025-07-19*
