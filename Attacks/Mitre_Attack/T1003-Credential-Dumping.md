```markdown
# 🕵️ Detection Report: LSASS Memory Dumping
**MITRE Technique:** [T1003.001 (OS Credential Dumping)](https://attack.mitre.org/techniques/T1003/001/)

## 1. Executive Summary
I emulated an advanced adversary attempting to steal credentials by dumping the memory of the Local Security Authority Subsystem Service (LSASS). The attack utilized `rdrleakdiag.exe`, a legitimate Microsoft-signed binary, to evade static antivirus signatures (a "Living off the Land" technique).

## 2. The Attack (Red Team)
**Tool:** Atomic Red Team (PowerShell)
**Technique:** T1003.001 - Test #13 (Dump LSASS using rdrleakdiag)

**Command Executed:**
```powershell
Invoke-AtomicTest T1003.001 
