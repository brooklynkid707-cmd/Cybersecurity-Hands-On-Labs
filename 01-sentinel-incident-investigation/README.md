# Lab 01 — Microsoft Sentinel Detection & Incident Investigation

## Executive Summary

This lab builds and validates an end-to-end Microsoft Sentinel telemetry and investigation workflow using a Windows 11 endpoint connected to Microsoft Azure through Azure Arc.

A dedicated local account, `CyberLabUser`, was used to generate controlled authentication activity.

Windows Security Events were collected through Azure Monitor Agent (AMA), governed by a Data Collection Rule (DCR), ingested into a Log Analytics workspace, and analyzed in Microsoft Sentinel using KQL.

Cloud-side validation confirmed both a failed authentication event (**4625**) and a subsequent successful authentication event (**4624**) for the same test identity and endpoint.

A correlation query successfully identified the failed-to-successful authentication sequence.

> **Scope:** This is an authorized synthetic cybersecurity lab. It does not represent a real compromise.

---

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

---

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

---

## Controlled Scenario

The lab generated a controlled authentication sequence against the local endpoint.

The workflow included:

1. Failed network authentication attempts against `CyberLabUser`.
2. A successful network authentication for the same account.
3. Windows Security Event validation.
4. AMA/DCR ingestion into Sentinel.
5. KQL investigation of Event IDs 4625 and 4624.
6. Correlation of failed authentication followed by successful authentication.
7. Analyst disposition based on surrounding evidence.

Earlier local testing produced six failed 4625 events and one successful 4624 event.

After Sentinel ingestion was enabled, a fresh cloud-validation sequence was generated.

Sentinel visibly returned a **4625** and **4624** for `CyberLabUser` on `CRYPTOGRAPHIC18`.

The local baseline and cloud validation are deliberately documented separately so local events are not misrepresented as having been retroactively ingested into Sentinel.

---

## Detection Engineering

Detection and hunting content in this project includes:

- Event ID 4625 — Failed authentication
- Event ID 4624 — Successful authentication
- Failed-to-successful authentication correlation
- Event ID 4663 — Sensitive file access investigation query
- Event ID 4104 — PowerShell Script Block investigation query

The authentication queries and correlation workflow were validated against Sentinel telemetry.

The 4663 and 4104 queries are retained as future telemetry-expansion content and are **not represented as completed Sentinel detections**.

---

## Investigation Findings

The validated authentication activity contained:

| Attribute | Observation |
|---|---|
| Account | CyberLabUser |
| Endpoint | CRYPTOGRAPHIC18 |
| Failed authentication | Event ID 4625 |
| Successful authentication | Event ID 4624 |
| Logon type | 3 — Network |
| Source | IPv6 loopback (`::1`) |
| Correlation | Failed authentication followed by successful authentication |

Because the source was localhost and the activity was deliberately generated, the correct disposition was:

**Authorized security validation / benign simulation**

rather than compromise.

---

## MITRE ATT&CK Context

The simulated behavior can be used to validate detection coverage for:

- **T1110 — Brute Force**
- **T1078 — Valid Accounts**

Additional planned telemetry maps to:

- **T1059.001 — PowerShell**
- **T1005 — Data from Local System**

These mappings describe simulated behavior for detection validation. They do not claim that an adversary executed these techniques.

See [investigation/mitre-mapping.md](./investigation/mitre-mapping.md).

---

## Evidence Integrity

Raw local evidence is retained under the `evidence` directory.

Screenshots added to this repository should contain only genuine Azure, Sentinel, Windows, or KQL output.

No passwords, access tokens, API keys, temporary credentials, or sensitive personal information should be committed.

---

## Skills Demonstrated

This lab demonstrates:

- Azure Arc endpoint onboarding
- Azure RBAC troubleshooting
- Azure Monitor Agent deployment
- Data Collection Rule engineering
- Log Analytics integration
- Microsoft Sentinel configuration
- Windows Security Event analysis
- KQL hunting
- Detection correlation
- SOC investigation methodology
- MITRE ATT&CK mapping
- False-positive/context analysis
- Technical documentation
- Evidence integrity

---

## Key Takeaway

This project demonstrates the complete security telemetry lifecycle rather than only a single query:

**endpoint activity → telemetry collection → cloud ingestion → SIEM analysis → detection correlation → analyst decision → remediation guidance**

That distinction is critical in production security operations.
