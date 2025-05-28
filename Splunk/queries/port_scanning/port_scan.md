# 🔎 Splunk Query Analysis – Port Scanning

This file documents how port scanning activity was analyzed using log data ingested from `port_scan_log.log`.

---

## 🔍 Query 1: View All Scan Events
```
sourcetype="port_scan"
```
Displays all lines from the Nmap scan log.
<img width="959" alt="scan_events_raw" src="https://github.com/user-attachments/assets/ef3a265e-5a6c-48e4-a9ca-4221618c19e2" />


## 🔍 Query 2: Most Frequently Detected Open Ports
```
sourcetype="port_scan"
| rex field=_raw "open port (?<port>\d+)/tcp"
| stats count by port
| sort - count
```
Extracts open ports and shows which ones were detected most often.
<img width="959" alt="port_count_output" src="https://github.com/user-attachments/assets/3e1f8754-1a6e-46c3-84b0-c507f6b86d69" />


## 🔍 Query 3: Number of Ports Detected Per Target
```
sourcetype="port_scan"
| rex field=_raw "open port (?<port>\d+)/tcp on (?<target_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by target_ip
```
Counts how many ports were discovered on each IP.
<img width="959" alt="target_port_count" src="https://github.com/user-attachments/assets/166340f4-9bf6-4ca8-bb0c-3e8d2d1193af" />


## 🔍 Query 4: Timeline of Port Scan Activity
```
sourcetype="port_scan"
| timechart count
```
Visualizes how many lines/events occurred over time (scan rate).
<img width="959" alt="scan_timeline" src="https://github.com/user-attachments/assets/8c69733a-8ff9-4d01-b97f-c270fe2701df" />

