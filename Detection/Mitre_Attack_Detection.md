1. The Detection (Blue Team)
Telemetry Source: Sysmon (Event ID 1 & 10) -> Splunk

Splunk Query Used
To find this specific activity among the noise, I searched for the binary name:

Code snippet

index=* source="xmlwineventlog:microsoft-windows-sysmon/operational" "rdrleakdiag"
Evidence
(INSERT YOUR SPLUNK SCREENSHOT HERE - The one showing rdrleakdiag)

Analysis
The log captures critical indicators of compromise (IOCs):

Image: C:\Windows\System32\rdrleakdiag.exe (Legitimate file)

CommandLine: /p [PID] /o ... (Arguments proving it targeted a process)

Parent Image: powershell.exe (Suspicious parent process)

2. Mitigation & Response
In a production environment, I would recommend:

Attack Surface Reduction (ASR): Enable the ASR rule "Block credential stealing from the Windows local security authority subsystem."

Alerting: Create a high-severity alert for any process accessing lsass.exe with GrantedAccess permissions related to memory reading (e.g., 0x1F3FFF or specific subsets).
