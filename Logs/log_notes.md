# 📁 Log Files Overview

This folder contains all the raw logs collected from various stages of the network simulation. These logs are used to simulate both normal and malicious behavior in the network, which are later ingested into Splunk for detection and analysis.

---

## 🟢 clean_logs.log

### ✅ Purpose:
This file contains **normal, baseline activity** in the network. No attacks are performed here.

### ✅ Captured:
- From PC1 and PC2 (Packet Tracer)
- Ping tests to router, web server, DNS, and each other
- Includes simulated timestamps for realism
- Used to compare against future attack behavior


## 🔥 arp_attack_real_log.log

### ✅ Purpose:
This file captures a **real ARP spoofing attack** executed from Kali Linux in GNS3.

### ✅ Captured:
- From Kali: Terminal output of `arpspoof`
- ARP reply flood toward victim device (`192.168.15.100`)
- Simulates a live man-in-the-middle redirection scenario

---

## 📂 File Format
All logs are saved as `.log` files using raw text format. These logs are either simulated (Packet Tracer) or directly extracted from real terminal sessions (Kali).

---

## 📌 Usage
These logs can be ingested into Splunk using:
- File upload method
- Assigned custom source types (`clean_traffic`, `arp_attack`, `real_arp_attack`)
- Timeline-based detection using included timestamps or event gaps