# 📁 Log Files Overview

This folder contains all the raw logs collected from various stages of the network simulation. These logs are used to simulate both normal and malicious behavior in the network, which are later ingested into Splunk for detection and analysis.

---

## 🟢 clean_logs.log

### ✅ Purpose:
This file contains **normal, baseline activity** in the network. No attacks are performed here.

### ✅ Captured:
- From PC1 and PC2
- Ping tests to router, web server, DNS, and each other
- Includes simulated timestamps for realism
- Used to compare against future attack behavior

---

## 🔴 arp_attack.log

### ✅ Purpose:
This file contains logs captured during a **simulated ARP poisoning attack**.

### ✅ Captured:
- From PC2: ARP spoofing command (`arp -s`)
- From PC1: ARP table before/after
- Ping results possibly affected by altered routing
- Demonstrates what a red flag would look like in logs

---

## 📂 File Format
All logs are saved as `.log` files using raw text format. These logs are manually collected from Packet Tracer CLI and formatted for Splunk ingestion.

---

## 📌 Usage
These logs can be ingested into Splunk using:
- File upload method
- Assigned custom source types (`clean_traffic`, `arp_attack`, etc.)
- Timeline-based detection using included timestamps
