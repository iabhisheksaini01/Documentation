# SOP for Common Ubuntu Commands

## Objective
To provide a detailed list of frequently used Ubuntu commands with their descriptions, examples, and best practices. This SOP helps the users to perform basic system tasks effectively on Ubuntu systems.

---

## 1. System Information

### Description:
Commands to get kernel, hostname, memory, disk usage, and uptime information.

### Commands:
```bash
uname -a          # Show system information including kernel version
hostnamectl       # Display hostname, OS, kernel, architecture, etc.
df -h             # Show disk space usage in human-readable format
free -h           # Show memory usage in human-readable format
uptime            # Show how long the system has been running and load average
```

### Examples:
```bash
uname -a
df -h
free -h
uptime
```

---

## 2. User Management

### Description:
Manage user accounts and groups.

### Commands:
```bash
sudo adduser <username>               # Add a new user interactively
sudo userdel <username>               # Delete an existing user
sudo usermod -aG <group> <username>   # Add user to a supplementary group
id <username>                         # Display UID, GID, and groups of the user
```

### Examples:
```bash
sudo adduser devuser
sudo usermod -aG sudo devuser
id devuser
```

---

## 3. Directory & File Operations

### Description:
Create, view, move, delete, and manage files and directories.

### Commands:
```bash
ls -l                         # List files and directories with details
cd /path/to/dir               # Change current directory
mkdir new_folder              # Create a new directory
rm -rf folder/                # Remove a directory and its contents recursively
touch file.txt                # Create a new empty file
cat file.txt                  # Display contents of a file
cp source.txt dest.txt        # Copy file from source to destination
mv oldname.txt newname.txt    # Rename or move a file
```

### Examples:
```bash
mkdir test_dir
cd test_dir
touch example.txt
cat example.txt
mv example.txt sample.txt
```

---

## 4. Permission & Ownership

### Description:
Modify file permissions and ownership.

### Commands:
```bash
chmod +x script.sh            # Add execute permission to a script
chmod 755 file                # Set permission: rwxr-xr-x
chown user:group file         # Change file owner and group
```

### Examples:
```bash
chmod +x install.sh
chown ubuntu:ubuntu config.json
```

---

## 5. Networking

### Description:
View IP configuration, test connectivity, and check network services.

### Commands:
```bash
ip a                          # Display all IP addresses and network interfaces
ping <hostname>               # Check connectivity to a remote host
netstat -tuln                 # Show active listening ports (TCP/UDP)
curl http://localhost:3000    # Send HTTP request to test a local service
```

### Examples:
```bash
ip a
ping google.com
curl http://localhost:8080
```

---

## 6. Reboot and Shutdown

### Description:
Restart or shut down the machine.

### Commands:
```bash
sudo reboot                   # Reboot the system
sudo shutdown now             # Shut down the system immediately
```

### Examples:
```bash
sudo reboot
sudo shutdown now
```

---

## 7. File Viewing & Editing

### Description:
Read or modify file content using terminal editors.

### Commands:
```bash
cat file.txt                  # Display file content in terminal
less file.txt                 # View file one page at a time
nano file.txt                 # Edit file using nano (beginner friendly)
vim file.txt                  # Edit file using vim (advanced editor)
```

### Examples:
```bash
cat notes.txt
nano config.txt
vim script.sh
```

---

