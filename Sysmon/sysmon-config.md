# Sysmon Configuration

## Objective

Sysmon was configured to provide enhanced Windows telemetry for:
- process creation
- network connections
- PowerShell activity
- registry modifications
- file creation events

This telemetry was forwarded into Splunk SIEM for:
- detection engineering
- threat hunting
- ATT&CK mapping
- adversary emulation analysis

---

## Configuration Source

SwiftOnSecurity Sysmon configuration was used as the primary baseline configuration.

Purpose:
- reduce telemetry noise
- improve detection visibility
- enable useful event filtering

---

## Installation Command

```powershell
Sysmon64.exe -accepteula -i sysmonconfig.xml
```
---

## Key Event IDs
| Event ID | Description |
|----|---|
| 1 | Process Creation |
| 3 | Network Connections |
| 7 | Image Load |
| 11 | File Creation |
| 13 | Registry Modification |

---
## Splunk Integration

Sysmon logs were forwarded using:

- Splunk Universal Forwarder

Primary index: sysmon

Primary sourcetype: XmlWinEventLog:Microsoft-Windows-Sysmon/Operational

## Example SPL Queries

Process Creation
```spl id="gf4z0p"
index=sysmon EventCode=1
| table _time Image CommandLine ParentImage User
```

Network Connections
```spl id="gf4z0p"
index=sysmon EventCode=3
| table _time Image DestinationIp DestinationPort
```
---

## Telemetry Benefits

Sysmon enabled visibility into:

- process execution
- PowerShell abuse
- adversary discovery techniques
- C2 activity
- LOLBins
- suspicious parent-child relationships
