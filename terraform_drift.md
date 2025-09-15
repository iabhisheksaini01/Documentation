# Terraform Drift

![maxresdefault](https://github.com/user-attachments/assets/891d6557-9ef0-4a2b-9120-817ea093bd75)

---

## Author Information

| Created by      | Created on         | Version          | Last updated on   | pre Reviewer       | L0 Reviewer     | L1 Reviewer          |    L2 Reviewer    |
|-----------------|--------------------|------------------|-------------------|--------------------|-----------------|----------------------|-------------------|
| Abhishek saini  |  16-09-2025        | V 1.0            |     16-09-2025    |  Prashant          |  Nikita     |      Rishabh sharma  |   piyush upadhyay |


---

## Table of Contents

- [Introduction](#Introduction)
- [What is Drift?](#What-is-Drift)
- [Reasons for Terraform Drift](#Reasons-for-Terraform-Drift)
- [Impact of Drift](#impact-of-drift)
- [How to Detect Terraform Drift](#how-to-detect-terraform-drift)
- [Terraform Drift Management Workflow](#terraform-drift-management-workflow)
- [Best Practices for Managing Terraform Drift](#best-practices-for-managing-terraform-drift)
- [Conclusion](#Conclusion) 
- [Contact Information](#Contact-Information) 
- [References](#References)

 ---

 ## Introduction

This document explores Terraform Drift—when your code and actual infrastructure fall out of sync. You’ll learn what drift is, why it happens, the benefits of managing it, the workflow to detect and fix it, and best practices to keep your infrastructure reliable and secure.

---

## What is Drift?

Drift is when your Terraform code (desired state) and your real infrastructure (actual state) do not match. It usually happens when changes are made outside Terraform, like manual edits in the cloud console or by other tools. This mismatch can lead to issues in consistency, security, and reliability of your infrastructure.

---

## Reasons for Terraform Drift  

#### Lack of Automation  
>Drift often occurs when infrastructure changes are made manually instead of through automated pipelines. Without CI/CD in place, updates may be applied inconsistently and remain undocumented. Establishing a proper automation workflow ensures changes are tested, tracked, and deployed reliably.  

#### Urgent Hotfixes  
>During production issues, teams may introduce quick fixes directly in the cloud console. Although these changes resolve problems rapidly, they bypass Terraform’s state and lead to drift. For example, modifying a security group at midnight to address a critical bug.  

#### Insufficient Team Training  
>When team members are unfamiliar with Terraform, they may resort to manual updates in the console. These changes are invisible to Terraform, causing the desired and actual states to diverge. Adequate training and clear processes reduce this risk.  

#### Third-party Tools  
>External automation tools, such as monitoring or security systems, may update resources via AWS CLI or SDK. Since these tools do not interact with Terraform configurations, the Terraform state file becomes outdated, resulting in drift.  

---

## Impact of Drift 

| Category               | Description |
|-------------------------|-------------|
| **Security Risks**      | Drift can create weak points like open ports or misconfigured firewalls, which may allow unauthorized access and lead to data breaches. |
| **Compliance Risks**    | Untracked changes can cause violations of regulatory or industry standards, resulting in penalties, fines, or loss of trust. |
| **Performance Issues**  | Drift may reduce performance by increasing latency, lowering throughput, or even causing outages that hurt user experience. |
| **Higher Costs**        | Extra or misconfigured resources from drift can increase cloud bills and lead to resource waste. |
| **Operational Burden**  | Drift makes infrastructure harder to manage, troubleshoot, and maintain, adding complexity and effort for teams. |
| **Resource Mismatch**   | Resources may no longer fit actual application needs, leading to over-provisioning or under-provisioning. |


---

## How to Detect Terraform Drift

#### Use `terraform plan`
  >The `terraform plan` command compares your **actual infrastructure** with the **desired state** defined in your Terraform configuration. It highlights any differences and shows the changes needed to bring your infrastructure back in sync.

#### Regular Monitoring
  >Perform drift checks regularly—ideally a few times a day or at least once daily. Think of it as routine maintenance: detecting small mismatches early prevents bigger issues and keeps your infrastructure consistent and reliable.

---

## Terraform Drift Management Workflow

#### Detect Drift
  >Use `terraform plan` or cloud-native drift detection tools to compare the actual state of infrastructure with the desired state defined in Terraform.  

#### Review Differences
  >Analyze the reported mismatches to understand the impact and decide which changes should be applied.  

#### Correct Drift  
  >Apply the necessary updates via Terraform (`terraform apply`) or update configurations to align infrastructure with the desired state.  

#### Monitor Continuously
  >Set up regular drift detection checks and integrate alerts to ensure ongoing alignment between code and infrastructure.  

---

## Best Practices for Managing Terraform Drift

| Best Practice                  | Description |
|--------------------------------|-------------|
| **Apply Changes Only via Terraform** | Avoid manual edits in the cloud console. Always use Terraform to create, update, or delete resources to keep infrastructure and code in sync. |
| **Implement CI/CD Pipelines**  | Automate deployments using Continuous Integration/Continuous Deployment pipelines to ensure consistent and repeatable changes. |
| **Restrict Console Access**    | Limit direct access to cloud consoles for critical resources to prevent unauthorized or accidental changes. |
| **Document All Changes**       | Maintain clear documentation of infrastructure changes and update Terraform configurations accordingly. |
| **Regular Drift Detection**    | Schedule regular checks using `terraform plan` or other drift detection tools to catch mismatches early and fix them before they escalate. |


---

## Conclusion

Drift in Infrastructure as Code (IaC) occurs when the actual state of infrastructure diverges from its intended state, leading to risks like security vulnerabilities, compliance issues, performance problems, increased costs, operational complexity, and resource misalignment. Detecting and addressing drift using tools like Terraform's terraform plan command is crucial for maintaining a secure and efficient infrastructure.
 
***


## Contact Information

| **Name**           | **Email address**                         |
|--------------------|--------------------------------------------|
| Abhishek saini    | abhishek.saini.snaatak@mygurukulam.co |

---
 
## References

| **Source** | **Description** |
| ---------- | --------------- |
| [**Link**](https://controlmonkey.io/blog/the-definitive-guide-for-terraform-drift-detection/) | Introduction of Drift |

| [**Link**](https://blog.brainboard.co/terraform-drift-detection-how-to-monitor-and-remediate-cloud-infrastructure-drift-3e365921420#:~:text=Whenever%20the%20terraform%20plan%20command,using%20the%20terraform%20apply%20command.) | Drift Tool |
