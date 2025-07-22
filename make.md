# SOP: Make Build Tool - Installation

## Author Information

| Created by      | Created on         | Version          | Last updated ON   | pre Reviewer       | L0 Reviewer     | L1 Reviewer        | L2 Reviewer       |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|--------------------|-------------------|
| Abhishek Saini  | 21-07-2025         | V 1.0            | 21-07-2025        | Prashant           | Priyanka        | Rishabh Sharma     | Piyush Upadhyay   |

---

## 1. Objective

The purpose of this SOP is to define a standardized procedure to:

- Install the `make` build tool
- Ensure it is ready for use in build automation tasks

---

##  2. Prerequisites

- Operating System: Ubuntu/Debian-based Linux
- User must have `sudo` privileges

---

## 3. Step-by-Step Installation Guide

###  Step 1: Update System Packages

```bash
sudo apt update
```

### 🔹 Step 2: Install Make (and essential build tools)

```bash
sudo apt install build-essential -y
```

*Note:* `build-essential` includes `make`, `gcc`, and other compilation tools.

---

## ✅ 4. Acceptance Criteria

After installation, validate that `make` is correctly installed and functional:

| Checkpoint                      | Command                           | Expected Output                                    |
|---------------------------------|-----------------------------------|----------------------------------------------------|
| Verify make version             | `make --version`                  | Displays installed make version (e.g. GNU Make 4.x)|
| Check make binary location      | `which make`                      | Should return `/usr/bin/make`                     |
| Compile basic Makefile example  | See below sample test             | Should build `hello` program successfully         |

---

## 🧪 5. Functional Test (Simple Makefile Example)

### Create test files:

#### 🔸 hello.c

```c
#include <stdio.h>
int main() {
    printf("Hello, Make!\n");
    return 0;
}
```

#### 🔸 Makefile

```makefile
all:
	gcc -o hello hello.c
```

### Run make:

```bash
make
```

### Run the output:

```bash
./hello
```

### Expected:

```text
Hello, Make!
```

---

## 🧼 6. Cleanup (Optional)

```bash
rm hello hello.c Makefile
```

---

## 📝 7. Notes

- `make` does not compile code by itself; it automates the compilation by reading instructions from a `Makefile`.
- Useful in C/C++ projects and even in DevOps automation pipelines.
