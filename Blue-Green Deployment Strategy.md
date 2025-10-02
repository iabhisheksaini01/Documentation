# Blue-Green Deployment Strategy

<img width="1035" height="510" alt="blue-green" src="https://github.com/user-attachments/assets/ff8767ba-2d9f-4d29-b760-cd82c3656c29" />

## Author Information

| Created by      | Created on         | Version          | Last updated On   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek Saini  |  1-10-2025        | V 1.0            |    1-10-2025   |  Prashant         |   Nikita   |    Rishab     |   Piyush |


## Table of Content

- [Overview](#overview)  
- [Workflow](#workflow)  
- [Advantages](#advantages)  
- [Challenges](#challenges)  
- [Practical Implementation Examples](#practical-implementation-examples)  
  - [Kubernetes + Ingress Controller](#1-kubernetes--ingress-controller)  
  - [AWS Elastic Beanstalk](#2-aws-elastic-beanstalk)  
  - [NGINX Reverse Proxy](#3-nginx-reverse-proxy)  
  - [Cloud Foundry / Heroku](#4-cloud-foundry--heroku)  
- [Suitable Use Cases](#suitable-use-cases)  
- [Conclusion](#conclusion)  
- [Contact Information](#contact-information)

---

## Overview

Blue-Green Deployment is a method to update applications with almost no downtime.  
It uses two environments: **Blue** and **Green**.

- **Blue**: the current live environment serving users.  
- **Green**: the environment where the new version is prepared.  

When the new version is ready, traffic is switched from Blue to Green using a load balancer or DNS.  
This makes the new version live instantly, while the old one can still be kept as backup.

---

## Workflow

1. **Two Environments**: Keep two setups – *Blue* (live for users) and *Green* (used for the new version).

2. **Deploy to Green**: Put the new application version on Green.

3. **Test Green**: Run quick checks (smoke tests) to ensure everything works fine.

4. **Switch Users**: Change the load balancer or DNS so users start using Green.

5. **Blue as Backup**: Blue is kept ready in case something goes wrong, so you can switch back fast.

6. **Update Blue**: Once Green is stable, update Blue with the new version. Blue then becomes the standby for the next release.

<img width="1600" height="1355" alt="unnamed" src="https://github.com/user-attachments/assets/2b865d52-3334-4396-8d1d-32050448e3fa" />


---

## Advantages

* **Zero Downtime**: Switching traffic is instant, so users don’t face interruptions.  
* **Easy Rollback**: If problems appear, just switch traffic back to Blue.  
* **Isolation**: New version runs separately from the live one until ready.  
* **Realistic Testing**: You can test the new version on the same type of setup as production before going live.


---

## Challenges

* **High Cost**: Needs two full environments, which doubles infrastructure use.  
* **Data Sync Issues**: Hard to keep databases or stateful services in sync.  
* **Routing Complexity**: Load balancer or DNS setup must be managed carefully.  
* **Idle Resources**: One environment sits unused most of the time.

---

## Practical Implementation Examples

### 1. **Kubernetes + Ingress Controller**
* Blue and Green are two separate `Deployment` and `Service` objects.  
* Ingress sends traffic to whichever is active.  
* Switching is done by changing a label or routing rule.  

### 2. **AWS Elastic Beanstalk**
* Built-in support for Blue-Green deployments.  
* Clone the environment, deploy the new version, test it, then swap URLs.  

### 3. **NGINX Reverse Proxy**
* Define Blue and Green as separate upstreams.  
* Change a flag or config to shift traffic between them.  

### 4. **Cloud Foundry / Heroku**
* Use HTTP routers to move traffic between app versions.  
* Rollback is as simple as routing back to the old app.

---
## Suitable Use Cases

* **High Availability Apps**: For systems that cannot afford downtime.  
* **Critical APIs**: When quick rollback and safe testing are needed.  
* **Staging to Production**: Useful for testing new versions in a production-like setup.  
* **Microservices**: Works well when services are loosely coupled and can be swapped one by one.  


---
## Conclusion

Blue-Green Deployment is a reliable way to release new versions without downtime.  
It reduces risk by keeping a backup environment ready for rollback.  
Though it needs extra infrastructure and careful routing, it’s well-suited for critical systems where stability and safety matter most.


---

## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---

## References

| **Title**                                      | **Link** |
|-----------------------------------------------|----------|
| Blue-Green Deployment Strategy – Martin Fowler | [martinfowler.com](https://martinfowler.com/bliki/BlueGreenDeployment.html) |
| NGINX Blue-Green Deployment Guide              | [nginx.com](https://docs.nginx.com/nginx/deployment-guides/blue-green-deployments/) |
| Cloud Foundry Blue-Green Deployment Example    | [docs.cloudfoundry.org](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html) |

