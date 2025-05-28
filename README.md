# 🛡️ Simulated Network Threat Detection (Packet Tracer + GNS3 + Splunk)

## 📌 Project Overview

This project simulates a real-world enterprise network, introduces common cyber attacks, and demonstrates how to detect them using both simulated and real lab environments. It leverages tools like **Cisco Packet Tracer**, **Kali Linux**, **GNS3**, and **Splunk** — a powerful SIEM platform used by security professionals.

> 🎓 It serves as a hands-on blueprint for students, SMBs, or trainers to build network visibility and attack detection capabilities using affordable, open tools.

---

## 🎯 Objectives

- Simulate a small enterprise network using **Cisco Packet Tracer**
- Set up a real attack lab using **Kali Linux + GNS3**
- Generate both normal and malicious network activity
- Capture logs from **both simulated and real attacks**
- Ingest logs into **Splunk**
- Write detection queries using **SPL**
- Package it all into a clean, open-source documentation project

---

## 🛠️ What’s Inside (How It’s Built)

### 🔹 Phase 1: Simulated Environment (Packet Tracer)
- LAN topology with router, switch, web server, DNS, and 2 PCs
- Generated clean ICMP traffic logs
- Saved CLI logs and topology visuals
- 📂 `PacketTracer/`

### 🔹 Phase 2: Real Lab (Kali + GNS3)
- Kali VM connected to GNS3 via VMnet1
- VPCS node used as a vulnerable PC
- Ran **live ARP spoofing**, **Nmap port scanning**, and **Hydra brute-force** attacks
- Captured logs and screenshots of real attack behavior
- 📂 `GNS3_Simulation/`

### 🔹 Log Collection & Analysis (Splunk)
- Logs saved as `.log` files with timestamps
- Each log assigned a custom sourcetype in Splunk
- Detection queries written in SPL per attack
- 📂 `Splunk/queries/<attack_type>/`

### 🔹 Documentation & Reporting
- Markdown files explain every phase, attack, and query
- Screenshots included in `.md` files
- GitHub-ready for public reuse
- 📂 `Attack_Scenarios/` + `Report/`

---

## 💡 Why This Project Matters

Many orgs — especially small or academic — struggle with:
- Outdated infrastructure
- No centralized logging
- Little understanding of real attacker behavior

This project helps:
- Build end-to-end detection skills
- Practice **network monitoring and SIEM use**
- Understand **common attack patterns**
- Create a **portfolio-worthy capstone project**

---

## ✅ Who This Project is Great For

- Cybersecurity students and SOC analysts
- Instructors and lab creators
- Small businesses wanting to test basic security
- Anyone learning Splunk, packet analysis, or log correlation

---

## 🚀 Can You Use This Project?

**Yes!** You are encouraged to:
- Clone, fork, or remix it
- Use it for classes, training, bootcamps
- Build on it with more attacks or detections

📄 Contributions welcome — open issues or PRs to improve this resource.

---

## 📦 Repository Structure

```
Simulated-Network-Threat-Detection/
├── PacketTracer/ → Topology files and diagrams
├── GNS3_Simulation/ → Real ARP/scan/brute-force attacks (Kali + VPCS)
├── Attack_Scenarios/ → Step-by-step attack explanations
├── Logs/ → Raw .log files (normal + attack)
├── Splunk/ → SPL queries, visualizations, and documentation
│ ├── queries/
│ │ ├── clean_log/
│ │ ├── arp_spoofing/
│ │ ├── port_scanning/
│ │ └── brute_force/
│ └── splunk_setup.md → How to ingest + analyze logs
├── Wireshark/ → Optional: packet captures (.pcap)
├── Report/ → Final write-up or summary
└── README.md → This file
```
