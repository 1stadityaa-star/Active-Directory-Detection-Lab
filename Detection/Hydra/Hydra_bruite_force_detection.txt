1. The Detection (Blue Team)
Telemetry Source: Windows Security Event Logs -> Splunk Event Code: 4625 (An account failed to log on)

Splunk Query Used
I created a query to detect high-frequency login failures targeting the specific user. Since the logs were indexed in a custom bucket, I targeted the endpoint index.

Code snippet

index=endpoint source="WinEventLog:Security" EventCode=4625 Target_User_Name="vishavs"
Detection Evidence
(Insert your screenshot here: The Splunk screen showing "68 events" and the list of failed logins)

Analysis
The logs revealed a clear pattern of a dictionary attack:

Event Code: 4625 (Failure Reason: "Unknown user name or bad password")

Account Targeted: vishavs

Volume: 68 failed attempts recorded in under 2 minutes.

Logon Type: 10 (Remote Interactive), confirming the attack vector was RDP.

2. Mitigation & Response
In a production environment, I would recommend:

Account Lockout Policy: Automatically lock the vishavs account after 5 failed attempts (via Group Policy).

MFA: Enforce Multi-Factor Authentication (MFA) for all RDP connections.

Network Level Authentication (NLA): Ensure NLA is required for RDP to prevent the session from starting without valid credentials.

Geo-Blocking: Block RDP connections from IP addresses outside of the organization's operating region.
