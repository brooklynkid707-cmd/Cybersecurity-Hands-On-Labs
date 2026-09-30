# Cybersecurity Engineering Portfolio

Hands-on cybersecurity portfolio maintained by **JohnPaul Scirica** and organized around security operations, detection engineering, vulnerability management, offensive-security methodology, incident response, network analysis, automation, and enterprise security architecture.

This repository is designed for technical reviewers and hiring managers who want to see **how I investigate, validate, document, and communicate security work**, not just a list of tools.

## Current Portfolio Status

| Lab | Domain | Status | Evidence Level |
|---|---|---|---|
| 01 | Microsoft Sentinel Detection & Incident Investigation | **Validated** | Queries, CSV evidence, analyst notes, timeline, MITRE mapping |
| 02 | Windows & Active Directory Attack / Detection | **Execution-ready** | Lab plan + detection targets |
| 03 | Vulnerability Assessment & Prioritization | **Execution-ready** | Methodology + reporting structure |
| 04 | Web Application Penetration Testing | **Execution-ready** | OWASP-aligned methodology |
| 05 | Network Traffic Investigation | **Execution-ready** | PCAP investigation methodology |
| 06 | Compromised Endpoint Incident Response | **Execution-ready** | DFIR workflow |
| 07 | Purple Team Detection Validation | **Execution-ready** | ATT&CK validation workflow |
| 08 | Security Automation & Engineering Capstone | **Execution-ready** | Automation design + integration plan |

> **Evidence rule:** A project is only marked **Validated** when the repository contains evidence from an actually executed lab. Planned or scaffolded work is never represented as completed work.

## Featured Validated Project

### 01 — Microsoft Sentinel Detection & Incident Investigation

Built and validated an end-to-end telemetry path from a Windows 11 endpoint to Microsoft Sentinel using Azure Arc, Azure Monitor Agent, a Data Collection Rule, Log Analytics, Windows Security Events, and KQL.

Validated work includes:

- Windows Security Event ingestion
- Event ID 4625 failed authentication analysis
- Event ID 4624 successful authentication analysis
- Failed-to-successful authentication correlation
- KQL hunting queries
- Analyst notes and incident timeline
- MITRE ATT&CK mapping
- Remediation recommendations
- Evidence-integrity boundaries separating local baseline data from cloud-validated telemetry

[Open the validated Sentinel investigation](./01-sentinel-incident-investigation/README.md)

## Portfolio Domains

### Security Operations & Detection Engineering
Microsoft Sentinel, KQL, Windows Security Events, alert investigation, telemetry validation, MITRE ATT&CK mapping, false-positive/context analysis.

### Identity & Active Directory Security
Windows authentication, domain activity, privilege changes, Kerberos telemetry, account lifecycle events, password-spray detection, lateral-movement indicators.

### Vulnerability Management
Asset discovery, service enumeration, vulnerability scanning, CVE/CWE research, CVSS interpretation, CISA KEV context, manual validation, remediation prioritization.

### Offensive Security
Authorized reconnaissance, application mapping, web testing, Burp Suite workflow, OWASP Top 10, validation of findings, technical reporting, retesting.

### Network Security & Forensics
Wireshark, PCAP analysis, DNS/HTTP/TLS inspection, suspicious flow reconstruction, host communication analysis, timeline development.

### Incident Response & DFIR
Windows Event Logs, PowerShell telemetry, endpoint triage, process and persistence analysis, evidence handling, containment and remediation planning.

### Security Automation
Python, PowerShell, structured log parsing, enrichment workflows, API-driven automation concepts, repeatable evidence collection and reporting.

### Security Architecture, Risk & Governance
See the companion repositories **Project Iron Curtain** and **Project Guardian Angel** for risk assessment, security architecture, AI security governance, control mapping, incident response strategy, and executive communication.

## Recruiter / Hiring Manager Navigation

Start here:

1. **Validated technical investigation:** [Lab 01](./01-sentinel-incident-investigation/README.md)
2. **Skills-to-evidence map:** [SKILLS-EVIDENCE-MATRIX.md](./SKILLS-EVIDENCE-MATRIX.md)
3. **Portfolio review guide:** [HIRING-MANAGER-GUIDE.md](./HIRING-MANAGER-GUIDE.md)
4. **Upcoming technical labs:** Labs 02–08 below

## Lab Roadmap

- [02 — Windows & Active Directory Attack / Detection](./02-active-directory-attack-detection/README.md)
- [03 — Vulnerability Assessment & Prioritization](./03-vulnerability-assessment/README.md)
- [04 — Web Application Penetration Testing](./04-web-application-pentest/README.md)
- [05 — Network Traffic Investigation](./05-network-traffic-investigation/README.md)
- [06 — Compromised Endpoint Incident Response](./06-endpoint-incident-response/README.md)
- [07 — Purple Team Detection Validation](./07-purple-team-detection-validation/README.md)
- [08 — Security Automation & Engineering Capstone](./08-security-automation-capstone/README.md)

## Technical Stack

| Category | Technologies / Concepts |
|---|---|
| SIEM | Microsoft Sentinel, Log Analytics |
| Query | KQL |
| Microsoft Security | Azure Arc, AMA, DCR, Windows Security Events |
| Endpoint / OS | Windows 11, Windows Server, PowerShell, Linux/Kali |
| Network | Nmap, Wireshark, TCP/IP, service enumeration |
| Web Security | Burp Suite, OWASP testing methodology |
| Offensive Tooling | Nmap, Gobuster, Hydra, John, Metasploit in authorized labs |
| Scripting | Python, PowerShell, SQL |
| Frameworks | MITRE ATT&CK, NIST concepts, OWASP, CVSS/CWE/CVE |
| Documentation | Incident timelines, analyst notes, remediation, executive and technical reporting |

## Security & Ethics

All attack-like activity documented here is performed in personally owned, intentionally vulnerable, CTF, or explicitly authorized lab environments.

No repository should contain real customer data, credentials, secrets, access tokens, or fabricated evidence.

## About

**JohnPaul Scirica**  
Cybersecurity | Security Operations | Detection Engineering | Security Architecture  
CompTIA Security+ | Certified Ethical Hacker (CEH)  
Post Graduate Program in Cybersecurity — The University of Texas at Austin  
MBA — Data Analytics
