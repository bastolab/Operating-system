
# Week 2 — Security Planning & Testing Methodology

**[Home](../README.md)** | **[Week 1](week1-system-planning.md)** | **[Week 3 →](week3-application-selection.md)**

---

## Overview

This week focuses on designing a comprehensive performance testing methodology and establishing a security baseline for a Linux server deployment. The emphasis is on planning before implementation—defining measurable metrics, evidence collection methods, and security controls using a defense-in-depth approach.

---

## Objectives

* Design a remote performance monitoring strategy
* Build a complete security configuration checklist
* Develop a threat model with defined risks and mitigations

---

## Deliverables

* Performance testing plan (metrics, tools, intervals, automation)
* Security configuration checklist (SSH, firewall, MAC, updates, users)
* Threat model with prioritized mitigations

---

## 1. Performance Testing Plan

### 1.1 Remote Monitoring Methodology

**Approach**

* All monitoring conducted remotely via SSH from the workstation
* Standard Linux command-line utilities only
* Metrics captured at fixed intervals (baseline and load)
* Evidence includes terminal output, logs, and screenshots

**Remote Execution Example**

```bash
ssh user@server "vmstat 5 5"
```

📸 **Screenshot to capture:**
**Filename:** `week2-ssh-remote-vmstat.png`
**Shows:** SSH command + vmstat output

```md
![Remote monitoring via SSH](../assets/screenshots/week2/week2-ssh-remote-vmstat.png)
**Figure W2-1:** Remote execution of vmstat via SSH from workstation.
```

---

### 1.2 Planned Metrics

| Resource  | Metrics                   |
| --------- | ------------------------- |
| CPU       | Utilization, load average |
| Memory    | Free/used RAM, swap       |
| Disk      | Throughput, latency       |
| Network   | Throughput, ports         |
| Processes | Responsiveness            |

---

### 1.3 Monitoring Tools & Commands

#### System Information

```bash
uname -a
```

📸 **Filename:** `week2-uname.png`
**Figure W2-2:** Kernel version and system architecture using uname.

---

#### CPU Monitoring

```bash
top
mpstat 1 5
```

📸 **Filename:** `week2-top-cpu.png`
**Figure W2-3:** CPU utilization observed using top.

---

#### Memory Monitoring

```bash
free -h
vmstat 1 5
```

📸 **Filename:** `week2-memory-vmstat.png`
**Figure W2-4:** Memory and swap statistics during baseline state.

---

#### Disk Performance

```bash
iostat -x 1 5
df -h
```

📸 **Filename:** `week2-iostat.png`
**Figure W2-5:** Disk I/O performance baseline using iostat.

---

#### Network Monitoring

```bash
ss -tulpn
iftop -t -s 5
```

📸 **Filename:** `week2-network-ports.png`
**Figure W2-6:** Listening ports and active services.

---

---

## 2. Security Configuration Checklist

### 2.1 SSH Hardening

Planned configuration for `/etc/ssh/sshd_config`:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers <admin-user>
ClientAliveInterval 300
ClientAliveCountMax 2
X11Forwarding no
```

📸 **Filename:** `week2-sshd-config.png`
**Figure W2-7:** Planned SSH hardening settings in sshd_config.

---

### 2.2 Firewall Configuration (UFW)

Planned firewall policy:

```bash
ufw default deny incoming
ufw allow from 192.168.56.102 to any port 22 proto tcp
ufw enable
```

📸 **Filename:** `week2-ufw-plan.png`
**Figure W2-8:** Planned UFW rules restricting SSH access to workstation.

---

### 2.3 Mandatory Access Control (MAC)

* AppArmor selected (Ubuntu default)
* Enforced mode planned
* Profiles to be applied to SSH and server services

📸 **Filename:** `week2-apparmor-plan.png`
**Figure W2-9:** AppArmor status and planned enforcement.

---

### 2.4 Automatic Updates

* `unattended-upgrades` enabled
* Security updates only
* Daily execution planned

📸 **Filename:** `week2-unattended-upgrades.png`
**Figure W2-10:** Planned unattended-upgrades configuration.

---

### 2.5 User Privilege Management

* Non-root admin user
* Least-privilege sudo
* No passwordless sudo

📸 **Filename:** `week2-user-plan.png`
**Figure W2-11:** Planned non-root administrative user configuration.

---

## 3. Threat Model

### Threat 1: Unauthorized SSH Access

**Risk:** High

Mitigations:

* Key-based authentication
* Firewall IP restriction
* fail2ban deployment
* Log monitoring

📸 **Filename:** `week2-threat-ssh.png`
**Figure W2-12:** SSH threat and mitigation mapping.

---

### Threat 2: Privilege Escalation

**Risk:** Medium–High

Mitigations:

* AppArmor enforcement
* Least-privilege sudo
* Automatic updates
* Lynis audits

📸 **Filename:** `week2-threat-privilege.png`
**Figure W2-13:** Privilege escalation mitigation strategy.

---

### Threat 3: Service Exploitation

**Risk:** Medium

Mitigations:

* Minimal services
* Firewall allowlisting
* MAC confinement
* Vulnerability scanning

📸 **Filename:** `week2-threat-service.png`
**Figure W2-14:** Service exploitation risk assessment.

---

## Evidence Summary (Planned)

| Evidence    | Command                     |
| ----------- | --------------------------- |
| System info | `uname -a`                  |
| Disk I/O    | `iostat`                    |
| Processes   | `top`, `ls`                 |
| Services    | `systemctl`                 |
| SSH config  | `sshd_config`               |
| Firewall    | `ufw status`                |
| Memory      | `vmstat`                    |
| Users       | `/etc/passwd`, `/etc/group` |

---

## Reflection

This planning phase ensured security and performance considerations were addressed before implementation. A defense-in-depth strategy was selected to balance strong protection with remote manageability.

---

## References

* Ubuntu OpenSSH Security
  [https://documentation.ubuntu.com/server/how-to/security/openssh-server/](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)

* Ubuntu Server Security Concepts
  [https://ubuntu.com/server/docs/explanation/security/](https://ubuntu.com/server/docs/explanation/security/)

* Ubuntu UFW Documentation
  [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
  [https://documentation.ubuntu.com/server/how-to/security/firewalls/](https://documentation.ubuntu.com/server/how-to/security/firewalls/)

---

**[← Week 1](week1-system-planning.md)** | **[Week 3 →](week3-application-selection.md)**


Just tell me 👍

