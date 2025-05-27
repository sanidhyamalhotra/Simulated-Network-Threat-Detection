# 🔍 Port Scanning Attack – Real Lab (GNS3 + Kali)

## 📌 What is Port Scanning?

Port scanning is a common reconnaissance technique used by attackers to discover open ports and services running on a target device. It's often one of the first steps in identifying vulnerabilities.

---

## 🛠️ Lab Setup Overview

This attack was performed in a real lab using **Kali Linux inside VMware**, connected to a **victim VPCS node in GNS3** via **VMnet1**.

### Devices Involved:
| Role      | IP Address         | Notes                        |
|-----------|--------------------|------------------------------|
| Kali VM   | 192.168.15.130     | Attacker                     |
| VPCS Node | 192.168.15.100     | Victim (simulated PC)        |

---

## 🔧 Command Used

```bash
nmap -sS -Pn 192.168.15.100 -p 1-1000 -v


🔍 Breakdown of Command:
```
Flag	Purpose
nmap	Network mapping tool
-sS	TCP SYN Scan – stealthy, fast
-Pn	Skip host discovery – assume host is up
-p 1-1000	Scan ports 1 to 1000
-v	Verbose output for more detail
```