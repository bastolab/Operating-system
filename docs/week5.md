

# Week 5 — Security Hardening & Monitoring Automation

**[← Week 4](week4.md)** | **Week 5** | **[Week 6 →](week6.md)**

---

## Overview

Week 5 focuses on strengthening the server security baseline while introducing lightweight monitoring automation. Mandatory Access Control (AppArmor), intrusion prevention (fail2ban), and automatic security updates are enabled. Custom scripts are deployed to collect performance metrics in preparation for controlled testing in Week 6.

---

## Objectives

* Enforce Mandatory Access Control
* Protect SSH from brute-force attacks
* Enable unattended security updates
* Deploy monitoring scripts for performance data
* Generate structured CSV output for analysis

---

## Deliverables

* AppArmor enforcement evidence
* fail2ban configuration and status
* unattended-upgrades configuration
* Monitoring script execution
* Generated CSV performance data

---

## 1. Mandatory Access Control (AppArmor)

📸 **Screenshot**
**Filename:** `week5-apparmor-statu.png`

```md
![AppArmor Status](../imagescreenshots/week5/week5-apparmor-statu.png)
```

**Figure W5-1:** AppArmor enforcing security profiles.

---

## 2. Automatic Security Updates

📸 **Screenshot**
**Filename:** `week5-unattended-config.png`

```md
![Unattended Upgrades Configuration](../imagescreenshots/week5/week5-unattended-config.png)
```

**Figure W5-2:** unattended-upgrades configuration.

---

## 3. Intrusion Prevention (fail2ban)

### 3.1 SSH Jail Configuration

📸 **Screenshot**
**Filename:** `week5-fail2ban-jail.png`

```md
![fail2ban SSH Jail](../imagescreenshots/week5/week5-fail2ban-jail.png)
```

**Figure W5-3:** fail2ban SSH jail configuration.

---

### 3.2 fail2ban Status

📸 **Screenshot**
**Filename:** `week5-fail2ban-status.png`

```md
![fail2ban Status](../imagescreenshots/week5/week5-fail2ban-status.png)
```

**Figure W5-4:** Active fail2ban service protecting SSH.

---

## 4. Security Baseline Script

📸 **Screenshot**
**Filename:** `week5-security-baseline-output.png`

```md
![Security Baseline Output](../imagescreenshots/week5/week5-security-baseline-output.png)
```

**Figure W5-5:** Security baseline verification output.

---

## 5. Monitoring Automation

### 5.1 Monitoring Script Execution

📸 **Screenshot**
**Filename:** `week5-monitor-script.png`

```md
![Monitoring Script Execution](../imagescreenshots/week5/week5-monitor-script.png)
```

**Figure W5-6:** Performance monitoring script execution.

---

### 5.2 Privilege Control Verification

📸 **Screenshot**
**Filename:** `week5-sudoers-config.png`

```md
![Sudoers Configuration](../imagescreenshots/week5/week5-sudoers-config.png)
```

**Figure W5-7:** Least-privilege sudo configuration.

---

### 5.3 Generated Data Evidence

CSV files generated in the `data/` directory:

```text
cpu_metrics.csv
memory_metrics.csv
disk_metrics.csv
network_metrics.csv
```

📸 **Screenshot**
**Filename:** `week5-csv-files.png`

```md
![Monitoring CSV Files](../imagescreenshots/week5/week5-csv-files.png)
```

**Figure W5-8:** CSV files generated for performance analysis.

---

## Reflection (Week 5)

### Security Enhancements

* AppArmor enforces service-level confinement
* fail2ban mitigates brute-force SSH attacks
* Automatic updates reduce vulnerability window

### Performance Considerations

* AppArmor overhead minimal and acceptable
* Monitoring scripts designed for low impact
* Update scheduling avoids peak workload hours

---

## Preparation for Week 6

* Define workload durations and sampling intervals
* Validate monitoring scripts under idle and load conditions
* Confirm data structure for analysis and visualisation
* Begin controlled performance testing

---

## Image Caption Reference

* **Figure W5-1:** AppArmor enforcing profiles
* **Figure W5-2:** unattended-upgrades configuration
* **Figure W5-3:** fail2ban SSH jail configuration
* **Figure W5-4:** fail2ban SSH jail status
* **Figure W5-5:** Security baseline script output
* **Figure W5-6:** Monitoring script execution
* **Figure W5-7:** Sudoers least-privilege configuration
* **Figure W5-8:** Generated CSV performance data

---

**[← Week 4](week4.md)** | **Week 5** | **[Week 6 →](week6.md)**
