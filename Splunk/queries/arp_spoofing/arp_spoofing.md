# 🛡️ Splunk Query Analysis – ARP Spoofing

This file documents how ARP spoofing was detected and analyzed using log data ingested from `arp_attack_real_log.log`.

---

## 🔍 Query 1: View All ARP Reply Events
```
sourcetype="arp_logs" "is-at"
```
Lists all ARP replies recorded in the log.



## 🔍 Query 2: Detect Conflicting MAC Addresses
```
sourcetype="arp_logs" "is-at"
| rex field=_raw "(?<ip_address>\d+\.\d+\.\d+\.\d+).*is-at (?<mac_address>\S+)"
| stats dc(mac_address) as mac_count by ip_address
```
This identifies cases where more than one MAC address claims the same IP address — a strong indicator of ARP spoofing.


## 🔍 Query 3: Table of IP ↔ MAC Mapping
```
sourcetype="arp_logs" "is-at"
| rex field=_raw "(?<ip_address>\d+\.\d+\.\d+\.\d+).*is-at (?<mac_address>\S+)"
| table _time, ip_address, mac_address
```
Lists every IP-MAC pair observed, along with the timestamp.


## 🔍 Query 4: ARP Reply Timeline
```
sourcetype="arp_logs" "is-at"
| timechart count
```
Plots ARP reply frequency over time — useful for spotting spikes during an attack.


