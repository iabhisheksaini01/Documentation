

# DNS Documentation
<img src="https://github.com/user-attachments/assets/84b5bcaa-b00f-476f-98cd-fe536b2e660a" alt="maxresdefault" width="550" />

---

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  28-07-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |

---
  
  ## Table of Content
- [Introduction](#introduction)
- [Why DNS ](#why-dns)
- [What is DNS ](#what-is-dns)
- [Types of records](#types-of-records)
- [How DNS works ](#how-dns-works)
- [ How To Get Domain](#how-to-get-domain)
- [Different DNS provider](#different-dns-provider)
- [DNS Providers Comparison](#dns-providers-comparison)
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

| DNS Record Type | Description                                    |
|-----------------|------------------------------------------------|
| A               | Maps a domain to an IPv4 address.              |
| AAAA            | Maps a domain to an IPv6 address.              |
| CNAME           | Alias for another domain name.                  |
| MX              | Specifies mail servers for email delivery.     |
| TXT             | Holds text information, often for verification or security. |
| NS              | Delegates a subdomain to a set of name servers.|
| SOA             | Contains administrative info about the domain. |
| PTR             | Maps an IP address to a domain name (reverse DNS). |
| SRV             | Defines location of servers for specific services. |
| SPF             | Specifies allowed mail servers to prevent spam (often in TXT). |


---
## How DNS Works

When you type a website name (like `example.com`) in your browser, DNS helps find the website’s address so your computer can connect to it. This happens in several steps with different servers:

<img width="1164" height="850" alt="dns-lookup" src="https://github.com/user-attachments/assets/14f0d3f8-e71e-4035-8cb8-cdcd29ce9943" />

### DNS Resolver  
This is like a helper that looks up the website address for you. It first checks if it already knows the answer. If not, it asks other servers to find the right address.

### Root Nameservers  
These are the first servers the resolver asks. They don’t have the exact address but tell the resolver which servers handle domain endings like ".com" or ".org".

### TLD Nameservers  
These servers handle the domain endings and tell the resolver where to find the exact server that knows the website’s address.

### Authoritative Nameservers  
These servers have the exact address of the website. They give the final answer to the resolver.

- **Primary (Master):** The main server that keeps the original website address.  
- **Secondary (Slave):** Backup servers that keep a copy in case the main one doesn’t work.

---

### Note:

- The resolver saves answers it finds for some time to help next requests faster.  
- The resolver can either do all the asking itself or ask you to check some servers step-by-step.  
- Authoritative servers can give different kinds of info like the website’s address, mail server, or verification details.


---

## How To Get Domain

**For detailed information How to get Domain and how to use Domnin please refer to the following resources**
| Link         | Description         |
|--------------|------------------------|
| [Domain](123) |POC of Domain name system.| 

---
## Different DNS Provider

| DNS Providers       | Description                                                     |
|---------------------|-----------------------------------------------------------------|
| Namecheap           | Easy to use and gives free DNS when you buy a domain.           |
| Amazon Route 53     | Good for complicated setups, especially with Amazon services.   |
| Google Public DNS   | Fast, free, and reliable DNS service.                           |
| GoDaddy             | Popular for buying domains and managing DNS, plus extra services like hosting and email. |


---

## DNS Providers Comparison

| Provider      | Speed             | Security (DNSSEC)                        | Pricing                   | Complexity                      |
|---------------|-------------------|------------------------------------------|----------------------------|----------------------------------|
| **Cloudflare**| Fast              | Supports DNSSEC for strong protection    | Free DNS service           | Very easy to use and set up     |
| **Google DNS**| Fast              | DNSSEC supported                         | Paid (based on usage)      | Requires GCP knowledge          |
| **AWS Route 53**| Fast            | High security with DNSSEC and failover   | Paid (per query/record)    | Needs AWS setup knowledge       |
| **GoDaddy**   | Slower than others| No DNSSEC (less secure)                  | Free with domain           | Beginner-friendly interface     |
| **Namecheap** | Moderate speed    | Basic DNSSEC available                   | Free with domain           | Simple and clean interface      |



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
