# PowerShell Logging

## Purpose

PowerShell logging was enabled to improve:
- attack visibility
- script execution monitoring
- adversary detection
- threat hunting

---

## Logging Enabled

### Script Block Logging
Event ID:
4104

### Module Logging
PowerShell operational telemetry

---

## Detection Value

PowerShell logging allows visibility into:
- Invoke-Expression
- Download cradles
- Get-CimInstance
- Encoded commands
- Discovery techniques

---

## Example Detection Query

```spl id="gf4z0p"
index=windows EventCode=4104
| table _time ScriptBlockText
```
---

## ATT&CK Relevance
| Technique | Description |
|---|---|
| T1059.001 | PowerShell |
| T1082	| System Discovery |
| T1057 | Process Discovery |

---
