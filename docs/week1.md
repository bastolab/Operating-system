👉 Anything inside ``` ``` is treated as **code**, not rendered content.  
So GitHub shows text instead of the image.

---

## ✅ FINAL FIX (IMPORTANT RULE)

❌ **REMOVE** the triple backticks  
✅ Image Markdown must be **plain text**

---

## ✅ FINAL CORRECT VERSION (COPY-PASTE THIS)

Replace your current content with **this corrected version** 👇

---

## Week 1 — System Architecture & Environment Planning

Home | Week 1 | Week 2 →

---

## Overview

Week 1 focuses on planning the system architecture and deployment environment for a Linux server before installation. This includes defining the host setup, virtualization strategy, network topology, and directory structure. The objective is to establish a clear, reproducible foundation that supports security, performance monitoring, and future scalability.

---

## Objectives

- Design the overall system architecture  
- Select host OS and virtualization platform  
- Define network configuration and addressing  
- Plan directory structure and repository organization  
- Prepare environment for secure remote management  

---

## Deliverables

- System architecture diagram  
- Virtualization and network design  
- Planned directory and repository structure  
- Evidence of host and VM environment setup  

---

## 1. System Architecture Design

### 1.1 High-Level Architecture

**Architecture Description**

- Host machine runs macOS  
- Virtualization provided via VirtualBox  
- Ubuntu Server runs as a guest VM  
- Management performed remotely via SSH  
- Isolated host-only network for secure access  

📸 **Screenshot / Diagram**  
Filename: `week1-system-architecture.png`

![System Architecture Diagram](../imagescreenshots/week1/week1-system-architecture.png)

**Figure W1-1:** High-level system architecture showing host, virtual machine, and management access.

---

## 1.2 Host Environment

**Host System**

- Operating System: macOS  
- Role: Development workstation and management console  

**Responsibilities**

- SSH access  
- Monitoring execution  
- Evidence collection  
- GitHub repository management  

📸 **Screenshot**  
Filename: `week1-host-info.png`

![Host System Information](../imagescreenshots/week1/week1-host-info.png)

**Figure W1-2:** Host system information confirming development environment.

---
