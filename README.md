#os
# Linux Server Security & Performance Evaluation

## Overview
This repository documents the design, security hardening, performance testing, and evaluation of a Linux server deployed in a VirtualBox lab environment. The project follows a structured weekly methodology focusing on defense-in-depth security and measurable system performance.

## Architecture
- Ubuntu Server 22.04 LTS (Host-Only network, isolated)
- Ubuntu Desktop 24.04 LTS (NAT + Host-Only, administrative workstation)
- Secure internal communication with controlled internet access

## Weekly Documentation
- [Week 1 – System Planning & Distribution Selection](docs/week1-system-planning.md)
- [Week 2 – Security Planning & Testing Methodology](docs/week2-security-planning.md)
- [Week 3 – Application Selection for Performance Testing](docs/week3-application-selection.md)
- [Week 4 – Initial Configuration & Security Implementation](docs/week4-initial-security.md)
- [Week 5 – Advanced Security & Monitoring](docs/week5-advanced-security.md)
- [Week 6 – Performance Evaluation & Analysis](docs/week6-performance-evaluation.md)
- [Week 7 – Security Audit & System Evaluation](docs/week7-security-audit.md)

## Key Features
- SSH key-based authentication
- Firewall allowlisting (UFW)
- AppArmor enforcement
- Automated security updates
- Performance monitoring & analysis
- Security auditing with Lynis

## Scripts
- `scripts/security-baseline.sh` – Validates system security configuration
- `scripts/monitor-server.sh` – Collects performance metrics for analysis

## Demo
A live demonstration is provided via recorded CLI sessions showing secure remote administration, monitoring, and auditing.

