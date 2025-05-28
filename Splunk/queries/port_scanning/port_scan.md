# 🔎 Splunk Query Analysis – Port Scanning

This file documents how port scanning activity was analyzed using log data ingested from `port_scan_log.log`.

---

## 🔍 Query 1: View All Scan Events
```
sourcetype="port_scan"
```
Displays all lines from the Nmap scan log.


## 🔍 Query 2: Most Frequently Detected Open Ports
```
sourcetype="port_scan"
| rex field=_raw "open port (?<port>\d+)/tcp"
| stats count by port
| sort - count
```
Extracts open ports and shows which ones were detected most often.


## 🔍 Query 3: Number of Ports Detected Per Target
```
sourcetype="port_scan"
| rex field=_raw "open port (?<port>\d+)/tcp on (?<target_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by target_ip
```
Counts how many ports were discovered on each IP.

## 🔍 Query 4: Timeline of Port Scan Activity
```
sourcetype="port_scan"
| timechart count
```
Visualizes how many lines/events occurred over time (scan rate).