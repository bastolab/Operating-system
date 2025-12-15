# Week 1 — System Planning & Distribution Selection

## Objectives
* Design VirtualBox-based lab with defined network topology, IP addressing, and SSH access paths
* Compare server distributions and justify selection based on project requirements
* Document baseline system specifications using CLI commands only
* Create architecture diagram illustrating network design and system connections

---

## System Architecture

![Figure 1.1: VirtualBox lab system architecture](images/week1/week1-system-architecture.png)

*Figure 1.1: Ubuntu Server isolated on Host-Only network; Ubuntu Workstation connected via NAT and Host-Only adapters for controlled internet access and internal communication.*

**Architecture Components:**
- **Ubuntu Server:** Host-Only network (isolated from internet)
- **Ubuntu Workstation:** Dual adapters (NAT + Host-Only)
- **Private Network:** `192.168.56.0/24` for secure SSH access
- **Internet Gateway:** Workstation only

---

## Distribution Selection

### Ubuntu Server 22.04 LTS — Selected

**Justification:**
- **Long-Term Support:** 5-year update cycle ensures stability
- **Extensive Documentation:** Beginner-friendly with robust community resources
- **Package Availability:** Large repositories simplify software installation
- **VirtualBox Compatibility:** Excellent guest additions support
- **Learning Value:** Industry-relevant skills and widespread adoption

**Trade-offs:**
- Slightly higher resource usage than minimal distributions
- Some enterprise features require Ubuntu Pro subscription

### Alternatives Considered

| Distribution | Pros | Cons | Decision |
|-------------|------|------|----------|
| **Debian 12** | Stable, lightweight, secure | Older packages, manual configuration | Not selected: steeper learning curve |
| **Rocky Linux 9** | RHEL-compatible, enterprise-grade | Limited beginner resources, complex setup | Not selected: overkill for lab environment |

**Conclusion:** Ubuntu Server balances ease of use, support, and real-world applicability for this project.

---

## Workstation Configuration

### Ubuntu Desktop 24.04 LTS — Selected Approach

**Role:**
- Administrative control node
- SSH client for server management
- Internet access gateway for updates
- Testing and monitoring platform

**Network Design:**
- **Adapter 1 (NAT):** Outbound internet access for package updates
- **Adapter 2 (Host-Only):** Internal communication with server

**SSH Configuration:**
- Key type: `ed25519`
- Storage path: `~/.ssh/id_ed25519`
- Authentication: Public key only (password disabled)

---

## Network Configuration

### IP Addressing Plan

| System | Adapter | Mode | IP Address | Gateway | Internet |
|--------|---------|------|------------|---------|----------|
| **Ubuntu Server** | vboxnet0 | Host-Only | `192.168.56.103/24` | None | No |
| **Ubuntu Workstation** | Adapter 1 | NAT | DHCP | Auto | Yes |
| **Ubuntu Workstation** | Adapter 2 | Host-Only | `192.168.56.102/24` | `192.168.56.1` | No |

### VirtualBox Network Settings
- **Host-Only Network:** `vboxnet0` (`192.168.56.0/24`)
- **DHCP:** Disabled (static IPs assigned)
- **Security:** Server isolated; workstation bridges internal/external networks

### Network Verification

```bash
# View network interfaces
ip addr show

# Check routing table
ip route show

# Test connectivity
ping -c 4 192.168.56.103  # From workstation to server
```

---

## System Baseline Documentation

### CLI Evidence Collection

**System Information:**
```bash
uname -a           # Kernel version and architecture
lsb_release -a     # Distribution details
```

**Resource Utilization:**
```bash
free -h            # Memory usage
df -h              # Disk space
```

**Network Configuration:**
```bash
ip addr show       # Network interfaces and IPs
ip route show      # Routing table
```

### System Specifications

![Figure 1.2: System specifications output](images/week1/week1-specs.png)

*Figure 1.2: Baseline CLI output showing kernel version, memory allocation, disk usage, and network configuration.*

**Key Metrics:**
- **OS:** Ubuntu Server 22.04.3 LTS / Ubuntu Desktop 24.04 LTS
- **Kernel:** Linux 5.15.0+ (Server) / 6.8.0+ (Workstation)
- **Memory:** 2GB (Server) / 4GB (Workstation)
- **Disk:** 20GB allocated per VM

---

## Deliverables Summary

✅ **Architecture Diagram:** Complete network topology with security boundaries  
✅ **Distribution Comparison:** Ubuntu Server vs Debian vs Rocky Linux  
✅ **Workstation Rationale:** Dual-adapter design for isolation and internet access  
✅ **Network Plan:** Host-Only (`192.168.56.0/24`) with static IP assignments  
✅ **CLI Baseline:** System specifications captured via terminal commands  

---

## Reflection

### Design Trade-offs

**Distribution Choice:**
- Prioritized **documentation and support** over minimal footprint
- Ubuntu's package availability outweighed Debian's lower resource usage
- LTS releases provide stability needed for long-term testing

**Networking Challenges:**
- **Static vs DHCP:** Manual IP assignment ensures predictable SSH connections
- **NAT vs Host-Only:** Dual adapters balance security isolation with update requirements
- **Internet Access:** Server isolation prevents unintended exposure while allowing workstation updates

### Lessons Learned
- VirtualBox Host-Only networks require careful adapter ordering
- Static IPs simplify SSH key management and firewall rules
- Baseline documentation proves invaluable for troubleshooting later changes

### Next Steps
- **Week 2:** Implement security hardening (SSH keys, firewall rules, fail2ban)
- Develop automated testing scripts for network isolation verification
- Prepare monitoring infrastructure (logs, metrics collection)

---

**[Home](../README.md)** | **[Week 2 →](week2.md)**
