# 📊 Splunk Query Analysis – Clean Logs

This document explains the queries executed against the `clean_logs.log` file in Splunk and what each query reveals about normal network behavior.

---

## 🔍 Query 1: View All Events
```
sourcetype="Clean_logs"
```
Displays all raw log lines ingested. Used to verify ingestion
<img width="959" alt="raw_log_output" src="https://github.com/user-attachments/assets/b0874047-aa7a-4ae0-8ea2-1f99b039c386" />


## 🔍 Query 2: Timechart of Event Frequency
```
sourcetype="Clean_logs"
| timechart count
```
Generates a timeline graph showing number of events over time.
<img width="959" alt="timechart_output" src="https://github.com/user-attachments/assets/ef78db77-4993-42a5-8a38-5c6ee6931fdd" />


## 🔍 Query 3: Most Pinged IP Addresses
```
sourcetype="Clean_logs"
| rex field=_raw "ping (?<target_ip>\\d+\\.\\d+\\.\\d+\\.\\d+)"
| stats count by target_ip
```
Extracts and counts ping targets to analyze which hosts were pinged most often.
<img width="959" alt="ping_stats_output" src="https://github.com/user-attachments/assets/7d3f29a8-2edd-43ac-8fd8-12bbd250d906" />


## 🔍 Query 4: Top 5 Most Common Log Lines
```
sourcetype="Clean_logs"
| top limit=5 _raw
```
Shows the most frequently repeated lines in the clean logs.
<img width="959" alt="top_lines_output" src="https://github.com/user-attachments/assets/39aa94c7-e5f8-48a8-93c1-27d4255313b8" />

