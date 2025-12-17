Perfect 👍
Now that **all filenames are fixed**, the last step is to **fix your Week 2 Markdown** so images actually render on GitHub.

Below is a **clean, corrected FINAL version of Week 2**, using:

* ✅ Proper Markdown headings
* ✅ Correct image syntax (NOT inside code blocks)
* ✅ Correct relative path: `../imagescreenshots/week2/`
* ✅ Image names matching what you renamed

You can **copy–paste this directly** into `docs/week2.md`.

---

# Week 2 — Security Planning & Testing Methodology

**[Home](../README.md)** | **[Week 1](week1.md)** | **[Week 3 →](week3.md)**

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

* Performance testing plan
* Security configuration checklist
* Threat model with prioritized mitigations

---

## 1. Performance Testing Plan

### 1.1 Remote Monitoring Methodology

**Approach**

* Monitoring conducted remotely via SSH
* Standard Linux command-line utilities
* Metrics captured at fixed intervals
* Evidence includes terminal output and screenshots

**Remote Execution Example**

```bash
ssh user@server "vmstat 5 5"
```

📸 **Screenshot**
Filename: `vmstat1-10.png`

![Remote monitoring via SSH](../imagescreenshots/week2/vmstat1-10.png)

**Figure W2-1:** Remote execution of vmstat via SSH.

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

📸 Filename: `baseline.png`

![System information](../imagescreenshots/week2/baseline.png)

**Figure W2-2:** Kernel version and system architecture.

---

#### CPU Monitoring

```bash
htop
```

📸 Filename: `htop.png`

![CPU monitoring](../imagescreenshots/week2/htop.png)

**Figure W2-3:** CPU utilization observed using htop.

---

#### Memory Monitoring

```bash
free -h
vmstat 1 10
```

📸 Filename: `free-h.png`

![Memory monitoring](../imagescreenshots/week2/free-h.png)

**Figure W2-4:** Memory and swap statistics.

---

#### Disk Performance

```bash
df -h
iostat
```

📸 Filename: `df-h.png`

![Disk usage](../imagescreenshots/week2/df-h.png)

📸 Filename: `iostat-d-io.png`

![Disk IO](../imagescreenshots/week2/iostat-d-io.png)

**Figure W2-5:** Disk usage and I/O performance.

---

#### Network Monitoring

```bash
ss -tlnp
```

📸 Filename: `ss-tlnp.png`

![Network ports](../imagescreenshots/week2/ss-tlnp.png)

**Figure W2-6:** Active listening ports and services.

---

## 2. Security Configuration Checklist

### 2.1 SSH Hardening

📸 Filename: `sshd-t.png`

![SSH hardening](../imagescreenshots/week2/sshd-t.png)

**Figure W2-7:** Planned SSH hardening configuration.

---

### 2.2 Firewall Configuration (UFW)

📸 Filename: `sudo-ufw.png`

![UFW rules](../imagescreenshots/week2/sudo-ufw.png)

📸 Filename: `ufw-status.png`

![UFW status](../imagescreenshots/week2/ufw-status.png)

**Figure W2-8:** Firewall rules and status.

---

### 2.3 User & Key Management

📸 Filename: `ssh-keygen.png`

![SSH key generation](../imagescreenshots/week2/ssh-keygen.png)

📸 Filename: `ssh-copy-id.png`

![SSH key copy](../imagescreenshots/week2/ssh-copy-id.png)

📸 Filename: `adduse.png`

![Add user](../imagescreenshots/week2/adduse.png)

**Figure W2-9:** Secure user and SSH key configuration.

---

### 2.4 Service Management

📸 Filename: `sudo-systemctl.png`

![Systemctl services](../imagescreenshots/week2/sudo-systemctl.png)

**Figure W2-10:** Managing services using systemctl.

---

## 3. Threat Model

### Threat 1: Unauthorized SSH Access

**Risk:** High

Mitigations:

* Key-based authentication
* Firewall IP restrictions
* Log monitoring

---

### Threat 2: Privilege Escalation

**Risk:** Medium–High

Mitigations:

* Least-privilege sudo
* AppArmor enforcement
* Automatic updates

---

### Threat 3: Resource Exhaustion

📸 Filename: `stress.png`

![Stress testing](../imagescreenshots/week2/stress.png)

**Figure W2-11:** Stress testing to identify performance limits.

---

## Evidence Summary

| Evidence    | Command       |
| ----------- | ------------- |
| System info | `uname -a`    |
| Disk I/O    | `iostat`      |
| Processes   | `htop`, `top` |
| Services    | `systemctl`   |
| SSH config  | `sshd_config` |
| Firewall    | `ufw status`  |
| Memory      | `vmstat`      |
| Users       | `/etc/passwd` |

---

## Reflection

This planning phase ensured security and performance considerations were addressed before implementation. A defense-in-depth strategy was selected to balance protection with remote manageability.

---

## References

* Ubuntu OpenSSH Security
  [https://documentation.ubuntu.com/server/how-to/security/openssh-server/](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)

* Ubuntu Server Security
  [https://ubuntu.com/server/docs/explanation/security/](https://ubuntu.com/server/docs/explanation/security/)

* Ubuntu Firewall
  [https://documentation.ubuntu.com/server/how-to/security/firewalls/](https://documentation.ubuntu.com/server/how-to/security/firewalls/)

---

**[← Week 1](week1.md)** | **[Week 3 →](week3.md)**

---

## ✅ FINAL CONFIRMATION

If images **still don’t show**, check **only these 3 things**:

1. Folder name is exactly: `imagescreenshots`
2. Files are inside: `imagescreenshots/week2/`
3. Filenames have **NO spaces**

If you want, next I can:

* ✔ Fix **Week 3–7** the same way
* ✔ Review for **grading / submission**
* ✔ Clean README navigation

Just tell me 👍
