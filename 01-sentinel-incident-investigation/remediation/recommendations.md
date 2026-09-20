# Remediation & Detection Recommendations

## Authentication Detection

Production detections should be tuned around baseline behavior rather than alerting on every Event ID 4625.

Useful dimensions include failure count, time window, source IP, target identity, endpoint, privilege level, successful authentication following failures, and historical user/device behavior.

## Preventive Controls

Potential controls include MFA, appropriate account lockout policies, privileged identity monitoring, conditional access where applicable, centralized authentication telemetry, endpoint monitoring, and alert enrichment with identity/device context.

## Telemetry Engineering

Before relying on a detection, validate that:

- the endpoint is connected;
- the collection agent is healthy;
- the DCR is associated with the correct endpoint;
- the selected event set includes required Event IDs;
- the expected destination table is receiving current records;
- timestamps, identities, and host fields are normalized correctly.

## Event ID 4663

Object-access auditing can generate significant telemetry.

Enable the required audit policy and SACL only for resources that matter, then confirm the DCR collects the necessary Security Event IDs.

## PowerShell Event ID 4104

PowerShell Script Block Logging requires a separate telemetry path because Event ID 4104 is generated in the PowerShell Operational channel rather than the Security log.

## SOC Investigation

A production investigation should preserve evidence, establish a timeline, correlate identity/endpoint/network context, assess potential blast radius, distinguish observed facts from analyst inference, document confidence and assumptions, and record remediation/follow-up actions.

The central lesson from this lab is that detection quality depends on both **query logic and telemetry quality**.
