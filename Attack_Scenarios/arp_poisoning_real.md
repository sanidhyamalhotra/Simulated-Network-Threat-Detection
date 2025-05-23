# 🧨 ARP Spoofing Attack – Real Lab (GNS3 + Kali)

## 🛠️ Lab Overview
This simulation demonstrates a real ARP spoofing attack using Kali Linux and GNS3.

### Devices Used:
- **Attacker:** Kali Linux VM (`192.168.15.130`)
- **Victim:** VPCS node (`192.168.15.100`)
- **Gateway (simulated):** `192.168.15.1` (not a real router, just spoofed)

### GNS3 Topology:
- Kali is connected via `Cloud` node to VMnet1
- VPCS is connected to the same Cloud node
- Both devices are on the same subnet

## 🔧 Attack Execution

### Commands used on Kali:

```bash
sudo arpspoof -i eth0 -t 192.168.15.100 192.168.15.1
```

> This tells the victim (PC1) that Kali’s MAC belongs to the gateway IP.

## 📈 Verification
- PC1 was successfully pinging Kali (`ping 192.168.15.130`)
- ARP table entries in PC1 updated to show Kali’s MAC for `192.168.15.1`
- `arpspoof` sent repeated ARP replies showing the spoof in progress

## 🖼️ Screenshots
- `topology_screenshot.png` – GNS3 lab setup
- `arpspoof_output.png` – Kali terminal running attack
- `victim_ping_output.png` – PC1 pinging attacker (pre/post attack)

## 🧠 Detection Suggestions
- Monitor ARP table changes with `arp -a`
- Use Wireshark filters like `arp`
- Look for frequent unsolicited ARP replies

## 📄 Log File
- `arp_attack_real_log.log` – raw output from arpspoof (if saved separately)