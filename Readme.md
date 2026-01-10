# 🛡️ Active Directory Adversary Emulation & Detection Lab

## 🚀 Project Overview
This project simulates a real-world cyber attack lifecycle to practice **Detection Engineering**. I deployed a vulnerable Active Directory environment, executed atomic attacks using **Atomic Red Team**, and built high-fidelity detections using **Sysmon** and **Splunk**.

## 🎯 Key Objectives
* **Infrastructure as Code:** Deployed Windows Server AD & Windows 10 Targets.
* **Telemetry Generation:** Configured **Sysmon (Olaf Hartong Config)** to generate MITRE ATT&CK tagged logs.
* **Log Aggregation:** Forwarded logs to **Splunk** using the Universal Forwarder.
* **Threat Hunting:** Detected "Living off the Land" binaries (LOLBins) used for credential dumping.

## 🛠️ Tech Stack
* **Attack:** Atomic Red Team, Hydra
* **Defense:** Splunk Enterprise, Sysmon
* **Tools:** PowerShell, VirtualBox, Kali Linux

---

## ⚔️ Featured Scenarios

### Scenario 1: Credential Dumping (MITRE T1003.001)
**The Attack:** Used `rdrleakdiag.exe`, a Microsoft-signed debugger, to dump LSASS memory. This is a "Living off the Land" technique often missed by traditional antivirus.
**The Detection:** Identified the specific command line arguments and process target in Splunk.
* [View Full Report](1-Attacks/T1003-Credential-Dumping.md)

### Scenario 2: RDP Brute Force (MITRE T1110)
**The Attack:** Performed a dictionary attack against the Domain Controller using Hydra.
**The Detection:** Created a Splunk alert for `Event Code 4625` (Failed Login) triggering >5 times in 1 minute.
