# NETWORKWALKS-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP



## 🔐 Virtual Cybersecurity Lab Environment

### Project Overview

This project demonstrates the creation of a controlled and isolated cybersecurity laboratory using **Oracle VM VirtualBox and Kali Linux**.

The lab provides a safe environment for learning and practicing basic cybersecurity activities such as network discovery, packet analysis, reconnaissance, and security investigation without directly affecting the host operating system or external networks.

---

## 🎯 Project Goals

The main goals of this laboratory setup were:

- Install and configure Oracle VM VirtualBox.
- Deploy Kali Linux as the security-testing virtual machine.
- Create an isolated **NAT Network** for laboratory communication.
- Configure a static IPv4 address for the Kali VM.
- Verify network connectivity between the virtual environment and gateway.
- Create a VM snapshot for recovery and experimentation.
- Document configuration issues and their solutions.

---

# 🏗️ Laboratory Architecture

| Component | Configuration |
|---|---|
| Host Operating System | Windows 10 |
| Host RAM | 8 GB |
| Hypervisor | Oracle VM VirtualBox 7.2 |
| Guest Operating System | Kali Linux 2026.3 |
| VM Memory | 2 GB |
| Network Type | VirtualBox NAT Network |
| Network Range | 10.0.0.0/24 |
| Kali IPv4 | 10.0.0.2/24 |
| Default Gateway | 10.0.0.1 |
| DNS | 8.8.8.8 |

### Network Layout

```text
                 Windows 10 Host
                        │
                 Oracle VirtualBox
                        │
              ┌─────────┴─────────┐
              │    NAT Network    │
              │   10.0.0.0/24     │
              │                   │
              │ Gateway: 10.0.0.1 │
              │                   │
              │ Kali: 10.0.0.2    │
              └───────────────────┘
```

---

# ⚙️ Environment Deployment

## 1. Installing Required Software

The first stage involved installing the necessary virtualization and extraction utilities.

### Software Used

- 7-Zip
- Oracle VM VirtualBox
- Kali Linux Virtual Machine

Official resources:

- 7-Zip: https://7-zip.org/download.html
- VirtualBox: https://virtualbox.org/wiki/Downloads
- Kali Linux: https://kali.org/get-kali

---

## 2. Creating the Virtual Network

A dedicated VirtualBox **NAT Network** was created to keep the laboratory traffic within the virtual environment.

### Network Configuration

```text
Network Name: NatNetwork
IPv4 Network: 10.0.0.0/24
Gateway:      10.0.0.1
```

Using a dedicated NAT Network allows virtual machines to communicate through the same private virtual network while keeping the lab separated from the physical network.

---

## 3. Kali Linux Deployment

The Kali Linux virtual machine was imported into VirtualBox and assigned appropriate virtual hardware resources.

### VM Configuration

```text
Operating System : Kali Linux
Memory           : 2 GB
Network Adapter  : NAT Network
Network          : NatNetwork
```

The network adapter was connected to the previously created private NAT Network.

---

## 4. Static Network Configuration

The Kali Linux system was configured with a static IPv4 address so that the machine could maintain a predictable address inside the lab.

```text
IPv4 Address : 10.0.0.2
Subnet Mask  : 255.255.255.0
Gateway      : 10.0.0.1
DNS Server   : 8.8.8.8
```

Static addressing makes it easier to identify the security-testing machine during network analysis and future lab exercises.

---

## 5. Snapshot Creation

After completing the initial configuration, a clean VM snapshot was created.

### Snapshot

```text
Snapshot Name: Lab Setup
```

The snapshot provides a recovery point that can be restored if future testing changes or damages the virtual machine configuration.

---

# 🧪 Network Validation

After completing the configuration, basic connectivity checks were performed from the Kali Linux environment.

### Validation Checklist

| Test | Purpose | Expected Result |
|---|---|---|
| IP configuration check | Confirm assigned address | `10.0.0.2` |
| Gateway test | Verify local network connectivity | Successful |
| DNS test | Verify name resolution | Successful |
| Network interface check | Confirm adapter status | Active |
| Snapshot verification | Confirm rollback point | Available |

Example commands used for basic verification:

```bash
ip addr
```

```bash
ip route
```

```bash
ping -c 4 10.0.0.1
```

```bash
ping -c 4 8.8.8.8
```

---

# 🔎 Security Analysis Environment

The configured laboratory can later be used for controlled cybersecurity exercises such as:

- Network reconnaissance
- TCP/IP traffic inspection
- Port and service identification
- Wireshark packet analysis
- HTTP traffic investigation
- Network troubleshooting
- Basic vulnerability assessment
- Security-event investigation

All testing should remain limited to systems and networks that are intentionally created or authorized for the lab.

---

# 🛠️ Issues Encountered

## Issue 01 — Windows Security Detection

During the Kali Linux VM deployment process, Windows security software detected potentially unwanted or suspicious components within the Kali package.

### Resolution

Instead of treating security warnings as something to permanently ignore, the lab files were handled carefully and the security software was restored/enabled after the required setup process.

> **Security Note:** Disabling host antivirus protection should be avoided whenever possible. If testing requires a security exception, it should be temporary and limited to a trusted source/file.

---

## Issue 02 — Kali Network Configuration Problem

The Kali VM initially experienced network connectivity problems after deployment.

### Investigation

The problem was related to the interaction between the VirtualBox network adapter configuration and the intended static network configuration.

### Resolution

The adapter was connected to the correct NAT Network and the Kali network settings were manually configured with the required static IPv4 parameters.

Final configuration:

```text
IP       : 10.0.0.2/24
Gateway  : 10.0.0.1
DNS      : 8.8.8.8
```

Connectivity was then tested again to confirm the configuration.

---

# 📸 Evidence

Screenshots captured during the project include:

1. VirtualBox NAT Network configuration
2. Kali Linux VM hardware settings
3. Kali network configuration
4. VirtualBox snapshot
5. Network connectivity verification

These screenshots provide evidence of the completed laboratory setup.

---

# 🧠 Key Learning Outcomes

Through this exercise, I learned:

- How virtualization can be used to create cybersecurity training environments.
- The difference between standard NAT and VirtualBox NAT Network.
- How to assign and verify static IPv4 configurations in Kali Linux.
- How snapshots help maintain safe recovery points.
- How to troubleshoot basic virtual network connectivity issues.
- The importance of isolating security-testing activities from production systems.
- How to document technical configurations in a reproducible manner.

---

# 🔗 Resources

**7-Zip**  
https://7-zip.org/download.html

**Oracle VirtualBox**  
https://virtualbox.org/wiki/Downloads

**Kali Linux**  
https://kali.org/get-kali

---

# 👤 Author

**PREOSHREE RANI DATTA**

Cybersecurity Intern — Batch B084

**Program:** Networkwalks Cybersecurity Internship  
**Week:** 01

**LinkedIn:**  
https://lnkd.in/p/gFFUXuxF



**GitHub:**  
https://github.com/preoshree/NETWORKWALKS-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP/tree/main

---

## ✅ Project Status

**Status:** Completed

**Environment:** Isolated Virtual Cybersecurity Lab

**Primary Tools:** VirtualBox + Kali Linux

**Lab Network:** `10.0.0.0/24`

**Kali Address:** `10.0.0.2`
