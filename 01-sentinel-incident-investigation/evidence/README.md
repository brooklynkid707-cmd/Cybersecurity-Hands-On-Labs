# Evidence

This directory contains evidence generated during the authorized CyberLab exercise.

## Current Artifacts

- `authentication-events.csv` — local Windows authentication evidence
- `file-access-events.csv` — local object-access evidence
- `powershell-events.csv` — local PowerShell logging evidence
- `screenshots/` — location for sanitized Azure, Sentinel, and KQL screenshots

## Evidence Standards

Only genuine output from the lab should be stored here.

Do not fabricate screenshots or results.

Before publishing screenshots:

- remove unnecessary tenant/subscription identifiers;
- crop unrelated personal information;
- never expose passwords;
- never expose API keys or access tokens;
- never expose temporary credentials;
- retain enough technical context to show the query, event, timestamp, and result.

## Recommended Screenshot Set

1. Azure Arc endpoint showing Connected.
2. Successful AMA/DCR deployment.
3. Sentinel connector showing SecurityEvent ingestion.
4. KQL output showing 4625 and 4624.
5. Failed-to-successful authentication correlation result.

## Evidence Boundary

The CSV files represent local baseline evidence.

They must not be described as proof that those historical events were retroactively ingested into Microsoft Sentinel.
