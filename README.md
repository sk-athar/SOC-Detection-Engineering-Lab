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

![Architecture Diagram of the Operation](../Screenshots/Architecture/lab-architecture-diagram.png)

### Machines
| System | Purpose |
|---|---|
| Kali Linux | Splunk + MITRE Caldera |
| Windows 10 | Victim / Telemetry Source + Atomic Red Team |


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

<a href="https://github.com/sk-athar/SOC-Detection-Engineering-Lab/blob/main/Architecture/soc-lab-architecture.md">Detailed Lab Architecture

---

## ATT&CK Techniques Simulated

| Technique | Description |
|---|---|
| <a href="https://github.com/sk-athar/SOC-Detection-Engineering-Lab/blob/main/ATTACK-Mappings/T1082-System-Information-Discovery.md">T1082 | System Information Discovery |
| <a href="https://github.com/sk-athar/SOC-Detection-Engineering-Lab/blob/main/ATTACK-Mappings/T1069.001-Local-Group-Discovery.md">T1069.001 | Local Group Discovery |
| T1057 | Process Discovery |

---

## Detection Engineering

Detection queries and hunting logic are documented in:
- <a href="https://github.com/sk-athar/SOC-Detection-Engineering-Lab/blob/main/Detection-Queries"> `Detection-Queries`

---

## Investigation Playbooks

Investigation methodologies are documented in:
- <a href="https://github.com/sk-athar/SOC-Detection-Engineering-Lab/blob/main/Investigation-Playbooks/general-investigation-workflow.md">`General-investigation-workflow`

---

## Future Improvements

- Additional ATT&CK techniques
- Detection tuning
- Dashboard development
- Sigma rule integration
- Zeek integration
- Alerting workflows
