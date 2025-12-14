Phase 1: System Planning and Distribution Selection (Week 1) 

 

OVERVIEWx 

This phase covers the planning and setup of my VirtualBox lab environment using a laptop as the host machine. The environment consists of one Ubuntu Server and one Ubuntu Desktop Workstation configured with appropriate network modes for secure internal communication and internet access. 

 

Systems 

Ubuntu Server 22.04 LTS 

Network Mode: Host-Only 
IP Address: 192.168.56.103/24 
Ubuntu Desktop 24.04 LTS 

Network Mode: NAT + Host-Only 
IP Address (Host-Only): 192.168.56.102/24 
 

Host Environment 

Physical Host Machine: Mac Laptop 
Virtualization Platform: Oracle VirtualBox 
 

System Architecture Diagram 

System Architecture Diagram showing both systems and network connections. 

The lab environment consists of: 

One Ubuntu Server VM connected only to the Host-Only network 
One Ubuntu Workstation VM connected to both NAT and Host-Only 
A private Host-Only network for internal communication 
A NAT network on the workstation for internet access 
This setup allows: 

Secure private communication between the server and workstation 
Internet access only from the workstation 
The server to remain isolated from the internet for security 
 

 

Distribution Selection Justification 

Comparing the chosen server distribution with alternatives: 

 

Ubuntu Server 

Pros: 

Easy to use and beginner-friendly, suitable for coursework and lab environments 
Huge repository of up-to-date software packages 
Large, active community with extensive documentation 
Excellent compatibility with VirtualBox and cloud platforms 
Frequent security updates and a 5-year LTS support cycle 
Cons: 

Slightly less stable than Debian for ultra-long-term production use 
Uses more system resources than ultra-light distributions 
Some enterprise features require Ubuntu Pro subscription 
 

Debian 

Pros: 

Extremely stable and reliable 
Excellent long-term performance 
Strong security due to strict package testing 
Very lightweight, suitable for low-spec systems 
Cons: 

Packages are often outdated 
Manual configuration is required 
Documentation can be very technical for beginners 
Less common in cloud environments compared to Ubuntu 
 

Red Hat Enterprise Linux (RHEL) 

Pros: 

Enterprise-grade stability and performance 
Very strong security features 
Professionally supported 
Suitable for corporate data centres 
Cons: 

Requires paid subscription for full features 
Difficult for beginners and students 
Limited free repositories 
Slower software updates 
 

Conclusion 

Ubuntu Server was selected as the most appropriate solution for this deployment because it offers the best balance between ease of use, modern software availability, long-term support, strong community backing, and full compatibility with VirtualBox. Debian is more stable but less beginner-friendly with older packages. RHEL is enterprise-focused but requires a paid subscription. Therefore, Ubuntu Server is the most effective choice for a learning and laboratory-based environment. 

Workstation Configuration Decision 
Workstation Configuration 
Workstation OS: Ubuntu Desktop 24.04 LTS 
VirtualBox Network Adapters: 
Adapter 1: NAT 
Adapter 2: Host-Only (Static IP: 192.168.56.102/24) 
Workstation Role 
The Ubuntu Workstation was installed as a client and control system to: 

Access the Ubuntu Server 
Test client/server communication 
Perform administrative tasks 
Download and update packages from the internet 
Act as the control terminal for all server services 
Since it requires both internet access and internal server communication, a dual-adapter setup was necessary. 

Rationale of Workstation Setup 
NAT Adapter – Internet Access 

NAT allows the workstation to access the internet through the host machine. This is required to: 

Update and download system packages 
Install tools such as OpenSSH client, curl, and browsers 
Access online documentation and learning resources 
Pros: 

Plug-and-play configuration 
No exposure of the VM to the public network 
Secure outbound-only internet access 
 

Host-Only Adapter – Internal Network and Server Access 

The Host-Only adapter provides a private LAN between: 

Host machine 
Ubuntu Server 
Ubuntu Workstation 
This enables: 

Direct SSH access to the server 
Secure internal testing 
No exposure to the public internet 
Pros: 

Static IP addressing 
Predictable SSH connections 
Secure isolated network 
Reasons Why Ubuntu Workstation Was Selected 
Ubuntu Workstation was selected because it fulfils all classroom and laboratory requirements. 

Pros: 

Easy-to-use graphical interface 
Large software repository and community 
Ideal for testing, learning, and rapid deployment 
Long-term support releases 
Excellent compatibility with VirtualBox 
Why Not Alternatives: 

Windows VM: High RAM usage, slow performance, licensing costs 
CentOS/RHEL Desktop: Complex and unsuitable for beginners 
Debian Desktop: Older packages and harder configuration 
Ubuntu Workstation provides the best balance of usability, performance, and compatibility for student use. 

Network Configuration Documentation 
This documentation describes the network setup for the VirtualBox-based environment. 

Ubuntu Server Network Configuration 
VirtualBox Settings: 

Adapter 1 → Host-Only Adapter (vboxnet0) 
IP Configuration: 

IP Address: 192.168.56.103/24 
Subnet Mask: 255.255.255.0 
Gateway: None 
Internet Access: None (Isolated by design) 
 

 

Ubuntu Workstation Network Configuration 

VirtualBox Settings: 

Adapter 1 → NAT 
Adapter 2 → Host-Only Adapter 
Host-Only Configuration: 

IP Address: 192.168.56.102/24 
Subnet Mask: 255.255.255.0 
Gateway: 192.168.56.1 
NAT Configuration: 

Provides automatic DHCP and DNS for internet access 
 

 

 

 

Host (Laptop) 

The system uses two VirtualBox network modes: 

Host-Only Network → Internal communication 
NAT Network → Internet access 
 

System Specifications Documentation 

The following commands were used: 
uname, free -h, df -h, ip addr, lsb_release 

 

System Information (uname) 

Kernel Version: 6.14.0-27-generic 
Architecture: x86_64 (64-bit) 
Operating System: GNU/Linux 
Build: Ubuntu SMP, PREEMPT_DYNAMIC 
 

Memory Information (free -h) 

Total RAM: 3.8 GiB 
Used RAM: 1.0 GiB 
Available RAM: 2.8 GiB 
Swap: 0 B 
 

 

Disk Space (df -h) 

Primary Disk Size: 25 GB 
Used: 5.1 GB 
Available: 19 GB 
Root Filesystem: /dev/sda2 
 

Network Interfaces (ip addr) 

Interface 
Network Type 
IP Address 
Purpose 
lo 
Loopback 
127.0.0.1 
Local processes 
enp0s3 
NAT 
10.0.2.15/24 
Internet access 
enp0s8 
Host-Only 
192.168.56.102/24 
Server communication 
 

 

 

Distribution Information (lsb_release) 

Distribution: Ubuntu 
Version: 24.04.3 LTS 
Codename: Noble 
Support: Long-Term Support (LTS) 
 

 

 

Final Summary 

In Phase 1, I successfully planned and deployed a secure VirtualBox lab environment consisting of: 

One isolated Ubuntu Server using Host-Only networking 
One Ubuntu Workstation using NAT + Host-Only networking 
This design ensures: 

Strong security through server isolation 
Reliable internal communication 
Safe and controlled internet access through the workstation only 
 
