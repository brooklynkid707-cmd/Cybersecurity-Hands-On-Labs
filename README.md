# Cybersecurity Hands-On Labs

Hands-on security engineering and SOC portfolio focused on building, validating, and documenting defensive security workflows in realistic lab environments.

## Portfolio Focus

This repository demonstrates practical work with:

- Microsoft Sentinel and KQL
- Azure Arc
- Azure Monitor Agent (AMA)
- Data Collection Rules (DCR)
- Log Analytics
- Windows Security Event telemetry
- Detection engineering and event correlation
- Incident investigation
- MITRE ATT&CK-informed analysis
- PowerShell and Windows security logging

The objective is not to present canned exercises. Each project documents the environment, telemetry path, detection logic, validation evidence, investigation decisions, limitations, and remediation recommendations.

---

## Featured Project

### 01 — Microsoft Sentinel Detection & Incident Investigation

Built a Microsoft Sentinel lab around an Azure Arc-enabled Windows 11 endpoint and validated end-to-end Windows Security Event ingestion through AMA and a Data Collection Rule.

### Verified workflow

```text
Windows 11 Endpoint
CRYPTOGRAPHIC18
        |
        v
Azure Arc
        |
        v
Azure Monitor Agent
        |
        v
Data Collection Rule
DCR-CyberLab-WindowsSecurity
        |
        v
Log Analytics Workspace
LAW-CyberLab-Sentinel
        |
        v
Microsoft Sentinel
        |
        v
KQL Hunting & Correlation
        |
        v
SOC Investigation
```

A controlled authentication scenario generated failed and successful network authentication activity for a dedicated local lab account.

Microsoft Sentinel received the corresponding Windows Security Events and KQL was used to investigate and correlate Event IDs **4625** and **4624**.

[View the full Sentinel investigation](./01-sentinel-incident-investigation/README.md)

---

## Technical Skills Demonstrated

| Area | Technologies / Skills |
|---|---|
| SIEM | Microsoft Sentinel |
| Query Language | KQL |
| Cloud Security | Microsoft Azure |
| Endpoint Integration | Azure Arc |
| Telemetry | Azure Monitor Agent |
| Collection Engineering | Data Collection Rules |
| Logging | Windows Security Event Logs |
| Investigation | Authentication analysis and correlation |
| Detection Engineering | KQL hunting and behavioral correlation |
| Frameworks | MITRE ATT&CK |
| Scripting | PowerShell |
| Documentation | Incident timeline, analyst notes, remediation |

---

## Project Roadmap

| Lab | Focus | Status |
|---|---|---|
| 01 | Microsoft Sentinel Detection & Incident Investigation | Validated |
| 02 | Windows & Active Directory Attack / Detection | Planned |
| 03 | Vulnerability Assessment & Prioritization | Planned |
| 04 | Web Application Penetration Testing | Planned |
| 05 | Network Traffic Investigation | Planned |
| 06 | Compromised Endpoint Incident Response | Planned |
| 07 | Purple Team Detection Validation | Planned |
| 08 | Security Engineering Capstone | Planned |

---

## Security & Ethics

All attack-like activity documented in this repository is performed in personally owned or explicitly authorized lab environments.

Synthetic data and dedicated test identities are used where appropriate.

Results are documented according to what was actually observed. Simulated activity is never represented as a real-world compromise.

---

## About

Maintained by **JohnPaul Scirica**.

This portfolio is designed to demonstrate practical cybersecurity capability through reproducible technical work, defensible analysis, detection engineering, and clear security documentation.
