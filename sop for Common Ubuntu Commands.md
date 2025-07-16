
# SOP: Common Ubuntu Commands

## Objective:
To provide a detailed list of frequently used Ubuntu commands with their purpose, examples, and best practices. This helps users perform basic system-level tasks efficiently.

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
lsb_release -a              # Distribution info
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

### 💻 Commands:
```bash
chmod +x script.sh                     # Add execute permission
chmod 755 file                         # Set permission
chown user:group file                  # Change owner
```

---

## 8. Process & Service Management

###  Commands:
```bash
ps aux                                 # Show running processes
top / htop                             # Live process monitor
kill <pid>                             # Kill process
sudo systemctl start <service>         # Start service
sudo systemctl stop <service>          # Stop service
sudo systemctl status <service>        # Status
sudo systemctl enable <service>        # Enable at boot
```

**Example:**
```bash
sudo systemctl start nginx
sudo systemctl status redis-server
```

---

## 9. Networking

### Commands:
```bash
ip a                                   # IP addresses
ping google.com                        # Ping test
netstat -tuln                          # Listening ports (use `ss` in newer versions)
curl http://localhost:3000             # Curl test
```

---

## 10.  Reboot and Shutdown

### 💻 Commands:
```bash
sudo reboot
sudo shutdown now
```

---

## 11. File Viewing & Editing

###  Commands:
```bash
cat file.txt           # View file
less file.txt          # View paginated
nano file.txt          # Edit file
vim file.txt           # Edit file with Vim
```

---

## 12. 🧹 Clear Cache & Logs

###  Commands:
```bash
sudo apt clean                    # Clean apt cache
journalctl --vacuum-time=3d      # Remove logs older than 3 days
sudo rm -rf /var/log/*           # Remove log files (use with caution)
```

---

## Conclusion

This SOP provides a practical guide for essential commands on Ubuntu. It improves onboarding, troubleshooting, and operational consistency for team members working in DevOps, development, and operations environments.

---

## Reference

- [Ubuntu Man Pages](https://manpages.ubuntu.com/)
- `man <command>` — In-terminal manual page
- https://ubuntu.com/tutorials
