# Standard Operating Procedure (SOP): Using `make` Build Automation Tool

## 1. Purpose
This document outlines the standard procedures for using the `make` build automation tool to compile and manage software projects efficiently.

## 2. Scope
This SOP applies to:
- Software developers
- Build engineers
- DevOps personnel
- Anyone responsible for project builds in Unix/Linux environments

## 3. Prerequisites
- GNU Make installed (typically `make` package)
- Basic understanding of compilation processes
- Familiarity with command line interface
- Project source code with a `Makefile`

## 4. Definitions
- **Makefile**: A file containing rules that define how to build the project
- **Target**: A file to be generated or an action to be performed
- **Prerequisite**: A file or action required before a target can be built
- **Recipe**: The commands needed to build the target

## 5. Procedures

### 5.1 Creating a Basic Makefile
```make
# Sample Makefile structure
target: prerequisites
	recipe
	...
