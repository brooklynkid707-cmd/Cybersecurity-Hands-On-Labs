# Lab 02 — Windows & Active Directory Attack / Detection

**Status: Execution-ready. Not yet represented as a completed lab.**

## Objective
Build a small authorized Windows domain environment and validate identity-focused attack and detection scenarios using Windows telemetry and SIEM analysis.

## Target Architecture

```text
Kali / Test Host
      |
Windows 11 Client
      |
Windows Server / Active Directory
      |
Windows Event Logs
      |
Microsoft Sentinel / Log Analytics
```

## Detection Targets

| Event | Security Relevance |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4648 | Logon using explicit credentials |
| 4672 | Special privileges assigned |
| 4688 | Process creation |
| 4720 | User account created |
| 4728 / 4732 | User added to privileged/local group |
| 4768 | Kerberos TGT request |
| 4769 | Kerberos service ticket request |
| 4776 | Credential validation |

## Controlled Scenarios

- repeated failed authentication;
- password-spray simulation against dedicated test identities;
- successful logon following failures;
- new-user creation;
- privileged-group membership change;
- administrative PowerShell;
- RDP or remote-logon validation;
- Kerberos authentication analysis.

## Deliverables

- architecture diagram;
- attack/validation procedure;
- KQL detection queries;
- event evidence;
- investigation timeline;
- ATT&CK mapping;
- analyst disposition;
- remediation guidance;
- screenshots from the actual lab.

## Evidence Gate
This lab becomes **Validated** only after the controlled scenarios are executed and evidence is committed.
