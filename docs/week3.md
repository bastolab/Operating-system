

# Week 3 — Application Selection for Performance Testing

**[← Week 2](week2-security-planning.md)** | **Week 3** | **[Week 4 →](week4-security-implementation.md)**

---

## Overview

Week 3 focuses on selecting representative applications to evaluate operating system performance under different workload categories. Each application is chosen based on how it stresses specific OS resources, including CPU scheduling, memory management, disk I/O, and network throughput.

All tools are installed and managed remotely via SSH using command-line utilities only. This ensures a headless, lightweight, and production-representative server environment.

Expected resource utilisation patterns are defined in advance to enable meaningful comparison between baseline (idle) and active workload states in later weeks.

---

## Objectives

* Select applications that stress different system resources
* Document installation using SSH and CLI tools only
* Define expected resource utilisation profiles
* Establish a monitoring strategy for each workload type

---

## Deliverables

* Application Selection Matrix
* Installation documentation with exact commands
* Expected resource utilisation profiles
* Monitoring strategy for each workload

---

## 1. Selected Workload Categories

The following workload types are evaluated:

* CPU-intensive
* Memory (RAM)-intensive
* Disk / I/O-intensive
* Network-intensive
* Server / service-based workload

---

## 2. Application Selection Matrix

| Workload Type      | Application              | Description              | Justification                                                       |
| ------------------ | ------------------------ | ------------------------ | ------------------------------------------------------------------- |
| CPU-intensive      | `stress-ng`              | CPU stress testing tool  | Generates controlled CPU load to evaluate scheduling and saturation |
| RAM-intensive      | `stress-ng` (vm workers) | Memory stress testing    | Allocates RAM to analyse paging and memory pressure                 |
| Disk I/O-intensive | `fio`                    | Flexible I/O tester      | Simulates realistic disk read/write workloads                       |
| Network-intensive  | `iperf3`                 | Network performance tool | Measures throughput and latency                                     |
| Server workload    | `nginx`                  | Lightweight web server   | Represents real-world service handling client requests              |

---

## 3. Installation Documentation (via SSH)

### 3.1 SSH Access Verification

📸 **Screenshot to capture**
**Filename:** `week3-ssh-access.png`

```md
![SSH Access Verification](../assets/screenshots/week3/week3-ssh-access.png)
**Figure W3-1:** Successful SSH connection from Ubuntu Workstation to Ubuntu Server.
```

This confirms the server is administered remotely without local GUI access.

---

### 3.2 Application Installation

All required tools were installed using APT over SSH:

```bash
sudo apt update
sudo apt install -y stress-ng fio iperf3 nginx sysstat
```

📸 **Screenshot to capture**
**Filename:** `week3-app-installation.png`

```md
![Application Installation](../assets/screenshots/week3/week3-app-installation.png)
**Figure W3-2:** Installation of performance testing applications via SSH.
```

---

### 3.3 Application Verification

Installed applications were verified using version checks:

```bash
stress-ng --version
fio --version
iperf3 --version
nginx -v
```

📸 **Screenshot to capture**
**Filename:** `week3-app-verification.png`

```md
![Application Verification](../assets/screenshots/week3/week3-app-verification.png)
**Figure W3-3:** Version outputs confirming successful installation.
```

---

## 4. Monitoring Strategy

### 4.1 Baseline Measurement (Idle State)

Before executing workloads, baseline system utilisation is captured.

📸 **Screenshot to capture**
**Filename:** `week3-baseline-idle.png`

```md
![Baseline Metrics](../assets/screenshots/week3/week3-baseline-idle.png)
**Figure W3-4:** Baseline system resource usage under idle conditions.
```

Baseline metrics serve as a reference point for active testing.

---

### 4.2 CPU Workload Observation

```bash
stress-ng --cpu 4 --timeout 60s
```

📸 **Screenshot to capture**
**Filename:** `week3-cpu-stress.png`

```md
![CPU Stress Test](../assets/screenshots/week3/week3-cpu-stress.png)
**Figure W3-5:** CPU utilisation during stress-ng execution.
```

---

### 4.3 Server Application Evidence

```bash
systemctl status nginx
```

📸 **Screenshot to capture**
**Filename:** `week3-nginx-status.png`

```md
![nginx Service Status](../assets/screenshots/week3/week3-nginx-status.png)
**Figure W3-6:** nginx running as a representative server-based workload.
```

---

## 5. Expected Resource Utilisation Profiles

| Application     | CPU Usage    | Memory Usage | Disk I/O      | Network Usage | Notes                |
| --------------- | ------------ | ------------ | ------------- | ------------- | -------------------- |
| stress-ng (CPU) | Very High    | Low          | Minimal       | None          | CPU saturation       |
| stress-ng (RAM) | Moderate     | Very High    | Possible swap | None          | Memory pressure      |
| fio             | Low–Moderate | Low          | Very High     | None          | Disk-focused testing |
| iperf3          | Moderate     | Low          | Minimal       | Very High     | Network throughput   |
| nginx           | Low–Moderate | Low–Moderate | Low           | Moderate–High | Real-world service   |

Predictions are based on documentation, prior experience, and workload characteristics.

---

## 6. Monitoring Tools and Metrics

### Monitoring Tools

* `top` / `htop` — CPU and memory usage
* `free -h` — Memory statistics
* `vmstat` — System load and memory behaviour
* `iostat -xz 5` — Disk I/O performance
* `iftop`, `ss -tulpn` — Network activity
* `uptime` — Load averages

---

### Measurement Approach

* Capture baseline metrics before workload execution
* Record metrics during active workload execution
* Use consistent sampling intervals
* Store outputs for later analysis and visualisation

---

## Evidence Summary

| Evidence                | Purpose                   |
| ----------------------- | ------------------------- |
| SSH session screenshots | Verify remote management  |
| Installation outputs    | Confirm tool availability |
| Version checks          | Validate readiness        |
| Baseline metrics        | Idle comparison           |
| Active workload metrics | Performance analysis      |
| Service status          | Confirm server workloads  |

---

## Reflection (Week 3)

This week reinforced the importance of aligning workload types with measurable operating system behaviours. Selecting appropriate tools demonstrated how CPU, memory, disk, and network subsystems can be independently evaluated.

The planning completed here establishes a solid foundation for performance testing, analysis, and optimisation in later weeks.

---

## Next Week Preview — Week 4

* Implement SSH key-based authentication
* Configure firewall rules (UFW)
* Create non-root administrative user
* Begin secure remote administration

---

## Image Caption Reference (Quick Copy)

* **Figure W3-1:** SSH access verification
* **Figure W3-2:** Application installation
* **Figure W3-3:** Application version verification
* **Figure W3-4:** Baseline idle metrics
* **Figure W3-5:** CPU workload execution
* **Figure W3-6:** nginx service status

---

## References

* stress-ng Documentation
  [https://manpages.ubuntu.com/manpages/stress-ng](https://manpages.ubuntu.com/manpages/stress-ng)

* fio Documentation
  [https://fio.readthedocs.io/](https://fio.readthedocs.io/)

* iperf3 Documentation
  [https://iperf.fr/](https://iperf.fr/)

* nginx Documentation
  [https://nginx.org/en/docs/](https://nginx.org/en/docs/)

---

**[← Week 2](week2-security-planning.md)** | **Week 3** | **[Week 4 →](week4-security-implementation.md)**

Just tell me 👍

