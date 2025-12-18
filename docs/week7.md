Got it! I’ll create a **final GitHub-ready Markdown report** and include your **exact screenshot filenames** (`w7-fig1-lynis-audit.png`, `w7-fig3-nmap-scan.png`, `w7-fig4-ssh-verification.png`) so everything matches your uploaded files. Here’s the polished version:

---

# Week 7 — Security Audit & System Evaluation

← **[Week 6](week6.md)** | **Week 7 (Final)**

---

## Overview

This final week conducts a comprehensive **security audit and system evaluation** of the Ubuntu Server configured throughout Weeks 2–6.
The objective is to validate the effectiveness of implemented controls, quantify security improvements using industry-standard tools, and present a **final risk-based assessment** balancing security, performance, and usability.

Auditing is performed using **Lynis**, **Nmap**, and direct verification of access controls, running services, and Mandatory Access Control (MAC) enforcement. Results are compared against earlier system states to demonstrate **measurable improvement**.

---

## Objectives

* Perform a full system security audit (Lynis, Nmap, access control checks)
* Compare Lynis hardening scores before and after remediation
* Validate SSH, sudo, firewall, and MAC enforcement
* Inventory running services and justify their necessity
* Produce a final risk assessment and system evaluation

---

## Deliverables

* 📄 Security audit summary with evidence
* 📊 Lynis audit results and score trend
* 🌐 Network exposure analysis (Nmap)
* 🔐 Access control verification (SSH, sudo, MAC)
* 📋 Service inventory with justification
* ⚠️ Remaining risks and mitigation plan

---

## Security Audit Methodology

### Tools Used

| Tool                 | Purpose                                        |
| -------------------- | ---------------------------------------------- |
| **Lynis**            | Host-based security audit & hardening analysis |
| **Nmap**             | Network exposure and service fingerprinting    |
| **System Utilities** | SSH, firewall, sudo, and MAC verification      |

All audits were conducted **non-disruptively** and remotely via SSH.

---

## Lynis Security Audit

### Audit Execution (Server)

```bash
sudo lynis audit system --quiet --logfile /var/log/lynis.log
```

Key findings extracted using:

```bash
grep -E "hardening_index|warning|suggestion" /var/log/lynis.log
```

---

### Lynis Results Summary

| Metric                   | Result                           |
| ------------------------ | -------------------------------- |
| Hardening Index (Before) | Documented during early baseline |
| Hardening Index (After)  | Increased following remediation  |

**Key Improvements Identified by Lynis:**

* SSH hardening (key-based auth, root login disabled)
* Firewall default-deny configuration
* fail2ban protection enabled
* Automatic security updates active
* MAC enforcement (AppArmor)

**Figure W7-1: Lynis hardening score after remediation**

![w7-fig1-lynis-audit](images/screenshots/week7/w7-fig1-lynis-audit.png)

Audit logs stored in:

```text
data/audit/
```

---

## Network Security Testing (Nmap)

### Scan Execution (Workstation Only)

```bash
nmap -sV -Pn 192.168.56.10
```

**Figure W7-2: Nmap service scan from trusted workstation**

![w7-fig3-nmap-scan](images/screenshots/week7/w7-fig3-nmap-scan.png)

### Findings

* Only **SSH (port 22)** exposed
* No unnecessary services detected
* Service versions consistent with patched system

This confirms effective firewall allow-listing and service minimisation.

---

## Access Control Verification

### SSH Configuration Validation

Confirmed via configuration review and login testing:

* Root login disabled
* Password authentication disabled
* Key-based authentication enforced
* Access restricted to approved admin users

**Figure W7-3: SSH login using key-based authentication**

![w7-fig4-ssh-verification](images/screenshots/week7/w7-fig4-ssh-verification.png)

---

### Sudo & User Privileges

```bash
ssh user@server "sudo -l"
```

* Non-root administrative user enforced
* Least-privilege sudo configuration
* No passwordless sudo unless justified

**Figure W7-4: sudo privilege verification**

---

### Mandatory Access Control (MAC)

```bash
ssh user@server "sudo aa-status"
```

* AppArmor enabled and enforcing
* Active profiles loaded for critical services

---

## Service Inventory & Justification

```bash
ssh user@server "systemctl list-units --type=service --state=running"
```

| Service             | Purpose               | Justification                  |
| ------------------- | --------------------- | ------------------------------ |
| ssh                 | Remote administration | Required for secure management |
| nginx               | Web workload          | Performance evaluation         |
| fail2ban            | Intrusion prevention  | SSH brute-force protection     |
| unattended-upgrades | Patch automation      | Reduces vulnerability exposure |

All running services are **documented and justified**. No unnecessary services remain enabled.

---

## Remediation Actions & Impact

| Issue Identified         | Action Taken            | Result                 |
| ------------------------ | ----------------------- | ---------------------- |
| Weak SSH defaults        | Enforced key-based auth | Reduced attack surface |
| Open network exposure    | Firewall allow-listing  | SSH only exposed       |
| Brute-force risk         | fail2ban enabled        | Automated blocking     |
| Missing patch automation | unattended-upgrades     | Improved patch hygiene |

Each remediation contributed to a **measurable Lynis score increase**.

---

## Remaining Risks & Mitigation Plan

| Risk                     | Status    | Rationale                                 |
| ------------------------ | --------- | ----------------------------------------- |
| SSH key compromise       | Accepted  | Mitigated via passphrase + IP restriction |
| Zero-day vulnerabilities | Deferred  | Addressed via updates & monitoring        |
| Insider misuse           | Mitigated | Least-privilege sudo + logs               |

All remaining risks are **documented with justification**.

---

## Final Evaluation

### Security

* Strong layered security baseline
* External exposure reduced to minimum
* Continuous monitoring enabled

### Performance

* Security controls introduced negligible overhead
* Prior optimisations preserved responsiveness

### Usability

* Efficient remote administration
* Clear privilege separation improves auditability

---

## Final Reflection

This project demonstrates a **complete secure Linux system lifecycle**:
planning → implementation → testing → optimisation → audit

Security improvements were validated quantitatively while maintaining acceptable performance and usability. The final system reflects **real-world production best practices**.

---

## Demonstration Preparation

### 8-Minute Video Walkthrough Plan

1. Project overview & architecture
2. Live SSH login (key-based)
3. Firewall & fail2ban verification
4. AppArmor enforcement
5. Lynis & Nmap key findings
6. `security-baseline.sh` & monitoring scripts
7. Lessons learned & trade-offs

---

## Key Screenshots

| Screenshot Filename          | Description                             |
| ---------------------------- | --------------------------------------- |
| w7-fig1-lynis-audit.png      | Lynis hardening score after remediation |
| w7-fig3-nmap-scan.png        | Nmap scan of exposed services           |
| w7-fig4-ssh-verification.png | SSH key-based login verification        |

---

## Navigation

← **[Week 6](week6.md)** | **Week 7 (Final)**

---

This version is **ready for GitHub**. Make sure your images are stored in:

```
images/screenshots/week7/
```

so they render correctly in the Markdown file.

---

If you want, I can also **create a compact `README.md`** for your full repository that links all weeks, including this final report with thumbnails of your screenshots for easier navigation.

Do you want me to do that too?
