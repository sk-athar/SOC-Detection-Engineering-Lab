# SOC Lab Architecture

## Overview

This lab was designed to simulate a real-world SOC environment focused on:
- adversary emulation
- endpoint telemetry
- threat hunting
- detection engineering
- ATT&CK mapping

---

## Lab Components

### Kali Linux
Purpose:
- Splunk SIEM
- MITRE Caldera
- Threat hunting
- Detection engineering

IP Address:
192.168.1.10

---

### Windows 10
Purpose:
- Victim workstation
- Telemetry generation
- Sandcat agent execution
- Atomic Red Team execution

Telemetry:
- Sysmon
- PowerShell logging
- Windows Event Logs

---

### Windows 7 SP1
Purpose:
- Legacy testing
- Additional telemetry source

---

### Metasploitable2
Purpose:
- Linux attack target
- Network attack simulation

---

## Data Flow

Windows Telemetry
→ Splunk Universal Forwarder
→ Splunk SIEM

Caldera Operations
→ Sandcat Agent
→ Windows Endpoint
→ Sysmon Logs
→ Splunk

Atomic Red Team
→ Windows Endpoint
→ Sysmon + PowerShell Logs
→ Splunk

---

## Security Telemetry Sources

| Source | Description |
|---|---|
| Sysmon | Endpoint telemetry |
| Event ID 4104 | PowerShell Script Block Logging |
| Windows Event Logs | Native Windows telemetry |
| Sysmon Event ID 1 | Process Creation |
| Sysmon Event ID 3 | Network Connections |

---

## ATT&CK Simulation Tools

| Tool | Purpose |
|---|---|
| MITRE Caldera | Adversary emulation |
| Atomic Red Team | ATT&CK simulations |
