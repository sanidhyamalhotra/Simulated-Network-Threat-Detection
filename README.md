# 🛡️ Simulated Network Threat Detection (Packet Tracer + Splunk)

## 📌 Project Overview

This project simulates a real-world enterprise network, introduces common cyber attacks, and demonstrates how to detect them using Splunk — a powerful SIEM tool.

> It’s a hands-on blueprint for how small-to-medium businesses (SMBs) can gain threat visibility using lightweight tools and practical detection logic.

---

## 🎯 Objectives

- Simulate a small enterprise network using Cisco Packet Tracer
- Generate both normal and malicious traffic (e.g., ARP spoofing, DNS spoofing, failed logins)
- Export and process network logs
- Ingest logs into **Splunk**
- Detect threats using **SPL queries**, dashboards, and alerts
- Package the whole project into a reusable blueprint for others

---

## 🛠️ What’s Inside (How It’s Built)

### 🔹 1. Network Simulation (Cisco Packet Tracer)
- Build a LAN with routers, switches, DNS server, web server, and client PCs
- Topology file: `PacketTracer/enterprise_network.pkt`

### 🔹 2. Threat Simulation
- Simulate:
  - ARP Poisoning
  - DNS Spoofing
  - Brute-force login attempts
- Export or replicate logs: `Logs/`

### 🔹 3. Log Analysis (Splunk)
- Install Splunk locally (or use Splunk Cloud trial)
- Ingest logs into Splunk
- Create detection logic with SPL
- Build dashboards for visibility

### 🔹 4. Documentation & Reuse
- All configs, logs, queries, and summaries are stored here on GitHub
- Anyone can reuse or modify for training, internal testing, or educational labs

---

## 💡 Why This Project Matters

Many companies, especially older or smaller ones, struggle with:

- Outdated network configurations
- No visibility into logs or threat activity
- Limited budgets for security tooling

This project shows how even a basic simulated network can help:

- Detect common attack patterns
- Learn Splunk fundamentals
- Improve security posture with low/no cost

✅ It’s useful for:
- Cybersecurity students
- SOC analyst trainees
- SMBs testing network awareness
- Instructors creating detection labs

---

## 🚀 Can you Use This Project?

Absolutely! This repo is public and designed to be **open-source and reusable** for learning or internal security awareness.

You can:
- Clone/fork it for your own simulations
- Modify the network topology or attack types
- Use it as a blueprint for your own detection labs

📄 If you'd like to contribute improvements or new detection rules, feel free to drop a comment or submit a pull request!

---

## 📦 Repository Structure

```
Simulated-Network-Threat-Detection/
├── PacketTracer/           → Topology files and diagrams
├── Attack_Scenarios/       → Summaries of attack methods
├── Logs/                   → Log files (normal and malicious)
├── Splunk/                 → SPL queries, dashboards, and alerts
├── Report/                 → Final summary or write-up
├── Demo_Video/ (optional)  → Demo walkthrough
└── README.md               → This file
```
