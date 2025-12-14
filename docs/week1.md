# Phase 1: System Planning and Distribution Selection (Week 1)

---

## Overview

This phase covers the planning and setup of a VirtualBox lab environment hosted on a Mac laptop.  
The lab environment consists of one **Ubuntu Server** and one **Ubuntu Desktop Workstation**, configured with secure network isolation and controlled internet access.

---

## Lab Environment Overview

### Systems

| Component | OS Version | Network Mode | IP Address |
|-----------|------------|--------------|------------|
| Ubuntu Server | 22.04 LTS | Host-Only | 192.168.56.103/24 |
| Ubuntu Workstation | 24.04 LTS | NAT + Host-Only | 192.168.56.102/24 |

---

### Host Environment

- Physical Host Machine: **Mac Laptop**  
- Virtualization Platform: **Oracle VirtualBox**

---

## System Architecture Diagram

The following diagram illustrates the lab architecture and network segmentation:

![System Architecture Diagram](../assets/screenshots/architecture.png)  
*Figure 1: Ubuntu Server and Workstation network setup in VirtualBox.*

**Architecture Description:**
- Ubuntu Server VM connected only to **Host-Only network**
- Ubuntu Workstation VM connected to **NAT + Host-Only**
- Private Host-Only network for internal communication
- NAT network for internet access on workstation only

**Benefits:**
- Secure private communication between server and workstation
- Internet access restricted to workstation
- Server remains isolated from the public internet

---

## Distribution Selection Justification

### Ubuntu Server (Chosen)

**Pros:**
- Beginner-friendly and suitable for coursework
- Large software repository and community support
- Extensive documentation
- Excellent VirtualBox compatibility
- Long-term support (5-year LTS)

**Cons:**
- Slightly higher resource usage than minimal distributions
- Some enterprise features require Ubuntu Pro subscription

### Debian

**Pros:**
- Extremely stable and lightweight
- Strong security through strict package testing

**Cons:**
- Packages often outdated
- Manual configuration and technical documentation
- Less common in cloud environments

### Red Hat Enterprise Linux (RHEL)

**Pros:**
- Enterprise-grade stability and performance
- Strong security features
- Professionally supported

**Cons:**
- Requires paid subscription
- Not beginner-friendly
- Limited free repositories

### Conclusion

Ubuntu Server was selected because it provides the **best balance between ease of use, software availability, long-term support, and VirtualBox compatibility**.  
Debian is more stable but less beginner-friendly, while RHEL is enterprise-focused and not free.

---

## Workstation Configuration

**OS:** Ubuntu Desktop 24.04 LTS  
**Network Adapters:**
- Adapter 1: NAT (internet access)
- Adapter 2: Host-Only (static IP: 192.168.56.102/24)

**Role:**
- Administrative control terminal
- Client for server access
- Internet gateway for updates
- Testing platform for client/server communication

**Rationale:**
- NAT: Provides secure outbound internet access
- Host-Only: Provides private LAN for server communication

---

## Network Configuration Documentation

### Ubuntu Server

| Adapter | Type | IP Address | Gateway | Internet Access |
|---------|------|------------|---------|----------------|
| Adapter 1 | Host-Only | 192.168.56.103/24 | None | Disabled |

![Server Network Configuration](../assets/screenshots/server-ip.png)  
*Figure 2: Server Host-Only network setup.*

### Ubuntu Workstation

| Adapter | Type | IP Address | Gateway |
|---------|------|------------|---------|
| Adapter 1 | NAT | DHCP | Auto |
| Adapter 2 | Host-Only | 192.168.56.102/24 | 192.168.56.1 |

![Workstation Network Configuration](../assets/screenshots/workstation-ip.png)  
*Figure 3: Workstation NAT + Host-Only network setup.*

---

## System Specifications

### Commands Used

```bash
uname
free -h
df -h
ip addr
lsb_release -a
Example Outputs
$ uname -a
Linux ubuntu-server 6.14.0-27-generic x86_64 GNU/Linux

Figure 4: Kernel and system architecture.
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           3.8G        1.0G        2.8G        0B         0B         2.8G
Swap:            0B          0B          0B

Figure 5: Memory usage.
Final Summary
Phase 1 successfully planned and deployed a secure VirtualBox lab environment:
Ubuntu Server isolated using Host-Only networking
Ubuntu Workstation with NAT + Host-Only networking
Secure internal communication
Internet access controlled through workstation
Strong foundation for future security and performance testing phases
