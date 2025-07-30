

# DNS Documentation
<img src="https://github.com/user-attachments/assets/84b5bcaa-b00f-476f-98cd-fe536b2e660a" alt="maxresdefault" width="550" />

---

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  28-07-2025        | V 1.0            |     29-07-2025    |  Prashant          |  -      |     -   |   - |

---
  
  ## Table of Content
- [Introduction](#introduction)
- [Why DNS ](#why-dns)
- [What is DNS ](#what-is-dns)
- [Types of records](#types-of-records)
- [How it is work ](#how-it-is-work)
- [How to get domain ](#how-to-get-domain)
- [Different DNS provider](#different-dns-provider)
- [Comparision between DNS providers](#comparision-between-dns-providers)
- [Contact information](#contact-information)
- [References](#references)

---

## Introduction
DNS (Domain Name System) is like the internet’s phone book. It helps you find websites by changing easy names (like www.google.com) into numbers (like 192.0.2.1) that computers understand. Without DNS, we would have to remember these numbers to open websites.

---

## What is DNS
DNS is a system that helps your computer find websites. When you type a website name like "google.com" in your browser, DNS finds the number (IP address) of that website. Then your browser uses that number to open the website. DNS servers are special computers that do this work.

---

## Why DNS
Without DNS, we would need to remember the number (IP address) of every website we want to visit. That would be hard and confusing. DNS makes it easy by letting us use simple names instead of numbers.

---

## Types of records

 - **A (Address) Record:** Maps a domain name to an IPv4 address.

 - **AAAA (IPv6 Address) Record:** Maps a domain name to an IPv6 address

 - **CNAME (Canonical Name) Record:** Maps a domain name (alias) to another domain name.

 - **MX (Mail Exchange) Record:** Directs email to mail servers for a domain.

 - **TXT (Text) Record:** Provides arbitrary text data for a domain. 

 - **SOA (Start of Authority) Record:** Contains administrative information about the domain.

---

## How it is work 

<img width="1164" height="850" alt="dns-lookup" src="https://github.com/user-attachments/assets/14f0d3f8-e71e-4035-8cb8-cdcd29ce9943" />


### DNS Recursor (or Resolver): 
This is like a "helper" that looks up the website address for you. When you want to visit a website, it asks other servers to find the correct IP address that leads to the website.

### Root Nameservers: 
These are the starting points of the DNS system. They help by pointing the resolver to the right type of server based on the website’s domain (like ".com", ".org", etc.).

### TLD Nameservers :
These servers manage the domain extensions like ".com", ".org", and so on. They tell the resolver where to find the next server that knows the website’s exact IP address.

### Authoritative Nameservers:
These are the "final answer" servers. They have the exact IP address for the website you're looking for. There are two types:

    Master (Primary): The main server that holds the original IP records.
    Slave (Secondary): A backup server that has a copy of the information in case the master server fails.

---

## How to get domain 

**For detailed information How to get Domain and how to use Domnin please refer to the following resources**
| Link         | Description         |
|--------------|------------------------|
| [Domain](123) |POC of Domain name system.| 

---

## Different DNS provider 

| DNS Providers       | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| Namecheap           | Easy-to-use DNS management, includes free DNS with domain registration.     |
| Amazon Route 53     | Good for complex setups, like apps on Amazon Web Services.                  |
| Google Public DNS   | Very fast, free, and trusted.                                               |
| GoDaddy             | Popular for domain registration and DNS management, with additional services like website hosting and email. |

---

## Comparision between DNS providers

| DNS Providers       | Key Features                                                                 | Speed  | Security           | Pricing                                                              |
|---------------------|-------------------------------------------------------------------------------|--------|---------------------|----------------------------------------------------------------------|
| **Namecheap**        | Easy-to-use interface, free DNS with domains, supports dynamic DNS, great support | High   | DDoS protection      | **Free DNS with domain; Premium DNS available at affordable pricing** |
| Google Public DNS   | Fast, low-latency DNS                                                         | High   | Basic (no advanced security features) | Free                                                                |
| Amazon Route 53     | Scalable, integrates with AWS, advanced routing policies                      | High   | DDoS protection      | Pay-as-you-go (based on queries and services used)                   |
| GoDaddy             | Domain registration and DNS, integrated with hosting services                 | Medium | DDoS protection      | Paid (pricing depends on domain and hosting plan)                    |

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References
| Description           | Link                                                                 |
|------------------------|----------------------------------------------------------------------|
| Introducing DNS        | [What is DNS – AWS](https://aws.amazon.com/route53/what-is-dns/)     |
| Working of DNS         | [How DNS Works – YouTube](https://youtu.be/vhfRArT11jc?si=3cYjikGF-gLjLbrf) |
| DNS Provider   | [Namecheap DNS](https://www.namecheap.com/domains/dns/)              |
