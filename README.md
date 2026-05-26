# SOC Detection Engineering Lab

## Overview
This project is a hands-on SOC Detection Engineering and Threat Hunting lab built using:

- Splunk SIEM
- Sysmon
- MITRE Caldera
- Atomic Red Team
- Windows Event Logging
- PowerShell Logging

The lab focuses on:
- Adversary emulation
- ATT&CK technique simulation
- Detection engineering
- Threat hunting
- PowerShell analysis
- Process creation telemetry
- ATT&CK mapping

---

## Lab Architecture

### Machines
| System | Purpose |
|---|---|
| Kali Linux | Splunk + MITRE Caldera |
| Windows 10 | Victim / Telemetry Source |
| Windows 7 | Legacy Testing |
| Metasploitable2 | Linux Target |

---

## Tool Stack

| Tool | Purpose |
|---|---|
| Splunk | SIEM |
| Sysmon | Endpoint telemetry |
| MITRE Caldera | Adversary emulation |
| Atomic Red Team | ATT&CK simulations |
| Splunk UF | Log forwarding |

---

## Current Capabilities

- Sysmon telemetry ingestion
- PowerShell 4104 logging
- ATT&CK technique simulation
- Sandcat C2 agent deployment
- Threat hunting in Splunk
- SPL detection engineering
- Process tree analysis

---

## ATT&CK Techniques Simulated

| Technique | Description |
|---|---|
| T1082 | System Information Discovery |
| T1069.001 | Local Group Discovery |
| T1057 | Process Discovery |

---

## Detection Engineering

Detection queries and hunting logic are documented in:
- `/Detection-Queries`

---

## Investigation Playbooks

Investigation methodologies are documented in:
- `/Investigation-Playbooks`

---

## Future Improvements

- Additional ATT&CK techniques
- Detection tuning
- Dashboard development
- Sigma rule integration
- Zeek integration
- Alerting workflows
