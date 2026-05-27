# T1082 - System Information Discovery Detection Queries

## ATT&CK Information

| Field | Value |
|---|---|
| Technique ID | T1082 |
| Technique Name | System Information Discovery |
| Related Technique | T1047 - Windows Management Instrumentation |
| ATT&CK Tactic | Discovery |

---

# Objective

These detection queries were developed to identify:
- WMIC-based reconnaissance
- operating system enumeration
- hardware discovery
- attacker system profiling activity

The detection logic focuses on:
- Sysmon process creation telemetry
- command-line auditing
- parent-child process relationships
- LOLBin abuse detection

---

# Threat Context

Adversaries commonly use WMIC to gather:
- operating system information
- hardware information
- CPU details
- disk information
- GPU information

This activity is frequently observed during:
- initial reconnaissance
- post-exploitation discovery
- malware staging
- adversary enumeration

---

# Telemetry Sources

| Source | Event ID | Purpose |
|---|---|
| Sysmon | 1 | Process Creation |
| Windows PowerShell | 4104 | Script Block Logging |
| Sysmon | 3 | Network Connections |

---

# Detection Query 1 - WMIC Process Creation

## SPL Query

```spl
index=sysmon EventCode=1
Image="*wmic.exe*"
(CommandLine="*os get*" OR CommandLine="*cpu get*" OR CommandLine="*diskdrive get*" OR CommandLine="*VideoController*")
| table _time Image CommandLine ParentImage User
```

---

## Detection Purpose

This query detects:
- WMIC execution
- hardware enumeration
- operating system discovery
- attacker reconnaissance activity

---

## Investigation Value

The query provides visibility into:
- executed discovery commands
- process lineage
- user execution context
- LOLBin abuse

---

# Detection Query 2 - Parent-Child Process Analysis

## SPL Query

```spl
index=sysmon EventCode=1
(Image="*wmic.exe*" OR ParentImage="*cmd.exe*")
| table _time ParentImage Image CommandLine User
```

---

## Detection Purpose

This query identifies:
- suspicious execution chains
- cmd.exe spawning wmic.exe
- attacker execution flow

---

## Investigation Value

The telemetry assists analysts with:
- process tree reconstruction
- adversary behavior analysis
- suspicious process lineage detection

---

# Detection Query 3 - Broad Discovery Hunting

## SPL Query

```spl
index=sysmon EventCode=1
(CommandLine="*wmic*" OR CommandLine="*systeminfo*" OR CommandLine="*hostname*")
| table _time Image CommandLine ParentImage User
```

---

## Detection Purpose

This query hunts for:
- general reconnaissance activity
- system discovery behavior
- attacker enumeration patterns

---

## Investigation Value

Useful for:
- enterprise hunting
- proactive investigations
- reconnaissance detection

---

# Detection Query 4 - Statistical WMIC Analysis

## SPL Query

```spl
index=sysmon EventCode=1
Image="*wmic.exe*"
| stats count by CommandLine User
```

---

## Detection Purpose

This query summarizes:
- WMIC usage frequency
- executed commands
- user execution patterns

---

## Investigation Value

Useful for:
- identifying abnormal WMIC usage
- establishing baselines
- anomaly detection

---

# Detection Logic Summary

The detection strategy focused on:
- WMIC execution monitoring
- command-line auditing
- process lineage analysis
- discovery activity hunting

The primary telemetry dependency was:
- Sysmon Event ID 1

---

# Potential False Positives

Legitimate administrative activity may generate similar telemetry.

Examples:
- IT asset inventory tools
- hardware diagnostics
- administrative troubleshooting
- system management scripts

Analysts should validate:
- execution context
- user activity
- parent process lineage
- execution frequency

---

# Detection Opportunities

## High-Risk Indicators

Suspicious indicators may include:
- WMIC launched by scripting engines
- repeated discovery commands
- Office applications spawning WMIC
- chained reconnaissance behavior

---

# ATT&CK Mapping

| ATT&CK ID | Technique |
|---|---|
| T1082 | System Information Discovery |
| T1047 | Windows Management Instrumentation |

---

# Detection Outcome

| Detection Area | Result |
|---|---|
| WMIC Execution Detection | Successful |
| Command-Line Visibility | Successful |
| Parent-Child Correlation | Successful |
| Splunk Telemetry Ingestion | Successful |
| ATT&CK Mapping | Successful |

---

# Conclusion

The developed detection queries successfully identified WMIC-based system information discovery activity.

The generated telemetry provided:
- strong process visibility
- command-line auditing
- process lineage reconstruction
- ATT&CK-aligned detection opportunities

Sysmon combined with Splunk provided highly effective visibility into reconnaissance behavior associated with system discovery activity.