# General Investigation Workflow

## Objective

This workflow is used to investigate adversary activity generated through:
- MITRE Caldera
- Atomic Red Team
- Windows LOLBins
- ATT&CK-based simulations

The investigation methodology focuses on:
- process execution visibility
- command-line analysis
- PowerShell telemetry
- network activity
- ATT&CK mapping
- detection engineering

---

# Investigation Methodology

The investigation process follows a structured SOC analyst workflow designed to identify:
- adversary reconnaissance
- suspicious process execution
- PowerShell abuse
- discovery activity
- process lineage relationships

---

# Investigation Steps

## 1. Identify Triggering Event

Initial investigation begins with identifying:
- ATT&CK technique execution
- suspicious process creation
- PowerShell activity
- unusual discovery commands

Examples:
- wmic.exe
- powershell.exe
- cmd.exe
- systeminfo
- hostname

---

## 2. Review Process Creation Telemetry

Primary Telemetry Source:
- Sysmon Event ID 1

Investigate:
- Image
- CommandLine
- ParentImage
- User
- ProcessId

Purpose:
- identify executed binaries
- reconstruct execution chains
- identify suspicious command-line activity

---

## 3. Review Parent-Child Process Relationships

Investigate:
- ParentImage
- Child process execution
- execution lineage
- scripting engine activity

Examples:
- powershell.exe → cmd.exe
- cmd.exe → wmic.exe
- powershell.exe → wmic.exe

Purpose:
- identify attacker execution flow
- detect LOLBin abuse
- analyze process ancestry

---

## 4. Review PowerShell Telemetry

Primary Telemetry Source:
- Event ID 4104 (Script Block Logging)

Analyze:
- ScriptBlockText
- suspicious PowerShell commands
- encoded commands
- download cradles
- CIM/WMI usage

Examples:
- Get-CimInstance
- Invoke-Expression
- DownloadData
- WebClient

Purpose:
- identify PowerShell-based attacks
- recover executed scripts
- detect attacker reconnaissance

---

## 5. Review Network Connections

Primary Telemetry Source:
- Sysmon Event ID 3

Investigate:
- outbound connections
- unusual ports
- suspicious IP addresses
- beaconing activity

Purpose:
- identify C2 traffic
- detect outbound communication
- investigate lateral movement

---

## 6. Correlate Telemetry

Correlate:
- process execution
- command-line activity
- PowerShell logs
- network telemetry
- user context
- timestamps

Purpose:
- reconstruct attacker timeline
- validate suspicious activity
- improve investigation accuracy

---

## 7. ATT&CK Mapping

Map observed behavior to:
- MITRE ATT&CK techniques
- ATT&CK tactics
- adversary objectives

Examples:
- T1082 - System Information Discovery
- T1047 - Windows Management Instrumentation
- T1057 - Process Discovery
- T1069.001 - Local Group Discovery

Purpose:
- standardize investigations
- improve reporting
- align detections with ATT&CK

---

# Common SPL Investigation Queries

# Process Creation Investigation

## Sysmon Event ID 1

```spl
index=sysmon EventCode=1
| table _time Image CommandLine ParentImage User
```

Purpose:
- identify executed processes
- investigate command-line activity
- analyze process lineage

---

# WMIC Discovery Detection

```spl
index=sysmon EventCode=1
Image="*wmic.exe*"
(CommandLine="*os get*" OR CommandLine="*cpu get*" OR CommandLine="*diskdrive get*")
| table _time Image CommandLine ParentImage User
```

Purpose:
- detect system information discovery
- identify WMIC reconnaissance
- investigate LOLBin abuse

---

# Parent-Child Process Analysis

```spl
index=sysmon EventCode=1
(Image="*wmic.exe*" OR ParentImage="*cmd.exe*")
| table _time ParentImage Image CommandLine User
```

Purpose:
- reconstruct execution chains
- identify suspicious parent-child relationships

---

# PowerShell Logging Investigation

## Event ID 4104

```spl
index=windows EventCode=4104
| table _time ScriptBlockText
```

Purpose:
- review PowerShell execution
- identify malicious scripts
- analyze attacker commands

---

# Discovery Activity Hunting

```spl
index=sysmon EventCode=1
(CommandLine="*wmic*" OR CommandLine="*systeminfo*" OR CommandLine="*hostname*")
| table _time Image CommandLine ParentImage User
```

Purpose:
- identify reconnaissance activity
- hunt for discovery techniques
- detect attacker enumeration

---

# Network Connection Investigation

## Sysmon Event ID 3

```spl
index=sysmon EventCode=3
| table _time Image DestinationIp DestinationPort
```

Purpose:
- investigate outbound traffic
- identify suspicious communication
- detect beaconing behavior

---

# Investigation Best Practices

## Validate Execution Context

Always verify:
- user context
- expected administrative behavior
- scheduled task activity
- legitimate tooling

---

## Investigate Parent Processes

Suspicious parent processes may include:
- powershell.exe
- winword.exe
- excel.exe
- scripting engines

---

## Correlate Discovery Activity

Multiple discovery commands executed together may indicate:
- adversary reconnaissance
- malware staging
- post-exploitation activity

---

# Conclusion

This workflow provides a structured methodology for:
- ATT&CK investigations
- telemetry analysis
- threat hunting
- detection engineering
- SOC investigations

The process enables analysts to:
- identify suspicious activity
- reconstruct attacker behavior
- correlate telemetry
- improve detection coverage