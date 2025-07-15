
# ScyllaDB + Redis + Java/Maven + Go Migration + Spring Boot Setup Guide

This guide walks you through setting up the environment, installing required components, configuring ScyllaDB, running migrations, and launching the Spring Boot salary-api application.

---

## 1. System Upgrade

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 2. Java & Maven Installation

```bash
sudo apt install openjdk-17-jdk maven -y
java -version      # Verify OpenJDK 17 installation
mvn -version       # Verify Maven installation
```

---

## 3. Utility Installation: jq

```bash
sudo apt install jq -y
```

---

## 4. Redis Setup

```bash
sudo apt install redis-server -y
sudo systemctl enable --now redis-server
sudo systemctl status redis-server
redis-cli ping    # Should respond with: PONG
```
Edit `redis.conf

Open the config file:

```bash
sudo nano /etc/redis/redis.conf

```

Update these entries with your server’s private IP (example: `172.31.92.217`):

bind 172.31.92.217

protected-mode no

---

## 5. ScyllaDB Installation & Configuration

### 5.1 Add Repository & Install

```bash
sudo mkdir -p /etc/apt/keyrings

sudo gpg --homedir /tmp --no-default-keyring \
     --keyring /etc/apt/keyrings/scylladb.gpg \
     --keyserver hkp://keyserver.ubuntu.com:80 \
     --recv-keys a43e06657bac99e3

sudo wget -qO /etc/apt/sources.list.d/scylla.list \
     http://downloads.scylladb.com/deb/debian/scylla-2025.2.list

sudo apt update
sudo apt install scylla scylla-jmx -y
sudo systemctl enable --now scylla-server
sudo systemctl status scylla-server
```

### 5.2 Edit `scylla.yaml`

Open the config file:

```bash
sudo nano /etc/scylla/scylla.yaml
```

Update these entries with your server’s private IP (example: `172.31.92.217`):

```yaml
rpc_address: 172.31.92.217
listen_address: 172.31.92.217
broadcast_rpc_address: 172.31.92.217  # if present

seed_provider:
  - class_name: org.apache.cassandra.locator.SimpleSeedProvider
    parameters:
      - seeds: "172.31.92.217"

api_address: 172.31.92.217
```

Save and exit (`CTRL+O`, `ENTER`, `CTRL+X`).

### 5.3 Restart & Verify

```bash
sudo systemctl restart scylla-server
sudo systemctl status scylla-server
ss -tlnp | grep 9042    # Verify Scylla is listening on port 9042
```

---

## 6. Connecting & Managing ScyllaDB

### 6.1 Connect via `cqlsh`

```bash
cqlsh 172.31.92.217 -u scylladb -p password
```
now creating database 

CREATE KEYSPACE employee_db
WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 1};

DESCRIBE KEYSPACES;


### 6.2 Check Node Status

```bash
nodetool status
```

---

## 7. Migration Tool Installation

```bash
curl -L https://github.com/golang-migrate/migrate/releases/download/v4.15.2/migrate.linux-amd64.tar.gz | tar xvz
sudo mv migrate /usr/local/bin/
migrate -version
sudo apt install make -y
```

---

## 8. Application Setup: salary-api

### 8.1 Clone & Configure

```bash
git clone https://github.com/OT-MICROSERVICES/salary-api.git
cd salary-api

cd src/main/resources
nano application.yml    # Update DB, Scylla, Redis connection settings with your private ip

cassandra:
contact-points: 172.31.92.217

redis:
  host: 172.31.92.217

remove password from redis 

cd ../../..
```

### 8.2 Define Migrations

Edit your migration scripts and mappings:

```bash
nano migration.json  # Mapping definitions, tables, etc.
replace all content with this and in ip put your private ip
Modify the migrations.json
{
"database": "cassandra://scylladb:password@172.31.92.217:9042/employee_db"
```

### 8.3 Run Migrations

```bash
make run-migrations
```

---

## 9. Build & Launch Application

```bash
mvn clean package -DskipTests
java -jar target/salary-0.1.0-RELEASE.jar
```

---

## ✅ Verification Checklist

| Item                 | Verification Command                         | Expected Result           |
|----------------------|---------------------------------------------|---------------------------|
| Redis running        | `redis-cli ping`                             | `PONG`                    |
| Scylla listening     | `ss -tlnp | grep 9042`                       | Shows Scylla on port 9042 |
| Scylla accessible    | `cqlsh <ip>`                                 | Connects successfully     |
| Migrations applied   | `make run-migrations`                        | Runs without errors       |
| Application running  | Check application logs or HTTP endpoint     | Successful startup logs   |

---

For further assistance, please refer to the official documentation of [ScyllaDB](https://www.scylladb.com/docs/), [Redis](https://redis.io/docs/), and [Spring Boot](https://spring.io/projects/spring-boot).

---

*End of Guide.*
