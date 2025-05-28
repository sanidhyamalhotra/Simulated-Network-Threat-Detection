# 🔐 Splunk Query Analysis – Brute-Force Login Attack

This file documents how brute-force login attempts were analyzed in Splunk using log data from `brute_force_log.log`.

---

## 🔍 Query 1: View All Brute-Force Log Events
```
sourcetype="brute_force"
```
Displays all events related to login attempts. Useful for verifying ingestion.
<img width="959" alt="brute_force_raw" src="https://github.com/user-attachments/assets/00154f68-d37c-471a-818a-eaff6bc0fc04" />


## 🔍 Query 2: Detect All Failed Login Attempts
```
sourcetype="brute_force" "Failed login"
| stats count by _time, _raw
```
Shows every failed login with a timestamp.
<img width="959" alt="failed_login_list" src="https://github.com/user-attachments/assets/257bc9f6-a199-4091-b4cf-8c853cba555d" />


## 📊 Query 3: Count Failed Logins Per IP
```
sourcetype="brute_force" "Failed login"
| rex field=_raw "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count > 3
```
Highlights IPs responsible for suspicious login volume — classic brute-force red flag.
<img width="959" alt="login_attempts_by_ip" src="https://github.com/user-attachments/assets/5ad2050d-8b5a-4368-8680-db190c26405e" />


## 📋 Query 4: Failed Logins Per Username
```
sourcetype="brute_force" "Failed login"
| rex field=_raw "user: (?<user>\w+)"
| stats count by user
```
Lists failed attempts by targeted usernames — helpful for attack targeting insights.
<img width="959" alt="login_attempts_by_user" src="https://github.com/user-attachments/assets/2930be14-b220-4989-8584-d9ff115827a2" />

