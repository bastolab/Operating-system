
# Week 5 — Security Hardening & Performance Monitoring Automation

**[← Week 4](week4.md)** | **Week 5** | **[Week 6 →](week6.md)**

---

## Overview

Week 5 focuses on strengthening system security controls while implementing automated performance monitoring. Security mechanisms such as AppArmor, fail2ban, and unattended upgrades are enabled to harden the server, while lightweight monitoring scripts collect performance metrics for later analysis.

All configurations and scripts are managed remotely via SSH, maintaining a secure and headless server environment.

---

## Objectives

* Enforce Mandatory Access Control using AppArmor
* Mitigate brute-force attacks using fail2ban
* Enable automatic security updates
* Deploy automated performance monitoring scripts
* Generate structured performance data for analysis

---

## Deliverables

* AppArmor enforcement evidence
* fail2ban SSH jail configuration and status
* unattended-upgrades configuration
* Monitoring scripts and execution output
* Generated CSV performance data

---

## 1. Mandatory Access Control (AppArmor)

AppArmor was enabled to provide service-level confinement and reduce the impact of potential compromises.

📸 **Screenshot**
Filename: `week5-apparmor-statu.png`

![AppArmor status](../imagescreenshots/week5/week5-apparmor-statu.png)

**Figure W5-1:** AppArmor enforcing security profiles.

---

## 2. Automatic Security Updates

Unattended upgrades were configured to automatically install security patches.

📸 **Screenshot**
Filename: `week5-unattended-config.png`

![Unattended upgrades configuration](../imagescreenshots/week5/week5-unattended-config.png)

**Figure W5-2:** unattended-upgrades configuration for automatic security updates.

---

## 3. Intrusion Prevention with fail2ban

fail2ban was configured to protect SSH against brute-force attacks.

### 3.1 SSH Jail Configuration

📸 **Screenshot**
Filename: `week5-fail2ban-jail.png`

![fail2ban jail configuration](../imagescreenshots/week5/week5-fail2ban-jail.png)

**Figure W5-3:** fail2ban SSH jail configuration.

---

### 3.2 Jail Status Verification

📸 **Screenshot**
Filename: `week5-fail2ban-status.png`

![fail2ban status](../imagescreenshots/week5/week5-fail2ban-status.png)

**Figure W5-4:** Active fail2ban SSH jail protecting the server.

---

## 4. Security Baseline Validation

A security baseline script was executed to verify the applied hardening measures.

📸 **Screenshot**
Filename: `week5-security-baseline-output.png`

![Security baseline output](../imagescreenshots/week5/week5-security-baseline-output.png)

**Figure W5-5:** Output of security baseline verification script.

---

## 5. Performance Monitoring Automation

### 5.1 Monitoring Script Deployment

Custom scripts were deployed to automate performance metric collection with minimal system impact.

📸 **Screenshot**
Filename: `week5-monitor-script.png`

![Monitoring script execution](../imagescreenshots/week5/week5-monitor-script.png)

**Figure W5-6:** Automated monitoring script collecting performance metrics.

---

### 5.2 Privilege Configuration

Sudo permissions were configured to allow controlled execution of monitoring tasks.

📸 **Screenshot**
Filename: `week5-sudoers-config.png`

![Sudoers configuration](../imagescreenshots/week5/week5-sudoers-config.png)

**Figure W5-7:** Least-privilege sudo configuration for monitoring scripts.

---

### 5.3 Generated Data Evidence

CSV files generated in the `data/` directory:

* `cpu_metrics.csv`
* `memory_metrics.csv`
* `disk_metrics.csv`
* `network_metrics.csv`




**Figure W5-8:** CSV files generated for performance analysis.

---

## Reflection (Week 5)

### Security Enhancements

* AppArmor enforces service-level confinement
* fail2ban mitigates brute-force SSH attacks
* Automatic updates reduce the vulnerability window

---

### Performance Considerations

* AppArmor overhead remains minimal and acceptable
* Monitoring scripts are lightweight and non-intrusive
* Update scheduling avoids peak workload hours

---

### Adjustments & Exceptions

* Firewall and fail2ban rules tuned for trusted workstation IP
* AppArmor profiles reviewed to prevent false positives

---

## Preparation for Week 6

* Define workload durations and sampling intervals
* Validate monitoring scripts under idle and load conditions
* Confirm data structure for analysis and visualisation
* Begin controlled performance testing

---

## Image Caption Reference (Quick Copy)

* **Figure W5-1:** AppArmor enforcing profiles
* **Figure W5-2:** unattended-upgrades configuration
* **Figure W5-3:** fail2ban SSH jail configuration
* **Figure W5-4:** fail2ban SSH jail status
* **Figure W5-5:** Security baseline script output
* **Figure W5-6:** Monitoring script execution
* **Figure W5-7:** Least-privilege sudo configuration
* **Figure W5-8:** Generated CSV performance data

---

**[← Week 4](week4.md)** | **Week 5** | **[Week 6 →](week6.md)**
