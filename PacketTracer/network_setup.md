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
![Network Topology](network_diagram.png)


## 🗺️ Topology Screenshot
`network_diagram.png` (save screenshot here)

## 📂 Save Packet Tracer File
`enterprise_network.pkt`
