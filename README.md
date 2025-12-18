

# Linux Server Security & Performance Evaluation

## Overview

This repository documents the **design, hardening, performance testing, and evaluation** of a Linux server deployed in a VirtualBox lab environment.
The project follows a structured **weekly methodology**, focusing on **defense-in-depth security** and **measurable system performance**.

---

## Architecture

* **Ubuntu Server 22.04 LTS** – Host-Only network (isolated)
* **Ubuntu Desktop 24.04 LTS** – NAT + Host-Only network (administrative workstation)
* Secure internal communication with controlled internet access



## Weekly Documentation

* [Week 1 – Initial setup & system configuration](docs/Week1.md)
* [Week 2 – Service deployment & baseline configuration](docs/Week2.md)
* [Week 3 – Application workload installation](docs/Week3.md)
* [Week 4 – Security hardening & user management](docs/Week4.md)
* [Week 5 – Monitoring scripts & initial performance tests](docs/Week5.md)
* [Week 6 – Performance evaluation & analysis](docs/Week6.md)
* [Week 7 – Security audit & final system evaluation](docs/Week7.md)



## Key Features

* **SSH key-based authentication** for secure remote access
* **Firewall allowlisting (UFW)** to limit external exposure
* **AppArmor enforcement** for Mandatory Access Control (MAC)
* **Automated security updates** with `unattended-upgrades`
* **Performance monitoring & analysis** using scripts and metrics
* **Security auditing** with Lynis and Nmap

---

## Scripts

* `scripts/security-baseline.sh` – Validates system security configuration
* `scripts/monitor-server.sh` – Collects performance metrics for analysis

---

## Demonstration

A live demonstration is provided via **recorded CLI sessions** showing:

* Secure SSH remote administration
* Real-time system monitoring
* Security auditing and remediation verification

---

## Notes

This repository provides a **complete example of a secure Linux system lifecycle**, from planning and implementation to testing, optimisation, and audit, suitable for lab environments or educational purposes.

