# SIEM-Detection-Lab

## Overview
Home SOC lab built from scratch with Wazuh SIEM, Suricata IDS on pfSense,
and custom detection rules mapped to MITRE ATT&CK.

## Architecture

## Components
- **SIEM:** Wazuh 4.14 (All-in-One on Ubuntu 24.04)
- **IDS:** Suricata on pfSense 2.8.1 (LAN + OPT1 interfaces)
- **Endpoints:** Windows 11 (Wazuh Agent + Sysmon), Kali Linux (attacker)
- **Log Transport:** SSH pull of eve.json from pfSense to Wazuh
- **Network:** 3 segments — WAN (NAT), LAN (192.168.10.0/24), OPT1 (192.168.20.0/24)

## Detection Rules
| Rule | MITRE ATT&CK | Description | File |
|------|-------------|-------------|------|
[Proof-of-work](https://github.com/C4LL1N/SIEM-Detection-Lab/tree/main/docs/Attack-Simmulation)
[example-of-rules](https://github.com/C4LL1N/SIEM-Detection-Lab/tree/main/wazuh-rules)

## Screenshots

<img width="1016" height="770" alt="2026-03-12_15-21" src="https://github.com/user-attachments/assets/5d633ccb-f9b3-4c67-9ee8-3211fd2277cd" />
<img width="2303" height="936" alt="2026-03-12_15-24" src="https://github.com/user-attachments/assets/35f94f0a-ad61-4d1c-a2a2-aac034ebf2b3" />
<img width="1016" height="770" alt="2026-03-12_15-21" src="https://github.com/user-attachments/assets/44f59b70-5c99-4e9e-8747-4bd00107159b" />
<img width="1022" height="726" alt="2026-03-12_15-30" src="https://github.com/user-attachments/assets/ae67c961-43ab-4e08-8199-5a11c861b319" />
<img width="1012" height="704" alt="2026-03-12_15-30_1" src="https://github.com/user-attachments/assets/031007a7-d6b2-4dec-9822-dd0ff748723b" />



## What I Learned
- Configured multi-segment network with pfSense firewall
- Deployed Suricata IDS on two interfaces (LAN + OPT1)
- Solved eve.json log forwarding via SSH pull (pfSense FreeBSD 15.0 
  incompatible with Wazuh agent), IT'S NOT PATTERN APROACH!, i will be creating own encrypted log collector with forwarder in the future
- Wrote custom Wazuh decoders for syslog-format Suricata alerts
- Built systemd service for persistent log collection
