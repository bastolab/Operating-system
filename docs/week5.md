
# Week 5 — Advanced Security & Monitoring

**[← Week 4](week4.md)** | **Week 5** | **[Week 6 →](week6.md)**

---

## Overview

Week 5 builds on the foundational security controls implemented in Week 4 by enabling advanced host-based security mechanisms and introducing automated monitoring and baseline validation scripts.

The focus is on enforcing Mandatory Access Control (MAC), hardening against brute-force attacks, ensuring timely security patching, and preparing structured data collection for performance analysis in Week 6.

All configuration, validation, and scripting are performed remotely via SSH to maintain a headless, production-like server environment.

---

## Objectives

* Enable and enforce Mandatory Access Control (AppArmor)
* Configure automatic security updates
* Deploy and configure fail2ban for SSH protection
* Build a security baseline verification script
* Build a remote performance monitoring script

---

## Deliverables

* MAC enforcement evidence (`aa-status`)
* Automatic update configuration and logs
* fail2ban configuration and jail status
* Fully commented scripts with execution evidence
* Generated monitoring data (CSV format)

---

## 1. Mandatory Access Control (MAC)

### 1.1 MAC Selection

**AppArmor** was selected due to:

* Native integration with Ubuntu Server
* Profile-based enforcement
* Lower complexity compared to SELinux
* Minimal performance overhead

---

### 1.2 AppArmor Status Verification

AppArmor status was verified using:

```bash
sudo aa-status
```

Evidence confirms:

* AppArmor enabled and running
* Multiple profiles loaded in **enforce** mode
* Service profiles (e.g., `nginx`) active where applicable

📸 **Screenshot to capture**
**Filename:** `week5-apparmor-status.png`

```md
![AppArmor Status](../assets/screenshots/week5/week5-apparmor-status.png)
**Figure W5-1:** AppArmor enabled with active enforcing profiles.
```

---

## 2. Automatic Security Updates

### 2.1 Installation & Configuration

Automatic security updates were enabled using `unattended-upgrades`:

```bash
sudo apt update
sudo apt install -y unattended-upgrades
```

Configuration verified in:

```text
/etc/apt/apt.conf.d/50unattended-upgrades
```

Key settings:

* Security updates **enabled**
* Non-security updates **disabled**

📸 **Screenshot to capture**
**Filename:** `week5-unattended-config.png`

```md
![Unattended Upgrades Config](../assets/screenshots/week5/week5-unattended-config.png)
**Figure W5-2:** unattended-upgrades configured for security updates only.
```

---

### 2.2 Verification Evidence

Logs verified using:

```bash
journalctl -u unattended-upgrades
```

This confirms that automatic updates are active and functioning correctly.

📸 **Screenshot to capture**
**Filename:** `week5-unattended-logs.png`

```md
![Unattended Upgrades Logs](../assets/screenshots/week5/week5-unattended-logs.png)
**Figure W5-3:** unattended-upgrades service logs confirming update activity.
```

---

## 3. fail2ban Configuration

### 3.1 Installation

fail2ban installed via APT:

```bash
sudo apt install -y fail2ban
```

---

### 3.2 Jail Configuration

Local jail configuration created:

```bash
sudo nano /etc/fail2ban/jail.local
```

**SSH Jail Configuration:**

```ini
[sshd]
enabled = true
port = ssh
maxretry = 5
bantime = 1h
findtime = 10m
```

📸 **Screenshot to capture**
**Filename:** `week5-fail2ban-jail.png`

```md
![fail2ban Jail Config](../assets/screenshots/week5/week5-fail2ban-jail.png)
**Figure W5-4:** fail2ban SSH jail configuration.
```

---

### 3.3 fail2ban Verification

fail2ban status verified using:

```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
```

Evidence includes:

* SSH jail enabled
* Failed attempt counters
* Active bans (if triggered during testing)

📸 **Screenshot to capture**
**Filename:** `week5-fail2ban-status.png`

```md
![fail2ban Status](../assets/screenshots/week5/week5-fail2ban-status.png)
**Figure W5-5:** fail2ban running with active SSH jail.
```

---

## 4. Security Baseline Verification Script

### 4.1 Script Overview

**Script location:**

```text
scripts/security-baseline.sh
```

This script validates the server’s security posture against defined requirements.

---

### 4.2 Checks Performed

* SSH configuration (root login, password authentication)
* Firewall status and rules (UFW)
* AppArmor enforcement status
* Automatic update configuration
* fail2ban service and jail state
* User accounts and sudoers configuration
* Optional kernel security parameters

---

### 4.3 Script Execution Evidence

```bash
bash scripts/security-baseline.sh
```

📸 **Screenshot to capture**
**Filename:** `week5-security-baseline-output.png`

```md
![Security Baseline Script](../assets/screenshots/week5/week5-security-baseline-output.png)
**Figure W5-6:** Security baseline verification script output.
```

---

## 5. Performance Monitoring Script

### 5.1 Script Overview

**Script location:**

```text
scripts/monitor-server.sh
```

This script collects system performance metrics and appends them to CSV files for later analysis.

---

### 5.2 Metrics Collected

* CPU usage
* Memory utilisation
* Disk I/O statistics
* Network activity
* Load averages

**Design Features:**

* Timestamped output
* Configurable sampling intervals
* Minimal system overhead

---

### 5.3 Script Execution Evidence

```bash
bash scripts/monitor-server.sh
```

📸 **Screenshot to capture**
**Filename:** `week5-monitor-script.png`

```md
![Monitoring Script Execution](../assets/screenshots/week5/week5-monitor-script.png)
**Figure W5-7:** Execution of remote monitoring script via SSH.
```

---

### 5.4 Generated Data Evidence

CSV files generated in `data/` directory:

```text
cpu_metrics.csv
memory_metrics.csv
disk_metrics.csv
network_metrics.csv
```

📸 **Screenshot to capture**
**Filename:** `week5-csv-files.png`

```md
![Monitoring CSV Files](../assets/screenshots/week5/week5-csv-files.png)
**Figure W5-8:** CSV files generated for performance analysis.
```

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

### Adjustments & Exceptions

* Firewall and fail2ban rules tuned for trusted workstation IP
* Service profiles reviewed to prevent false positives

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
* **Figure W5-3:** unattended-upgrades logs
* **Figure W5-4:** fail2ban SSH jail configuration
* **Figure W5-5:** fail2ban SSH jail status
* **Figure W5-6:** Security baseline script output
* **Figure W5-7:** Monitoring script execution
* **Figure W5-8:** Generated CSV performance data

---

**[← Week 4](week4.md)** | **Week 5** | **[Week 6 →](week6.md)**


Just say the word 👍

