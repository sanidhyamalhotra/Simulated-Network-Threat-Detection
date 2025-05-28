# 🛡️ Splunk Query Analysis – ARP Spoofing

This file documents how ARP spoofing was detected and analyzed using log data ingested from `arp_attack_real_log.log`.

---

## 🔍 Query 1: View All ARP Reply Events
```
sourcetype="arp_logs" "is-at"
```
Lists all ARP replies recorded in the log.
<img width="959" alt="arp_replies_list" src="https://github.com/user-attachments/assets/c0f17886-4200-4481-82e3-4ac736284a3c" />


## 🔍 Query 2: Detect Conflicting MAC Addresses
```
sourcetype="arp_logs" "is-at"
| rex field=_raw "(?<ip_address>\d+\.\d+\.\d+\.\d+).*is-at (?<mac_address>\S+)"
| stats dc(mac_address) as mac_count by ip_address
```
This identifies cases where more than one MAC address claims the same IP address — a strong indicator of ARP spoofing.
<img width="959" alt="mac_conflict_output" src="https://github.com/user-attachments/assets/843f3e88-8245-4318-b934-086d29353a3d" />


## 🔍 Query 3: Table of IP ↔ MAC Mapping
```
sourcetype="arp_logs" "is-at"
| rex field=_raw "(?<ip_address>\d+\.\d+\.\d+\.\d+).*is-at (?<mac_address>\S+)"
| table _time, ip_address, mac_address
```
Lists every IP-MAC pair observed, along with the timestamp.
<img width="959" alt="ip_mac_table" src="https://github.com/user-attachments/assets/6b9d04f2-072d-4c1d-8e93-08fb33c8ee87" />


## 🔍 Query 4: ARP Reply Timeline
```
sourcetype="arp_logs" "is-at"
| timechart count
```
Plots ARP reply frequency over time — useful for spotting spikes during an attack.
<img width="959" alt="arp_timeline" src="https://github.com/user-attachments/assets/5bf41a93-d8e7-4cf2-bead-8457ec30c2ad" />

