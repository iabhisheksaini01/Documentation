# Python Installation Automation Script

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  16-07-2025        | V 1.0            |     18-07-2025    |  Prashant          |  Priyanka      |      Rishabh sharma   |   piyush upadhyay |

---


![Python Logo](https://www.python.org/static/community_logos/python-logo.png)

## A Bash script to automate Python installation on Ubuntu systems using two methods:

- Package Manager (via APT + deadsnakes PPA)
- Tarball (from source using `make altinstall`)

######     It also configures and manages multiple Python versions using `update-alternatives`.

---

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Bash Script](#bash-script)
- [Basic Usage](#basic-usage)
- [Supported Python Versions](#supported-python-versions)

---

## Introduction

Managing multiple Python versions is essential for many developers, especially when working with legacy applications or trying new versions. This script provides a simplified interface to install Python via:

- APT-based package manager (`ppa:deadsnakes/ppa`)
- Source tarball (from [python.org](https://www.python.org/ftp/python/))

It also registers installed versions with `update-alternatives`, letting you switch defaults easily.

---

## Features

- Install Python via APT or Tarball (source build)
- Supports Python versions 3.8 to 3.12
- Automatically registers all installed `python3.x` versions
- Select default version interactively
- Safe system-wide installation (no override of system Python)

---

## Prerequisites

Make sure your system has the following:

- Ubuntu 20.04/22.04 or equivalent
- `sudo` access
- `build-essential`, `wget`, `curl`, and necessary Python build dependencies

---

## Bash Script
 install_python.sh
```bash
#!/bin/bash

echo "Select Python Installation Method:"
echo "1) Package Manager (via apt and deadsnakes PPA)"
echo "2) Tarball (build from source)"
read -p "Enter method (1 or 2): " method

echo
echo "Select Python version to install:"
echo "1) 3.8"
echo "2) 3.9"
echo "3) 3.10"
echo "4) 3.11"
echo "5) 3.12"
read -p "Enter version choice (1-5): " choice

case $choice in
  1) version=3.8 ;;
  2) version=3.9 ;;
  3) version=3.10 ;;
  4) version=3.11 ;;
  5) version=3.12 ;;
  *) echo "Invalid version choice"; exit 1 ;;
esac

if [[ $method == 1 ]]; then
  echo
  echo "Installing Python $version using apt package manager..."

  sudo apt update
  sudo apt install -y software-properties-common
  sudo add-apt-repository -y ppa:deadsnakes/ppa
  sudo apt update
  sudo apt install -y python$version

  installed_path="/usr/bin/python$version"

elif [[ $method == 2 ]]; then
  echo
  echo "Installing Python $version from source (tarball)..."

  sudo apt update
  sudo apt install -y wget build-essential zlib1g-dev \
    libncurses5-dev libgdbm-dev libnss3-dev libssl-dev \
    libreadline-dev libffi-dev curl libbz2-dev

  cd /usr/src
  sudo wget https://www.python.org/ftp/python/$version/Python-$version.tgz
  sudo tar -xf Python-$version.tgz
  cd Python-$version

  sudo ./configure --enable-optimizations
  sudo make -j$(nproc)
  sudo make altinstall

  installed_path="/usr/local/bin/python$version"
else
  echo "Invalid installation method selected."
  exit 1
fi

echo
echo "Registering all Python versions with update-alternatives..."

# Auto-register all python3.x versions
for bin in /usr/bin/python3.[0-9] /usr/local/bin/python3.[0-9]; do
  [[ -x "$bin" ]] || continue
  ver=$($bin --version 2>/dev/null | awk '{print $2}')
  prio=$((100 + ${ver##*.}))
  echo " - Registering $bin with priority $prio"
  sudo update-alternatives --install /usr/local/bin/python3 python3 "$bin" "$prio"
done

echo
echo "Do you want to select the default python3 version now?"
read -p "Enter y/n: " change_default

if [[ $change_default == "y" || $change_default == "Y" ]]; then
  sudo update-alternatives --config python3
fi

echo
echo "Installed Python versions available via alternatives:"
sudo update-alternatives --display python3

echo
echo "Current default python3 version: $(python3 --version)"
```
---
## Basic Usage

```bash
chmod +x install_python.sh
```
- Grants execute permission to the script

---
```bash
./install_python.sh
```
- This installs selected Python version via Package Manager or Tarball
- Also registers the version using `update-alternatives`

---

## Supported Python Versions

| Python Version | Status     |
|----------------|------------|
| 3.8+        | Supported  |


---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| **Link**                                                                 | **Description**                                   |
|--------------------------------------------------------------------------|---------------------------------------------------|
| [Python installation guide– ](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu) | Document format followed from this link.          |

