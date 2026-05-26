# MITRE Caldera Installation

## Purpose

MITRE Caldera was deployed for:
- adversary emulation
- ATT&CK simulations
- detection engineering
- telemetry generation

---

## Host System
Kali Linux

---

## Installation Method

```bash
git clone --recursive https://github.com/mitre/caldera.git

```
---

## Environment Setup
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
---

## Startup Command
```bash
python3 server.py --build --insecure
```
---

## Plugins Used

| Plugin | Purpose |
|---|---|
| Sandcat | Agent framework |
| Stockpile | ATT&CK abilities |
| Debrief | Reporting |

---

## Agent Deployment

Sandcat agent deployed on:

- Windows 10 endpoint

## Telemetry Generated
- PowerShell activity
- Process creation
- Discovery commands
- Network activity

---
