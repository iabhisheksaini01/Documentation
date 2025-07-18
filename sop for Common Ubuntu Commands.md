
# SOP forCommon Ubuntu Commands

## Author Information

| Created by      | Created on         | Version          | Last updated ON   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  16-07-2025        | V 1.0            |     18-07-2025    |  Prashant          |  Priyanka      |      Rishabh sharma   |   piyush upadhyay |

---

##  Table of Contents

| S.No | Section                            | Description                                             |
|------|------------------------------------|---------------------------------------------------------|
| 1️⃣   | [System Update and Upgrade](#1-system-update-and-upgrade)        | Commands to update and upgrade Ubuntu packages          |
| 2️⃣   | [Install/Remove Packages](#2-installremove-packages)             | Installing and removing packages using `apt`            |
| 3️⃣   | [Search Packages](#3-search-packages)                            | Finding and viewing packages before installation        |
| 4️⃣   | [System Information](#4-system-information)                      | Get system, disk, memory, and uptime info               |
| 5️⃣   | [User Management](#5-user-management)                            | Add, remove, or modify users and groups                 |
| 6️⃣   | [Directory & File Operations](#6-directory--file-operations)     | Basic file and directory commands                       |
| 7️⃣   | [Permission & Ownership](#7-permission--ownership)               | Manage file permissions and ownership                   |
| 8️⃣   | [Networking](#8-networking)                                      | View IPs, test connectivity, and view network ports     |
| 9️⃣   | [Reboot and Shutdown](#9-reboot-and-shutdown)                    | Commands to restart or power off the system             |
| 🔟   | [File Viewing & Editing](#10-file-viewing--editing)              | Tools to view and edit files                            |
| 1️⃣1️⃣  | [Clear Cache & Logs](#11-clear-cache--logs)                     | Clear package cache and manage logs                     |                         |

---


## Objective:
To provide a detailed list of frequently used Ubuntu commands with their detailed purpose and examples, This helps users perform basic system-level tasks easily.

---

## 1 System Update and Upgrade

### Description:
Used to update the package list and upgrade all the installed packages to the latest version.

### Commands:
```bash
sudo apt update         # Updates the list of available packages
sudo apt upgrade -y     # Upgrades the installed packages
sudo apt full-upgrade   # Upgrades with dependency resolution
```

---

## 2. Install/Remove Packages

### Description:
Install, remove, and manage software using `apt`.

### Commands:
```bash
sudo apt install <package-name>      # Install package
sudo apt remove <package-name>       # Remove package
sudo apt purge <package-name>        # Remove package with config files
```

**Example:**
```bash
sudo apt install git
sudo apt remove nginx
```

---

## 3 Search Packages

### Commands:
```bash
apt search <package>
apt show <package>
```

**Example:**
```bash
apt search docker
apt show docker.io
```

---

## 4. System Information

### Commands:
```bash
uname -a                    # Kernel info
hostnamectl                 # Host info
df -h                       # Disk space
free -h                     # Memory usage
uptime                      # System uptime
```

---

## 5. User Management

### Commands:
```bash
sudo adduser <username>               # Add user
sudo userdel <username>               # Delete user
sudo usermod -aG <group> <username>   # Add user to group
id <username>                         # Show user UID, GID
```

**Example:**
```bash
sudo adduser devuser
sudo usermod -aG sudo devuser
```

---

## 6. Directory & File Operations

### Commands:
```bash
ls -l                                  # List files with details
cd /path/to/dir                        # Change directory
mkdir new_folder                       # Create directory
rm -rf folder/                         # Remove directory
touch file.txt                         # Create file
cat file.txt                           # View file content
cp source.txt dest.txt                 # Copy file
mv oldname.txt newname.txt             # Rename/move file
```

---

## 7. Permission & Ownership

###  Commands:
```bash
chmod +x script.sh                     # Add execute permission
chmod 755 file                         # Set permission
chown user:group file                  # Change owner
```

---

## 8. Networking

### Commands:
```bash
ip a                                   # IP addresses
ping google.com                        # Ping test
netstat -tuln                          # Listening ports (use `ss` in newer versions)
curl http://localhost:3000             # Curl test
```

---

## 9. Reboot and Shutdown

### Commands:
```bash
sudo reboot
sudo shutdown now
```

---

## 10. File Viewing & Editing

###  Commands:
```bash
cat file.txt           # View file
less file.txt          # View paginated
nano file.txt          # Edit file
vim file.txt           # Edit file with Vim
```

---

## 11. Clear Cache & Logs

###  Commands:
```bash
sudo apt clean                    # Clean apt cache
journalctl --vacuum-time=3d      # Remove logs older than 3 days
sudo rm -rf /var/log/*           # Remove log files (use with caution)
```

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | [abhishek.saini.snaatak@mygurukulam.co |

---

## References

| **Link**                                                                 | **Description**                                   |
|--------------------------------------------------------------------------|---------------------------------------------------|
| [Linux common commands– ](https://www.digitalocean.com/community/tutorials/linux-commands) | Document format followed from this link.          |




## 👥 Contributor
## By: Abhishek saini
