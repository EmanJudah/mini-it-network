# 🧩 Mini IT Network (Virtual Lab)

This project simulates a **mini IT network** using virtualization software (**UTM**) on macOS.  
It demonstrates how a Windows-based server and a Linux client can communicate within an **isolated internal LAN** — a foundational setup for IT support and networking roles.

---

## 💡 Overview

The goal of this project is to create a **local network environment** with:
- A **Windows 11 Pro** machine acting as a **DHCP + DNS Server**
- An **Ubuntu Server 24.04** machine acting as a **Client**
- A **Private Internal Network** inside UTM, without internet access

This setup replicates a basic office LAN where a server manages IP distribution and network configuration for connected clients.

---

## ⚙️ Architecture

| Component | Role | Description |
|------------|------|-------------|
| 🪟 **Windows 11 Pro** | Server | Configured as a DHCP server using DHCP Server v2.5.2 to assign IPs and manage DNS queries |
| 🐧 **Ubuntu Server 24.04** | Client | Receives its IP dynamically from the Windows DHCP server |
| 🌐 **UTM Internal Network** | Network Medium | Connects both machines in a private 192.168.64.0/24 LAN |

---

## 🔧 DHCP Configuration (Windows)

| Setting | Value |
|----------|--------|
| **IP Range (Pool)** | 192.168.64.10 – 192.168.64.50 |
| **Subnet Mask** | 255.255.255.0 |
| **Gateway** | 192.168.64.2 |
| **DNS Server** | 192.168.64.2 |

DHCP Server tool: [dhcpserver.de](https://www.dhcpserver.de/cms/download/)

---

## 🧠 Ubuntu Network Verification

Ubuntu automatically obtained an IP address (`192.168.64.3`) from the Windows DHCP Server.

To verify network connectivity:
```bash
ip a
ping 192.168.64.2
