# 🔐 Splunk Query Analysis – Brute-Force Login Attack

This file documents how brute-force login attempts were analyzed in Splunk using log data from `brute_force_log.log`.

---

## 🔍 Query 1: View All Brute-Force Log Events
```
sourcetype="brute_force"
```
Displays all events related to login attempts. Useful for verifying ingestion.


## 🔍 Query 2: Detect All Failed Login Attempts
```
sourcetype="brute_force" "Failed login"
| stats count by _time, _raw
```
Shows every failed login with a timestamp.


## 📊 Query 3: Count Failed Logins Per IP
```
sourcetype="brute_force" "Failed login"
| rex field=_raw "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count > 3
```
Highlights IPs responsible for suspicious login volume — classic brute-force red flag.

🖼️ Screenshot: login_attempts_by_ip.png

## 📋 Query 4: Failed Logins Per Username
```
sourcetype="brute_force" "Failed login"
| rex field=_raw "user: (?<user>\w+)"
| stats count by user
```
Lists failed attempts by targeted usernames — helpful for attack targeting insights.

🖼️ Screenshot: login_attempts_by_user.png

