
---

# Week 4 — Initial Configuration & Security Implementation

**[← Week 3](week3.md)** | **Week 4** | **[Week 5 →](week5.md)**

---

## Overview

Week 4 focuses on implementing the core security controls planned in earlier phases. The primary goal is to harden remote access, restrict network exposure, and enforce least-privilege administration on the Ubuntu Server.

All configuration and evidence collection are performed remotely via SSH, with no local console access, to reflect real-world server administration practices.

---

## Objectives

* Configure SSH key-based authentication and disable password login
* Restrict SSH access via firewall rules to the workstation IP only
* Create a non-root administrative user following least-privilege principles
* Document configuration changes with before/after evidence
* Demonstrate secure remote administration via SSH

---

## Deliverables

* SSH configuration evidence (`sshd_config` before/after)
* Firewall ruleset verification (`ufw status numbered`)
* User and privilege setup evidence
* Proof of remote administration via SSH
* Screenshot-based evidence for all changes

---

## 1. SSH Key-Based Authentication & Hardening

### 1.1 SSH Key Preparation

SSH host keys were verified and generated where required:

```bash
sudo ssh-keygen -A
```

User public keys were installed securely:

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
nano ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

📸 **Screenshot to capture**
**Filename:** `week4-authorized-keys.png`

```md
![Authorized Keys Setup](../assets/screenshots/week4/week4-authorized-keys.png)
**Figure W4-1:** SSH public key installed in authorized_keys with correct permissions.
```

---

### 1.2 SSH Daemon Hardening

The SSH daemon configuration was edited to enforce key-based authentication and restrict access:

```bash
sudoedit /etc/ssh/sshd_config
```

**Key security settings applied:**

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers <admin>
X11Forwarding no
```

SSH service reloaded to apply changes:

```bash
sudo systemctl restart sshd
sudo systemctl status sshd
```

📸 **Screenshot to capture**
**Filename:** `week4-sshd-status.png`

```md
![SSHD Status](../assets/screenshots/week4/week4-sshd-status.png)
**Figure W4-2:** SSH daemon running after hardening configuration.
```

---

### 1.3 SSH Configuration Evidence

Before and after configurations were captured and compared:

```bash
diff -u sshd_config.before sshd_config.after
```

📸 **Screenshot to capture**
**Filename:** `week4-sshd-diff.png`

```md
![SSHD Configuration Diff](../assets/screenshots/week4/week4-sshd-diff.png)
**Figure W4-3:** Before/after comparison of SSH daemon configuration.
```

---

## 2. Firewall Configuration (UFW)

### 2.1 Firewall Policy

A default-deny posture was implemented:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

SSH access restricted to workstation IP only:

```bash
sudo ufw allow from 192.168.56.102 to any port 22 proto tcp
```

Firewall enabled and verified:

```bash
sudo ufw enable
sudo ufw status numbered
```

📸 **Screenshot to capture**
**Filename:** `week4-ufw-status.png`

```md
![UFW Ruleset](../assets/screenshots/week4/week4-ufw-status.png)
**Figure W4-4:** UFW ruleset showing SSH restricted to workstation IP only.
```

---

## 3. Non-Root Administrative User Setup

### 3.1 User Creation

A dedicated non-root administrative user was created:

```bash
sudo adduser <admin>
```

The user was granted sudo privileges:

```bash
sudo usermod -aG sudo <admin>
```

📸 **Screenshot to capture**
**Filename:** `week4-user-creation.png`

```md
![Admin User Creation](../assets/screenshots/week4/week4-user-creation.png)
**Figure W4-5:** Creation of non-root administrative user.
```

---

### 3.2 Sudo Configuration

Least-privilege sudo access was configured using a drop-in file:

```bash
sudo visudo -f /etc/sudoers.d/<admin>
```

**Key considerations:**

* Passwordless sudo disabled
* No unrestricted root shell access
* Configuration validated with `visudo`

📸 **Screenshot to capture**
**Filename:** `week4-sudoers-config.png`

```md
![Sudoers Configuration](../assets/screenshots/week4/week4-sudoers-config.png)
**Figure W4-6:** Custom sudoers configuration enforcing least privilege.
```

---

## 4. Remote Administration Evidence

All administration was performed remotely via SSH from the workstation.

Verification commands executed:

```bash
whoami
hostname
ip addr
```

📸 **Screenshot to capture**
**Filename:** `week4-remote-admin.png`

```md
![Remote Administration](../assets/screenshots/week4/week4-remote-admin.png)
**Figure W4-7:** Secure remote administration using non-root user and sudo.
```

Evidence confirms:

* Login as non-root admin user
* Successful privilege escalation via sudo
* No local console usage

---

## Reflection (Week 4)

### Security Impact

* SSH attack surface significantly reduced
* Password authentication fully eliminated
* Root login disabled, improving accountability
* Firewall restricts access to a single trusted IP

### Challenges & Risk Mitigation

* SSH lockout risk mitigated by keeping an active session open
* Firewall rules tested before enforcement
* SSH service status verified before disconnecting

### Design Justification

* IP-based firewall restrictions minimise exposure
* SSH key authentication provides strong cryptographic security
* Non-root administration improves auditability and containment

### Comparison to Week 1

| Aspect     | Week 1       | Week 4           |
| ---------- | ------------ | ---------------- |
| SSH Access | Default      | Key-based only   |
| Root Login | Enabled      | Disabled         |
| Firewall   | Not enforced | Strict allowlist |
| Privileges | Root-centric | Least privilege  |

---

## Image Caption Reference (Quick Copy)

* **Figure W4-1:** SSH authorized_keys setup
* **Figure W4-2:** SSH daemon running after hardening
* **Figure W4-3:** SSH configuration before/after diff
* **Figure W4-4:** UFW rules restricting SSH access
* **Figure W4-5:** Non-root admin user creation
* **Figure W4-6:** Sudoers least-privilege configuration
* **Figure W4-7:** Secure remote administration evidence

---

## Next Week Preview — Week 5

* Deploy performance monitoring scripts
* Capture baseline vs load metrics
* Automate data collection
* Begin performance analysis

---

**[← Week 3](week3.md)** | **Week 4** | **[Week 5 →](week5.md)**


Just tell me 👍

