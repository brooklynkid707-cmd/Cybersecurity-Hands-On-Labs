# Lab 07 — Purple Team Detection Validation

**Status: Execution-ready.**

## Objective
Validate whether defined defensive controls can detect controlled ATT&CK-aligned behaviors, then document gaps and tune detections.

## Validation Loop

```text
Technique -> Expected Telemetry -> Controlled Execution -> Observed Telemetry
          -> Detection Result -> Gap Analysis -> Tuning -> Retest
```

## Example ATT&CK Coverage

- T1110 Brute Force
- T1078 Valid Accounts
- T1059.001 PowerShell
- account / privilege manipulation techniques appropriate to the lab

## Deliverables
Technique test plan, expected event sources, actual telemetry, detection logic, pass/fail criteria, false-positive analysis, tuning changes, and retest results.
