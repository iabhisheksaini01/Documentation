# Golang Installation and Version Management Script

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  16-07-2025        | V 1.0            |     18-07-2025    |  Prashant          |  Priyanka      |      Rishabh sharma   |   piyush upadhyay |

---
![go](https://github.com/user-attachments/assets/302c1f38-bfec-4110-9d46-6b0f1007a125)

This Bash script provides an interactive utility to install or upgrade **Go (Golang)** on Ubuntu-based systems. It supports multiple methods including installation via package manager or downloading from the official tarball, and allows managing different Go versions effectively.

---

## Table of Contents

- [Prerequisites](#prerequisites)  
- [Features](#features)  
- [Supported Versions](#supported-versions)  
- [Installation Methods](#installation-methods)  
- [How It Works](#how-it-works)  
- [Usage](#usage)  
- [Setting Default Go Version](#setting-default-go-version)  
- [Verification](#verification)  
- [Troubleshooting](#troubleshooting)

---

## Prerequisites

- Ubuntu or Debian-based Linux distribution
- `sudo` privileges
- Internet connection (for tarball or APT-based installation)

---

## Features

- Install Go using APT package manager
- Install specific Go versions via official binary tarballs
- Upgrade previously installed Go versions (non-system)
- Clean removal of existing Go installation in `/usr/local/go`
- Automatically update `PATH` in `~/.profile` if required
- Version selection from supported list
- Easy to extend with more versions

---


## Supported Versions

Currently the script supports:

- Go 1.20.7  
- Go 1.21.0  
- Go 1.22.0

You can add more versions by updating the script.

---

## Installation Methods

The script supports three types of operations:

| Option | Description |
|--------|-------------|
| 1      | Install Go via system package manager (`apt`) |
| 2      | Install Go via official tarball from go.dev |
| 3      | Upgrade an existing Go installation using the tarball |

---

## How It Works

1. Prompts the user to select an operation (install/upgrade)
2. Asks for the desired Go version
3. Installs Go using the selected method
4. Ensures that `/usr/local/go/bin` is in your `PATH`
5. Displays the installed Go version at the end

---

## Usage

Run the script with Bash:

```bash
bash go_installer.sh

---
## Bash Script
install_go.sh
```bash
#!/bin/bash

echo "Select Go Operation:"
echo "1) Install via Package Manager (apt/snap)"
echo "2) Install via Tarball (official Go binary)"
echo "3) Upgrade Existing Installed Version (non-system)"
read -p "Enter choice (1-3): " method

echo
echo "Select Go version:"
echo "1) 1.20.7"
echo "2) 1.21.0"
echo "3) 1.22.0"
read -p "Enter version (1-3): " choice

case $choice in
  1) version="1.20.7" ;;
  2) version="1.21.0" ;;
  3) version="1.22.0" ;;
  *) echo "Invalid version"; exit 1 ;;
esac

install_via_package_manager() {
  echo "Installing Go via apt (may be outdated version)..."
  sudo apt update
  sudo apt install -y golang
  echo "Go installed via package manager. Check version with 'go version'."
}

install_via_tarball() {
  echo "Installing Go $version from official tarball..."

  sudo rm -rf /usr/local/go
  wget https://go.dev/dl/go${version}.linux-amd64.tar.gz -O /tmp/go${version}.linux-amd64.tar.gz
  sudo tar -C /usr/local -xzf /tmp/go${version}.linux-amd64.tar.gz

  # Add /usr/local/go/bin to PATH if not already present
  if ! grep -q '/usr/local/go/bin' <<< "$PATH"; then
    echo "export PATH=\$PATH:/usr/local/go/bin" >> ~/.profile
    echo "Added /usr/local/go/bin to PATH in ~/.profile. Please re-login or run 'source ~/.profile'"
  fi

  echo "Go $version installed from tarball."
}

upgrade_existing_version() {
  echo "Upgrading Go $version..."

  # Check if Go is installed
  if ! command -v go &> /dev/null; then
    echo "Go not found. Please install first."
    exit 1
  fi

  install_via_tarball

  echo "Go $version upgraded."
}

case $method in
  1) install_via_package_manager ;;
  2) install_via_tarball ;;
  3) upgrade_existing_version ;;
  *) echo "Invalid method selected."; exit 1 ;;
esac

echo
echo "Installed Go version:"
go version || echo "Go is not installed or not in PATH."
```
