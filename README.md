# 🛡️ Simulated Network Threat Detection (Packet Tracer + GNS3 + Splunk)

## 📌 Project Overview

This project simulates a real-world enterprise network, introduces common cyber attacks, and demonstrates how to detect them using both simulated logs and a real lab environment. It uses tools like Cisco Packet Tracer, Kali Linux, GNS3, and Splunk — a powerful SIEM platform.

> A hands-on blueprint for cybersecurity students, small businesses, or trainers to build network visibility and attack detection capabilities.

---

## 🎯 Objectives

- Simulate a small enterprise network using **Cisco Packet Tracer**
- Set up a real network attack lab using **Kali Linux and GNS3**
- Generate both normal and malicious traffic (e.g., ARP spoofing)
- Capture and document logs from both simulated and real sources
- Ingest logs into **Splunk** and write SPL queries for detection
- Package the project into a clean, open-source structure for learning and reuse

---

## 🛠️ What’s Inside (How It’s Built)

### 🔹 Phase 1: Simulated Environment (Packet Tracer)
- Built a LAN with routers, switches, DNS/web servers, and client PCs
- Normal traffic and CLI logs saved
- Topology file: `PacketTracer/enterprise_network.pkt`

### 🔹 Phase 2: Real Lab (Kali + GNS3)
- Kali Linux VM connected to GNS3 via `VMnet1`
- VPCS used as the simulated victim (PC1)
- Ran live `arpspoof` attack from Kali
- Captured output and documented every step

### 🔹 Log Analysis (Splunk)
- Logs can be ingested into Splunk or ELK Stack
- Includes timestamps and `.log` formatted text
- Supports timeline correlation and event detection

### 🔹 Documentation & Reuse
- All attack steps, topology screenshots, and logs are included
- Markdown files explain each phase and how to reproduce it

---

## 💡 Why This Project Matters

Many organizations struggle with:
- Outdated infrastructure
- No centralized logging
- No visibility into attacker activity

This project helps:
- Understand how attacks like ARP spoofing work
- Learn detection fundamentals in Splunk
- Practice setting up a working network lab
- Build a portfolio-ready case study

✅ Great for:
- Cybersecurity students
- SOC analyst trainees
- SMB security consultants
- Classroom labs or bootcamps

---

## 🚀 Can You Use This Project?

Yes! Fork, clone, remix, or adapt this for:

- Assignments
- Student labs
- Training modules
- Proof-of-concept detection testing

📄 Contributions welcome — feel free to open issues or PRs.

---

## 📦 Repository Structure

```
Simulated-Network-Threat-Detection/
├── PacketTracer/ → Topology files and diagrams
├── GNS3_Simulation/ → Real ARP spoofing lab with Kali + GNS3
├── Attack_Scenarios/ → Summaries of attack methods
├── Logs/ → Log files (normal and malicious)
├── Splunk/ → SPL queries, dashboards, and alerts
├── Report/ → Final summary or write-up
├── Wireshark/ → Packet captures (.pcap) from real lab
└── README.md → This file
```