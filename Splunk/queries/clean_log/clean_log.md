# 📊 Splunk Query Analysis – Clean Logs

This document explains the queries executed against the `clean_logs.log` file in Splunk and what each query reveals about normal network behavior.

---

## 🔍 Query 1: View All Events
```
sourcetype="Clean_logs"
```
Displays all raw log lines ingested. Used to verify ingestion
![alt text](raw_log_output.png)


## 🔍 Query 2: Timechart of Event Frequency
```
sourcetype="Clean_logs"
| timechart count
```
Generates a timeline graph showing number of events over time.
![alt text](timechart_output.png)


## 🔍 Query 3: Most Pinged IP Addresses
```
sourcetype="Clean_logs"
| rex field=_raw "ping (?<target_ip>\\d+\\.\\d+\\.\\d+\\.\\d+)"
| stats count by target_ip
```
Extracts and counts ping targets to analyze which hosts were pinged most often.
![alt text](ping_stats_output.png)


## 🔍 Query 4: Top 5 Most Common Log Lines
```
sourcetype="Clean_logs"
| top limit=5 _raw
```
Shows the most frequently repeated lines in the clean logs.
![alt text](top_lines_output.png)