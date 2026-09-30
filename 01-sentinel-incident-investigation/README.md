# Lab 01 — Microsoft Sentinel Detection & Incident Investigation

## Recruiter Snapshot

**What this proves:** SIEM configuration, Windows telemetry, KQL, detection engineering, evidence handling, incident analysis, MITRE ATT&CK mapping, and security documentation.

**Validation status:** Completed in an authorized synthetic lab. The repository distinguishes cloud-validated Sentinel events from local-only baseline artifacts.

## Executive Summary

This lab builds and validates an end-to-end Microsoft Sentinel telemetry and investigation workflow using a Windows 11 endpoint connected to Microsoft Azure through Azure Arc.

A dedicated local account, `CyberLabUser`, was used to generate controlled authentication activity.

Windows Security Events were collected through Azure Monitor Agent (AMA), governed by a Data Collection Rule (DCR), ingested into a Log Analytics workspace, and analyzed in Microsoft Sentinel using KQL.

Cloud-side validation confirmed both a failed authentication event (**4625**) and a subsequent successful authentication event (**4624**) for the same test identity and endpoint.

A correlation query successfully identified the failed-to-successful authentication sequence.

> **Scope:** This is an authorized synthetic cybersecurity lab. It does not represent a real compromise.

## Environment

| Component | Implementation |
|---|---|
| Endpoint | Windows 11 Pro |
| Host | CRYPTOGRAPHIC18 |
| Cloud onboarding | Azure Arc |
| Collection agent | Azure Monitor Agent |
| Data Collection Rule | DCR-CyberLab-WindowsSecurity |
| Security Event filter | Minimal |
| Log Analytics Workspace | LAW-CyberLab-Sentinel |
| SIEM | Microsoft Sentinel |
| Primary table | SecurityEvent |
| Test identity | CyberLabUser |
| Query language | KQL |

## Architecture

```text
CRYPTOGRAPHIC18
 Windows Security Log
        |
        v
    Azure Arc
        |
        v
Azure Monitor Agent
        |
        v
DCR-CyberLab-WindowsSecurity
        |
        v
LAW-CyberLab-Sentinel
        |
        v
Microsoft Sentinel
        |
        v
KQL Hunting / Correlation
        |
        v
SOC Investigation
```

See [architecture/lab-architecture.md](./architecture/lab-architecture.md).

## Controlled Scenario

1. Failed network authentication attempts against `CyberLabUser`.
2. Successful network authentication for the same account.
3. Windows Security Event validation.
4. AMA/DCR ingestion into Sentinel.
5. KQL investigation of Event IDs 4625 and 4624.
6. Correlation of failed authentication followed by successful authentication.
7. Analyst disposition based on surrounding evidence.

Earlier local testing produced six failed 4625 events and one successful 4624 event. After Sentinel ingestion was enabled, a fresh cloud-validation sequence was generated.

Sentinel visibly returned a **4625** and **4624** for `CyberLabUser` on `CRYPTOGRAPHIC18`.

The local baseline and cloud validation are deliberately documented separately so local events are not misrepresented as having been retroactively ingested into Sentinel.

## Detection Content

- [Failed authentication](./detections/failed-authentication.kql)
- [Successful authentication](./detections/successful-authentication.kql)
- [Failed-to-successful correlation](./detections/brute-force-correlation.kql)
- [PowerShell investigation](./detections/powershell-investigation.kql)
- [Sensitive file access](./detections/sensitive-file-access.kql)

The authentication queries and correlation workflow were validated against Sentinel telemetry.

The 4663 and 4104 queries are retained as future telemetry-expansion content and are **not represented as completed Sentinel detections**.

## Investigation Findings

| Attribute | Observation |
|---|---|
| Account | CyberLabUser |
| Endpoint | CRYPTOGRAPHIC18 |
| Failed authentication | Event ID 4625 |
| Successful authentication | Event ID 4624 |
| Logon type | 3 — Network |
| Source | IPv6 loopback (`::1`) |
| Correlation | Failed authentication followed by successful authentication |

Because the source was localhost and the activity was deliberately generated, the correct disposition was **authorized security validation / benign simulation**, not compromise.

## MITRE ATT&CK Context

Validated simulated behavior supports detection coverage discussion for:

- **T1110 — Brute Force**
- **T1078 — Valid Accounts**

Additional planned telemetry maps to:

- **T1059.001 — PowerShell**
- **T1005 — Data from Local System**

See [investigation/mitre-mapping.md](./investigation/mitre-mapping.md).

## Evidence and Investigation Artifacts

- [Evidence index](./evidence/README.md)
- [Authentication evidence](./evidence/authentication-events.csv)
- [Analyst notes](./investigation/analyst-notes.md)
- [Incident timeline](./investigation/incident-timeline.md)
- [MITRE mapping](./investigation/mitre-mapping.md)
- [Remediation recommendations](./remediation/recommendations.md)

### Screenshot gap

The repository does **not yet contain the recommended Sentinel/Azure screenshots**. This is intentionally disclosed rather than filled with reconstructed or fabricated imagery. Future lab execution should capture screenshots at the time of validation.

## Skills Demonstrated

- Azure Arc endpoint onboarding
- Azure Monitor Agent deployment
- Data Collection Rule engineering
- Log Analytics integration
- Microsoft Sentinel
- Windows Security Event analysis
- KQL hunting
- detection correlation
- SOC investigation methodology
- MITRE ATT&CK mapping
- false-positive/context analysis
- technical documentation
- evidence integrity

## Key Takeaway

This project demonstrates the complete security telemetry lifecycle:

**endpoint activity → telemetry collection → cloud ingestion → SIEM analysis → detection correlation → analyst decision → remediation guidance**
