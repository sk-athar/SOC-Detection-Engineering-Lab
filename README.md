# SOC Detection Engineering Lab

## Overview

A hands-on Detection Engineering and Threat Hunting lab built to simulate real-world adversary behavior, generate endpoint telemetry, investigate activity in Splunk SIEM, and develop ATT&CK-aligned detections.

The project focuses on the complete detection engineering lifecycle:

```text
Attack Simulation
→ Telemetry Collection
→ Log Ingestion
→ Threat Hunting
→ Detection Engineering
→ ATT&CK Mapping
→ Investigation Reporting
```

Using MITRE Caldera and Atomic Red Team, adversary techniques are executed against a Windows endpoint while Sysmon and Windows Event Logs generate telemetry that is collected, analyzed, and investigated through Splunk.

---

## Project Highlights

* Built a Splunk-based Detection Engineering lab from the ground up
* Simulated adversary techniques using MITRE Caldera and Atomic Red Team
* Collected endpoint telemetry through Sysmon and Windows Event Logging
* Investigated attacks using Splunk SPL queries and threat hunting workflows
* Developed ATT&CK-aligned detection logic
* Performed process lineage and command-line analysis
* Created SOC-style investigation reports with supporting evidence
* Documented detections, attack simulations, and investigation methodologies

---

## Lab Architecture

![SOC Detection Engineering Lab Architecture](Screenshots/Architecture/lab-architecture-diagram.png)

### Detailed Architecture Documentation

[SOC Lab Architecture](Architecture/soc-lab-architecture.md)

---

## Environment

| System     | Purpose                                                         |
| ---------- | --------------------------------------------------------------- |
| Kali Linux | Splunk Enterprise, MITRE Caldera, Threat Hunting                |
| Windows 10 | Attack Target, Telemetry Source, Sandcat Agent, Atomic Red Team |

---

## Technology Stack

| Technology                 | Purpose                     |
| -------------------------- | --------------------------- |
| Splunk Enterprise          | SIEM Platform               |
| Sysmon                     | Endpoint Telemetry          |
| Splunk Universal Forwarder | Log Collection & Forwarding |
| MITRE Caldera              | Adversary Emulation         |
| Sandcat Agent              | Endpoint Agent              |
| Atomic Red Team            | ATT&CK Simulations          |
| PowerShell Logging         | Script Visibility           |
| MITRE ATT&CK               | Threat Mapping Framework    |

---

## Detection Engineering Workflow

Each ATT&CK technique follows a structured workflow:

### 1. Simulate Adversary Activity

Generate realistic attack telemetry using:

* MITRE Caldera
* Atomic Red Team

### 2. Collect Telemetry

Capture:

* Sysmon Events
* PowerShell Logs
* Windows Event Logs

### 3. Ingest Into Splunk

Forward telemetry using:

* Splunk Universal Forwarder

### 4. Investigate Activity

Analyze:

* Process Creation Events
* Parent-Child Process Relationships
* Command-Line Activity
* PowerShell Execution

### 5. Develop Detections

Create:

* SPL Detection Queries
* Threat Hunting Logic
* ATT&CK Mappings

### 6. Document Findings

Produce:

* Investigation Reports
* Detection Documentation
* ATT&CK Mapping Reports

---

## Current Capabilities

### Telemetry Collection

* Sysmon Event Collection
* Process Creation Monitoring (Event ID 1)
* Network Connection Monitoring (Event ID 3)
* PowerShell Script Block Logging (Event ID 4104)
* Windows Event Logging

### Adversary Emulation

* MITRE Caldera Operations
* Sandcat Agent Deployment
* ATT&CK Technique Simulation
* Atomic Red Team Testing

### Threat Hunting & Investigation

* Process Tree Analysis
* Command-Line Investigation
* ATT&CK-Based Hunting
* Telemetry Correlation
* Timeline Reconstruction

### Detection Engineering

* SPL Query Development
* Detection Validation
* ATT&CK Mapping
* Investigation Playbooks

---

## ATT&CK Techniques Simulated

| Technique | Description                  | Report                                                               |
| --------- | ---------------------------- | -------------------------------------------------------------------- |
| T1082     | System Information Discovery | [View Report](ATTACK-Mappings/T1082-System-Information-Discovery.md) |
| T1069.001 | Local Group Discovery        | [View Report](ATTACK-Mappings/T1069.001-Local-Group-Discovery.md)    |
| T1057     | Process Discovery            | In Progress                                                          |

---

## Detection Content

### Detection Queries

Detection logic and hunting queries:

[Detection-Queries](Detection-Queries)

### Investigation Playbooks

SOC investigation methodologies:

[General Investigation Workflow](Investigation-Playbooks/general-investigation-workflow.md)

---

## Repository Structure

```text
SOC-Detection-Engineering-Lab/
│
├── Architecture/
├── ATTACK-Mappings/
├── Detection-Queries/
├── Investigation-Playbooks/
├── MITRE-Caldera/
├── Atomic-Red-Team/
├── Splunk/
├── Sysmon/
├── Screenshots/
└── README.md
```

---

## Skills Demonstrated

### Security Operations (SOC)

* Security Monitoring
* Incident Investigation
* Event Correlation
* Threat Hunting
* Security Documentation

### Detection Engineering

* SPL Query Development
* Sysmon Telemetry Analysis
* Detection Validation
* ATT&CK Mapping

### Threat Hunting

* Process Analysis
* PowerShell Investigation
* Parent-Child Process Analysis
* Command-Line Auditing

### Adversary Emulation

* MITRE Caldera
* Sandcat Operations
* Atomic Red Team
* ATT&CK Technique Validation

---

## What Makes This Project Different?

Many cybersecurity home labs focus primarily on tool installation and configuration.

This project focuses on the complete blue-team workflow:

* Simulate realistic adversary behavior
* Generate telemetry
* Investigate activity
* Develop detections
* Map findings to ATT&CK
* Produce SOC-style investigation reports

The objective is to demonstrate practical Detection Engineering and SOC Analyst skills rather than simply deploying security tools.

---

## Future Improvements

* Additional ATT&CK Technique Coverage
* Detection Tuning & Validation
* Splunk Dashboard Development
* Sigma Rule Mapping
* Zeek Integration
* Detection Correlation Rules
* Alerting Workflows
* ATT&CK Coverage Dashboard
* Detection Metrics & Reporting

---
