# 🛠️ GNS3 + Kali Lab Setup Notes

This file documents the configuration of the GNS3 lab used for simulating the ARP spoofing attack.

## 🔧 VM Settings
- Kali VM set up in VMware with 20 GB disk, XFCE desktop
- Network adapter: `Custom` → `VMnet1`
- Tool installed: `dsniff` (for `arpspoof`)
- IP address: `192.168.15.130`

## 🔧 GNS3 Configuration
- Created a new project: `ARP-Spoofing-Lab`
- Added:
  - Cloud node (mapped to VMnet1)
  - VPCS (victim)
- Linked Cloud ↔ VPCS with cable
- VPCS config:
  ```bash
  ip 192.168.15.100 255.255.255.0 192.168.15.1
  ```

## ✅ Connectivity Test
- Ping from PC1 to Kali: ✅ Successful
- Ping from Kali to PC1: ✅ Successful

## 🧠 Notes
- VPCS acts as a simple victim on the same subnet
- Cloud node bridges Kali’s VM network with GNS3 topology
- Wireshark or `arp -a` can verify spoof effectiveness