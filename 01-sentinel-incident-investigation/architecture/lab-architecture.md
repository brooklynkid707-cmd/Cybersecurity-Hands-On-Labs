# Lab Architecture

## Objective

Create and validate a reproducible telemetry path from a locally owned Windows endpoint into Microsoft Sentinel.

## Data Flow

```text
+------------------------------+
| CRYPTOGRAPHIC18              |
| Windows 11 Pro               |
| Windows Security Event Log   |
+--------------+---------------+
               |
               | Azure Arc
               v
+------------------------------+
| Azure Monitor Agent (AMA)    |
+--------------+---------------+
               |
               | DCR association
               v
+------------------------------+
| DCR-CyberLab-WindowsSecurity |
| Security Events: Minimal     |
+--------------+---------------+
               |
               v
+------------------------------+
| LAW-CyberLab-Sentinel        |
| Log Analytics Workspace      |
+--------------+---------------+
               |
               v
+------------------------------+
| Microsoft Sentinel           |
| SecurityEvent table          |
+--------------+---------------+
               |
               v
+------------------------------+
| KQL Hunting & Correlation    |
| SOC Investigation            |
+------------------------------+
```

## Validated Components

Azure Arc reported the endpoint as connected.
The Windows Security Events Data Collection Rule was created and associated with the Arc-enabled endpoint.
Azure Monitor Agent was deployed successfully.
Microsoft Sentinel subsequently received SecurityEvent telemetry from the endpoint.
KQL queries returned Windows authentication events from `CRYPTOGRAPHIC18`.

## Collection Boundaries

The current Security Events DCR uses the **Minimal** event set.

The lab therefore does not assume that every Windows Security Event is being collected.

Event ID 4663 requires appropriate object-access auditing and collection coverage.

PowerShell Script Block Event ID 4104 originates from `Microsoft-Windows-PowerShell/Operational` rather than the Windows Security log and therefore requires a separate Windows Event Log collection configuration.

This distinction is important because successful agent deployment does not automatically mean every desired telemetry source is being collected.
