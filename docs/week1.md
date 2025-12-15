Week 1 — System Planning & Distribution Selection
Overview
This phase covers the planning and setup of a VirtualBox lab environment using a Mac laptop as the host machine.
The environment consists of one Ubuntu Server and one Ubuntu Desktop Workstation, configured with appropriate network modes to ensure secure internal communication and controlled internet access.
Lab Systems Overview
Virtual Machines
System	OS Version	Network Mode	IP Address
Ubuntu Server	22.04 LTS	Host-Only	192.168.56.103/24
Ubuntu Workstation	24.04 LTS	NAT + Host-Only	192.168.56.102/24
Host Environment
Physical Host Machine: Mac Laptop
Virtualization Platform: Oracle VirtualBox
System Architecture Diagram

Figure 1: VirtualBox architecture showing Ubuntu Server and Workstation network segmentation.
Architecture Description
The lab environment consists of:
One Ubuntu Server VM connected only to the Host-Only network
One Ubuntu Workstation VM connected to NAT + Host-Only
A private Host-Only network for internal communication
A NAT network on the workstation for internet access
Design Benefits
Secure private communication between server and workstation
Internet access restricted to the workstation only
Server remains isolated from the internet for enhanced security
Distribution Selection Justification
Ubuntu Server (Selected)
Pros:
Beginner-friendly and suitable for coursework and lab environments
Large repository of up-to-date software packages
Active community with extensive documentation
Excellent compatibility with VirtualBox and cloud platforms
Frequent security updates with 5-year LTS support
Cons:
Slightly less stable than Debian for ultra-long-term production use
Higher resource usage than minimal distributions
Some enterprise features require Ubuntu Pro subscription
Debian
Pros:
Extremely stable and reliable
Excellent long-term performance
Strong security through strict package testing
Lightweight and suitable for low-spec systems
Cons:
Packages are often outdated
Requires more manual configuration
Documentation can be very technical for beginners
Less common in cloud environments compared to Ubuntu
Red Hat Enterprise Linux (RHEL)
Pros:
Enterprise-grade stability and performance
Strong built-in security features
Professionally supported
Widely used in corporate data centres
Cons:
Requires paid subscription
Not beginner-friendly
Limited free repositories
Slower software updates
Conclusion
Ubuntu Server was selected because it provides the best balance between ease of use, modern software availability, long-term support, strong community backing, and full compatibility with VirtualBox.
Debian is more stable but less beginner-friendly, while RHEL is enterprise-focused and requires a paid subscription.
Therefore, Ubuntu Server is the most effective choice for a learning and laboratory-based environment.
Workstation Configuration Decision
Workstation Configuration
Operating System: Ubuntu Desktop 24.04 LTS
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
A dual-adapter configuration was required to support both internet access and private server communication.
Rationale of Workstation Setup
NAT Adapter — Internet Access
NAT allows the workstation to access the internet through the host machine. This is required to:
Download system updates
Install tools (OpenSSH client, curl, browsers)
Access online documentation and learning resources
Advantages:
Plug-and-play configuration
No exposure to public networks
Secure outbound-only internet access
Host-Only Adapter — Internal Network Access
The Host-Only adapter provides a private LAN between:
Host machine
Ubuntu Server
Ubuntu Workstation
This enables:
Direct SSH access to the server
Secure internal testing
No exposure to the public internet
Advantages:
Static IP addressing
Predictable SSH connections
Secure isolated network
Reasons for Choosing Ubuntu Workstation
Ubuntu Workstation was selected because it fulfills all classroom and laboratory requirements.
Pros:
Easy-to-use graphical interface
Large software repository and community
Ideal for testing, learning, and rapid deployment
Long-term support releases
Excellent compatibility with VirtualBox
Why Not Alternatives:
Windows VM: High RAM usage, licensing costs
CentOS/RHEL Desktop: Complex and unsuitable for beginners
Debian Desktop: Older packages, harder configuration
Ubuntu Workstation provides the best balance of usability, performance, and compatibility for student use.
Network Configuration Documentation
Ubuntu Server Network Configuration
VirtualBox Settings:
Adapter 1 → Host-Only Adapter (vboxnet0)
IP Configuration:
Setting	Value
IP Address	192.168.56.103/24
Subnet Mask	255.255.255.0
Gateway	None
Internet Access	Disabled (Isolated)
Ubuntu Workstation Network Configuration
VirtualBox Settings:
Adapter 1 → NAT
Adapter 2 → Host-Only
Host-Only Configuration:
Setting	Value
IP Address	192.168.56.102/24
Subnet Mask	255.255.255.0
Gateway	192.168.56.1
NAT Configuration:
Automatic DHCP and DNS
Internet access enabled
System Specifications Documentation
Commands Used
uname
free -h
df -h
ip addr
lsb_release -a
System Information
uname -a
Kernel Version: 6.14.0-27-generic
Architecture: x86_64
Operating System: GNU/Linux
Memory Information
free -h
Total RAM: 3.8 GiB
Used RAM: 1.0 GiB
Available RAM: 2.8 GiB
Swap: 0 B
Disk Space
df -h
Disk Size: 25 GB
Used: 5.1 GB
Available: 19 GB
Root Filesystem: /dev/sda2
Network Interfaces
Interface	Network Type	IP Address	Purpose
lo	Loopback	127.0.0.1	Local processes
enp0s3	NAT	10.0.2.15/24	Internet access
enp0s8	Host-Only	192.168.56.102/24	Server communication
Distribution Information
lsb_release -a
Distribution: Ubuntu
Version: 24.04.3 LTS
Codename: Noble
Support: Long-Term Support
Final Summary
In Phase 1, a secure VirtualBox lab environment was successfully planned and deployed:
One isolated Ubuntu Server using Host-Only networking
One Ubuntu Workstation using NAT + Host-Only networking
This design ensures:
Strong security through server isolation
Reliable internal communication
Safe and controlled internet access via the workstation only
