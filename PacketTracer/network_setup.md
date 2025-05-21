# 🌐 Network Setup

## 🎯 Objective
Create a simulated enterprise network with basic routing and servers to later test for attack detection.

## 🧱 Devices Used

| Device         | IP Address     | Purpose         |
|----------------|----------------|-----------------|
| Router         | 192.168.1.1     | Gateway          |
| PC1 (User)     | 192.168.1.10    | Normal user      |
| PC2 (Attacker) | 192.168.1.11    | Runs attacks     |
| DNS Server     | 192.168.1.2     | Resolves domains |
| Web Server     | 192.168.1.3     | Target for traffic|


## 🛠️ How I Built the Network

1. Opened Cisco Packet Tracer and started a new project
2. Added the following devices:
   - 1 Router (1841)
   - 1 Switch (2960)
   - 2 PCs
   - 2 Servers (for DNS and Web)
3. Connected everything using copper straight-through cables
4. Assigned IPs manually to each device
5. Configured gateway: All devices use 192.168.1.1
6. Saved the file as `enterprise_network.pkt` and added a screenshot below

📸 Screenshot:  
![Network Topology]
![image](https://github.com/user-attachments/assets/306da64a-f17b-4eeb-bd32-b8af4ea42b50)

## 🔎 How to Verify the Network is Working

After building the network and assigning IP addresses, follow these steps to ensure all devices are connected correctly and can communicate.

### ✅ 1. Check Interface Lights
- Green = active connection ✅
- Red = link down ⚠️
- Orange = initializing (wait a few seconds)

### ✅ 2. Ping Devices
Open the **Command Prompt** on each PC (Desktop tab → Command Prompt):

From **PC1**, test:
ping 192.168.1.1 # Ping the router
ping 192.168.1.2 # Ping the DNS server
ping 192.168.1.3 # Ping the web server
ping 192.168.1.11 # Ping PC2

✅ If you see replies, everything is working.

### ✅ 3. Check Router Interface Status
On the Router (CLI tab), type:
enable
show ip interface brief

You should see:
FastEthernet0/0 192.168.1.1 YES manual up up

If it's not `up`, run:
configure terminal
interface FastEthernet0/0
no shutdown

## 🧾 Clean Network Logs

These logs were captured by simulating normal traffic in the network before any attacks were launched.

### ✅ Activities Performed:
- Ping from PC1 to Web Server, DNS, and PC2
- Ping from PC2 to Router and PC1

### 📄 Log File:
Save the CLI output to a log file inside log folder
See `Logs/clean_logs.log` for full output


## 🗺️ Topology Screenshot
`network_diagram.png` (save screenshot here)

## 📂 Save Packet Tracer File
`enterprise_network.pkt`
