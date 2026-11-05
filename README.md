# Splunk SOC Lab: Windows Security Monitoring & Threat Detection

Built a SOC monitoring environment from scratch on Windows Server 2022 and Splunk Enterprise. I simulated attacker activity, wrote detections and alerts, triaged the results, and documented the findings in an incident report.

**Stack:** Splunk Enterprise 10.4.0 · Sysmon · Windows Event Logging · PowerShell · Oracle VirtualBox · Windows Server 2022

> This project was completed in an isolated virtual lab. No production systems were used.

## Architecture

![Lab architecture](docs/architecture.png)
<!-- Add a simple diagram: Windows Server VM → Sysmon + Windows Event Logs → Splunk Enterprise -->

## Environment

| Component | Purpose |
|---|---|
| Splunk Enterprise 10.4.0 | SIEM: log collection, search, alerting, dashboards |
| Sysmon | Process, network, file, and registry telemetry |
| Windows Server 2022 | Monitored target VM (guest OS) |
| Oracle VirtualBox | Virtualization platform |
| PowerShell | Event simulation |
| Atomic Red Team (optional) | Simulated ATT&CK techniques |

**Hardware used:** 8 GB RAM minimum, dual-core CPU, 100 GB free storage

## Build Steps

1. **Windows Server setup:** Installed Windows Server 2022 in VirtualBox, set hostname and static IP, verified connectivity, and created an administrator and a standard user account.
2. **Logging configuration:** Enabled Windows Event Logging and auditing policies, then installed and configured Sysmon to capture process creation, network connections, file changes, and registry modifications. Config: [`configs/sysmonconfig.xml`](configs/sysmonconfig.xml)
3. **Splunk installation:** Installed Splunk Enterprise 10.4.0 on the server, configured it to ingest Windows Event Logs and Sysmon logs, and verified data was flowing. Config: [`configs/inputs.conf`](configs/inputs.conf)
4. **Security event simulation:** Generated failed logins, new account creation, privilege escalation attempts, and suspicious PowerShell execution.
5. **Detections and alerts:** Wrote SPL queries and scheduled alerts for brute-force indicators, suspicious process creation, account creation, and PowerShell execution. Searches: [`detections/`](detections/)
6. **Dashboards and triage:** Built dashboards for login activity, top Event IDs, process creation timelines, and alert history. Triaged alerts and separated true positives from false positives.
7. **Incident report:** Wrote a formal report covering findings, timeline, and recommendations. See [`docs/incident-report.md`](docs/incident-report.md)

## Detections

| Event ID / Source | What it shows | Detection use |
|---|---|---|
| 4625 | Failed logon | Brute-force indicator (T1110) |
| 4720 | User account created | Persistence via new accounts (T1136) |
| 4732 | User added to privileged group | Privilege escalation (T1098) |
| 4104 | PowerShell script block logging | Suspicious PowerShell execution (T1059.001) |
| Sysmon 1 | Process creation | Suspicious process execution |
| Sysmon 3 | Network connection | Unexpected outbound activity |

> Confirm the ATT&CK IDs match the detections you actually built.

## Dashboard

![Splunk dashboard](docs/dashboard.png)

## Key Findings

[Summarize the most important alert you triaged, the timeline, and the recommendation from your incident report.]

## What I Learned

- Building a SOC environment from scratch with free and open-source tools
- How Windows Event Logging and Sysmon together give full system visibility
- Writing SPL to hunt for suspicious activity
- Triaging alerts and separating true positives from false positives
- Producing a clear incident report
- The day-to-day workflow of a SOC analyst

## Disclaimer

All activity was performed on a personal, isolated virtual machine. No real systems or networks were involved. This project is for educational purposes.
