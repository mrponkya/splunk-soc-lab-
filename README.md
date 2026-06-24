# splunk-soc-lab-
🖥️ Windows Security Monitoring & Threat Detection — Splunk SOC Lab
Module: Cybersecurity Analyst Student Project | Cybersecurity & Ethical Hacking  
Student: Rishi Ponkya  
Tools Used: Splunk Enterprise 10.4.0 · Sysmon · Windows Server 2022 · Oracle VirtualBox · PowerShell
> ⚠️ This project was completed in an isolated virtual lab environment. No real production systems were used.
---
📌 What This Project Covers
This project involved building a fully functional Security Operations Centre (SOC) monitoring environment from scratch using a Windows Server 2022 virtual machine running Splunk Enterprise. The goal was to simulate the real-world work of a SOC Analyst — ingesting logs, building alerts, triaging incidents, and writing investigation reports.
---
🛠 Tools & Environment
Tool	Purpose
Splunk Enterprise 10.4.0	SIEM platform for log collection, search, alerting and dashboards
Sysmon	Advanced Windows process and event monitoring
Windows Server 2022	Host OS for the entire lab environment
Oracle VirtualBox	Virtualisation platform
PowerShell	Scripting and event simulation
Atomic Red Team (optional)	Simulating real attack techniques
---
💻 Hardware Requirements Used
Component	Spec
RAM	8 GB minimum
CPU	Dual Core
Storage	100 GB Free
---
🧠 What I Did
Phase 1 — Windows Server Setup
Installed and configured Windows Server 2022 inside Oracle VirtualBox
Set administrator password and configured hostname
Assigned static IP address and verified internet connectivity
Created one administrator account and one standard user account
Phase 2 — Windows Logging Configuration
Enabled and configured Windows Event Logging and Auditing policies
Installed and configured Sysmon for deep process-level visibility
Configured Sysmon to capture process creation, network connections, file changes, and registry modifications
Phase 3 — Splunk Installation & Configuration
Installed Splunk Enterprise 10.4.0 on the Windows Server
Configured Splunk to ingest Windows Event Logs and Sysmon logs
Set up log forwarding and index configuration
Verified data was flowing correctly into Splunk
Phase 4 — Security Event Simulation
Generated real security events on the system including:
Failed login attempts
New user account creation
Privilege escalation attempts
Suspicious PowerShell execution
Used these events as the basis for alert creation and investigation
Phase 5 — SIEM Alerts & Searches
Built custom Splunk Search Processing Language (SPL) queries to detect:
Multiple failed logins (brute force indicators)
Suspicious process creation via Sysmon Event ID 1
New account creation (Event ID 4720)
PowerShell execution (Event ID 4104)
Created automated alerts to trigger on suspicious activity thresholds
Phase 6 — Dashboards & Incident Investigation
Built security monitoring dashboards in Splunk showing:
Login activity over time
Top event IDs
Process creation timeline
Alert history
Performed alert triage and investigated suspicious events as a SOC Analyst would
Wrote a formal incident report documenting findings, timeline, and recommendations
---
🔍 Key Windows Event IDs Monitored
Event ID	Description
4624	Successful logon
4625	Failed logon
4720	User account created
4732	User added to privileged group
4104	PowerShell script block logging
1 (Sysmon)	Process creation
3 (Sysmon)	Network connection
---
📚 What I Learned
How to build a SOC environment from scratch using free/open tools
How Windows Event Logging and Sysmon work together to provide full system visibility
How to write SPL queries in Splunk to hunt for suspicious activity
How to triage alerts and distinguish true positives from false positives
How to produce a professional incident report
The real day-to-day workflow of a SOC Analyst
---
⚠️ Disclaimer
All activities were performed on a personal isolated virtual machine running Windows Server 2022 inside Oracle VirtualBox. No real production systems or networks were involved. This project is purely educational.
