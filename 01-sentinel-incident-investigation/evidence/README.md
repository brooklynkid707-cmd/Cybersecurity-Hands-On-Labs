# Evidence

This directory contains evidence generated during the authorized CyberLab exercise.

## Current Artifacts

- `authentication-events.csv` — local Windows authentication evidence
- `file-access-events.csv` — local object-access evidence
- `powershell-events.csv` — local PowerShell logging evidence
- `screenshots/` — reserved for sanitized Azure, Sentinel, and KQL screenshots

## Current Evidence Gap
The screenshot directory is presently empty. This is a known portfolio-quality gap.

No replacement or synthetic screenshot should be created merely to make the repository appear complete. The next live execution of the lab should capture the evidence set below.

## Required Screenshot Set for Next Validation Run

1. Azure Arc endpoint showing connected state.
2. AMA / DCR assignment or successful collection configuration.
3. Microsoft Sentinel / Log Analytics query returning SecurityEvent data.
4. KQL output showing the controlled 4625 event.
5. KQL output showing the controlled 4624 event.
6. Correlation query showing the failed-to-successful sequence.
7. Optional incident/analytics-rule view if an analytic rule is created and triggered.

## Evidence Standards
Before publishing screenshots, remove unnecessary tenant/subscription identifiers; crop unrelated personal information; never expose passwords, API keys, access tokens, or temporary credentials; and preserve enough query/event context for technical review.

## Evidence Boundary
The CSV files represent local baseline evidence. They must not be described as proof that those historical events were retroactively ingested into Microsoft Sentinel.
