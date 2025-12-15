
# Linux Server Security & Performance Evaluation

## Overview

This repository documents the design, security hardening, performance testing,
and evaluation of a Linux server deployed in a VirtualBox-based lab environment.
The project follows a structured weekly methodology, focusing on defense-in-depth
security controls and measurable system performance analysis.

All configuration, testing, and evidence collection were performed remotely via
SSH to reflect real-world server administration practices.

---

## Architecture

- **Ubuntu Server 22.04 LTS**
  - Host-only network
  - Hardened and headless
- **Ubuntu Desktop 24.04 LTS**
  - NAT + Host-only networking
  - Administrative workstation
- Secure internal communication with controlled internet access

## Weekly Documentation

* docs/week1.md
* docs/week2.md
* docs/week3.md
* docs/week4.md)
* docs/week5.md)
* docs/week6.md)
* docs/week7.md)

---

## Key Security Features

* SSH key-based authentication
* Firewall allowlisting with UFW
* Non-root administrative user
* AppArmor enforcement
* fail2ban intrusion prevention
* Automated security updates

---

## Scripts

* `scripts/security-baseline.sh`
  Validates SSH, firewall, MAC enforcement, updates, and user privileges.

* `scripts/monitor-server.sh`
  Collects CPU, memory, disk, and network performance metrics for analysis.

---

## Demonstration

A recorded CLI-based demonstration shows:

* Secure SSH administration
* Firewall and MAC verification
* Performance monitoring
* Lynis security auditing
* Final system evaluation and analysis

---

## Conclusion

This project demonstrates a complete secure Linux system lifecycle:
from initial deployment and hardening to performance testing, optimisation,
and final security audit. All conclusions are supported by quantitative
evidence and real-world best practices.


Just tell me 👌
```
