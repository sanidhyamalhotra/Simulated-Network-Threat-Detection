# 🚀 Splunk Setup & Log Analysis Overview

This file explains how Splunk was used in this project to analyze various types of simulated and real network activity logs. It also documents the step-by-step process for uploading and analyzing log files, as well as the benefits of using Splunk for threat detection.

---

## ✅ What We Are Doing

We are using **Splunk Enterprise (Free Edition)** to:

- Ingest `.log` files generated from simulated and real attack scenarios
- Extract key patterns using **SPL** (Search Processing Language)
- Detect potential security threats such as:
  - ARP spoofing
  - Port scanning
  - Brute-force login attempts
- Visualize network activity to understand both normal and malicious behavior

---

## 🛠️ Log Files Used

| Log File | Purpose |
|----------|---------|
| `clean_logs.log` | Normal baseline traffic |
| `arp_attack_real_log.log`        | ARP spoofing attack |
| `port_scan_log.log`              | Nmap port scan activity |
| `brute_force_log.log`            | SSH brute-force login attempts |

Each log file is mapped to a `sourcetype` in Splunk and analyzed using `.spl` scripts found in:
Splunk/queries/<scenario_name>/

---

## 📥 Step-by-Step Log Ingestion in Splunk

1. Open **http://localhost:8000**
2. Log in to Splunk (admin user)
3. Click **Settings → Add Data**
4. Choose **Upload → Select File**
5. Upload one `.log` file (e.g., `arp_attack_real_log.log`)
6. On the source type screen:
   - Choose `Set source type manually`
   - Use meaningful name like `arp_logs`, `port_scan`, etc.
7. Select or create an index:
   - Recommended: use a single index like `network_logs`
8. Click **Start Searching**

Repeat these steps for each log file.

---

## 🔍 Querying and Analysis

- Open the **Search & Reporting** app
- Use `.spl` queries located in each scenario’s folder
- View data in:
  - **Events Tab**: Raw data entries
  - **Statistics Tab**: Structured counts
  - **Visualization Tab**: Graphs, bar charts, and timelines

---

## 🧠 Why Splunk is Useful for This Project

| Benefit | Description |
|---------|-------------|
| 🔎 Fast Pattern Matching | SPL makes it easy to search and filter logs by keywords, fields, and IPs |
| 📈 Visualization | Instantly turn queries into charts and dashboards |
| 🧩 Modular Queries | Each `.spl` file can be reused in other environments (SOC, SIEM, ELK) |
| 🔄 Easy to Extend | New logs or attack types can be added anytime |
| 🧠 Learning Opportunity | Helps students understand threat detection logic |

---

## ✅ Summary

Splunk was used to simulate the process of a real Security Operations Center (SOC) by:

- Uploading various network logs
- Writing detection rules in SPL
- Visualizing potential threats
- Documenting the results per attack scenario

Each detection scenario is stored in its own folder with:
- `queries/*.spl` → Search queries
- `queries/*.md` → Explanation and screenshots

---
