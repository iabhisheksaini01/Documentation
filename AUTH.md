# Documentation: VCS Authentication


<p align="center">
  <img src="https://github.com/user-attachments/assets/e88f0394-5c5d-4694-b710-113073498a60" alt="DNS Security" width="550" height="450" />
</p>



## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  28-07-2025        | V 1.0            |       |  Prashant          |  -      |     -   |   - |

---

## Table of Contents  
1. [Introduction](#introduction)  
2. [Why Authentication?](#why-authentication)  
3. [Authentication Strategies](#authentication-strategies)  
   - [SSH Key-Based Authentication](#ssh-key-based-authentication)  
   - [OAuth 2.0 / OpenID Connect](#oauth-20--openid-connect)  
   - [Personal Access Tokens (PATs)](#personal-access-tokens-pats)  
   - [Username/Password (Basic Auth)](#usernamepassword-basic-auth)  
   - [Two-Factor Authentication (2FA)](#two-factor-authentication-2fa)  
4. [Comparison Table](#comparison-table)  
5. [Advantages & Disadvantages](#advantages--disadvantages)  
6. [Best Practices](#best-practices)  
7. [Conclusion](#conclusion)  
8. [Contact Information](#contact-information)  
9. [References](#references)  

---

## Introduction  
Authentication is an important part of keeping your Version Control System (VCS) secure. It makes sure that only the right people can access and make changes to your code. This document explains easy ways to protect access to VCS platforms like GitHub, GitLab, and Bitbucket. It also compares different methods of authentication such as passwords, SSH keys, personal access tokens, and Single Sign-On (SSO), to help you choose the best and safest option.

---

## Why Authentication?  
- Verifies the identity of users before granting access.  
- Prevents unauthorized users from viewing or modifying code.  
- Ensures compliance with organizational security policies.  
- Protects code and data from potential security threats.  
- Enables tracking of user actions and code changes for accountability.

---

## Authentication Strategies  


### SSH Key-Based Authentication
- Uses a pair of keys (public and private) to prove who you are.  
- Often used when working with Git over SSH.  
- Example command: `ssh-keygen -t ed25519`.

### OAuth 2.0 / OpenID Connect
- Lets you log in using accounts like Google or GitHub.  
- Uses special tokens to check your identity.  
- Good for logging into websites.

### Personal Access Tokens (PATs)
- A safer way to use tokens instead of passwords.  
- You can limit what these tokens can do (like only read code).  
- Example: GitHub Personal Access Tokens.

### Username/Password (Basic Auth)
- Old method using username and password.  
- Not very safe, so it needs extra security like HTTPS.  

### Two-Factor Authentication (2FA)
- Adds a second step to log in (like a code from your phone).  
- Recommended by most platforms for better security.  
- Protects your account even if your password is stolen.


---

## Comparison Table  

| Method                     |  Security       | Ease of Use       | When to Use                  | Extra Info                    |
|----------------------------|-----------------|-----------------|------------------------------|------------------------------|
| SSH Key-Based Authentication | Very Safe       | Needs Setup     | For Git using SSH            | Uses keys instead of passwords |
| OAuth 2.0 / OpenID Connect  | Safe            | Very Easy       | Login with Google or GitHub  | Uses tokens to check identity  |
| Personal Access Tokens (PATs) | Very Safe       | Medium          | For API or scripts           | Tokens can limit access        |
| Username/Password (Basic Auth) | Less Safe       | Very Easy       | Older systems or simple use  | Should use HTTPS for security  |
| Two-Factor Authentication (2FA) | Very Safe       | Medium          | Add extra protection to logins| Adds a code or key on login    |

---
## Advantages & Disadvantages

| Authentication Method          | Advantages                              | Disadvantages                         |
|-------------------------------|---------------------------------------|-------------------------------------|
| **SSH Keys**                   | Very secure, no risk of password stealing | Need to manage and keep track of keys |
| **OAuth 2.0**                  | Easy login using trusted accounts (Google, GitHub) | Depends on external services working properly |
| **Personal Access Tokens (PATs)** | Can control exactly what the token can do | Must keep tokens safe and private     |
| **Basic Authentication (Username/Password)** | Easy to set up and use                 | Easy to attack if no extra protections |
| **Two-Factor Authentication (2FA)** | Adds strong extra security to accounts | Needs extra setup; can be tricky if device lost |

---

## Best Practices  

1. Use **SSH keys** or **OAuth** instead of passwords when possible.  
2. Always **enable 2FA** for all users.  
3. Change your **tokens and keys regularly**.  
4. Use **short-lived tokens** for OAuth to reduce risk.  
5. Keep track of all login attempts by checking **audit logs**.
---

## Conclusion  

There are many ways to authenticate users, like SSH keys, OAuth, and Personal Access Tokens (PATs). To keep our project safe, we will require **Two-Factor Authentication (2FA)** for all team members and contributors.

We will set up 2FA on GitHub using apps like Google Authenticator or Authy, or with hardware security keys. This way, even if passwords are stolen, access to our repositories will stay secure.

---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References  

| Title                          | Link                                                                 |  
|--------------------------------|----------------------------------------------------------------------|  
| GitHub PAT Documentation | [Visit](https://docs.github.com/en/authentication)       |  
| GitHub 2FA Guide | [Visit](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa) |  
| OAuth 2.0 RFC | [Visit](https://tools.ietf.org/html/rfc6749) |

---
