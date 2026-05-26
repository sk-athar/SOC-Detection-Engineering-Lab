# Sysmon Installation

## Purpose

Sysmon was deployed to provide:
- process creation telemetry
- network connection telemetry
- PowerShell visibility
- endpoint monitoring

---

## Sysmon Version
Sysmon64

---

## Installation Command

```powershell
Sysmon64.exe -accepteula -i sysmonconfig.xml

```
---

## Configuration

SwiftOnSecurity Sysmon configuration was used to improve:

- Detection visibility
- process telemetry
- PowerShell monitoring

---

## Key Telemetry
| Event ID | Description |
|---|---|
| 1 | Process Creation |
| 3 | Network Connections |
| 7 |Image Load |
| 11 | File Creation |
| 13 | Registry Modification |

---

## Integration

Sysmon logs were forwarded to Splunk using:

Splunk Universal Forwarder

---
