# General Investigation Workflow

## Objective

This workflow is used to investigate adversary activity generated through:
- MITRE Caldera
- Atomic Red Team

---

## Investigation Steps

### 1. Identify Triggering Event
- ATT&CK technique
- suspicious process
- PowerShell activity

---

### 2. Review Parent/Child Process Relationships
Investigate:
- ParentImage
- Image
- CommandLine

---

### 3. Review PowerShell Telemetry
Analyze:
- Event ID 4104
- ScriptBlockText

---

### 4. Review Network Connections
Analyze:
- Sysmon Event ID 3
- outbound connections
- unusual ports

---

### 5. Correlate Activity
Correlate:
- process execution
- PowerShell activity
- network telemetry

---

### 6. ATT&CK Mapping
Map observed activity to:
- MITRE ATT&CK techniques

---

## Common SPL Queries

### Process Creation

```spl id="20ngrs"
index=sysmon EventCode=1

```
---

## PowerShell Logging
```spl id="20ngrs"
index=windows EventCode=4104
```
---

## Network Connections
```spl id="20ngrs"
index=sysmon EventCode=3
```

---
