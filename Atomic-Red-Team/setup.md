# Atomic Red Team Setup

## Purpose

Atomic Red Team was deployed to simulate:
- ATT&CK techniques
- adversary behavior
- telemetry generation
- detection engineering scenarios

The framework was used to generate realistic Windows telemetry for:
- Splunk
- Sysmon
- PowerShell logging

---

## Host System

Windows 10

---

## PowerShell Configuration

Execution policy bypass was enabled for the current PowerShell process:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force
```
---

## Installation Steps
- Install NuGet Provider
```powershell
Install-PackageProvider NuGet -Force
```
- Install PowerShellGet
```powershell
Install-Module PowerShellGet -Force
```
- Install Invoke-AtomicRedTeam
```powershell
IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing)

Install-AtomicRedTeam -Force
```
- Import Module
```powershell
Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1"
```
- Atomic Tests Path
```powershell
$PSDefaultParameterValues["Invoke-AtomicTest:PathToAtomicsFolder"]="C:\AtomicRedTeam\atomics\atomics"
```
## Example Test
```powershell
Invoke-AtomicTest T1082
```
## Telemetry Generated

- Sysmon Event ID 1
- PowerShell Event ID 4104
- Process creation telemetry
- Discovery command execution

## ATT&CK Techniques Simulated
| Technique | Description |
|---|---|
| T1082 | System Information Discovery |
| T1057 | Process Discovery |
| T1069.001 | Local Group Discovery |
