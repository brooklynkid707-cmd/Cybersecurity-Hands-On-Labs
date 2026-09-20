# Incident Timeline — Controlled Authentication Simulation

## Scope

This timeline documents authorized cybersecurity lab activity performed on September 19, 2026.

| Sequence | Activity | Evidence | Interpretation |
|---|---|---|---|
| 1 | Controlled failed authentication attempts generated | Windows Event ID 4625 | Synthetic authentication failure behavior |
| 2 | Local evidence confirmed repeated failures | Windows Security log export | Six failures observed in earlier local baseline |
| 3 | Azure Arc / AMA / DCR pipeline enabled | Azure configuration | Cloud telemetry path established |
| 4 | Fresh authentication validation generated | 4625 and 4624 | Failed then successful network authentication |
| 5 | Sentinel returned both event types | SecurityEvent KQL | End-to-end ingestion validated |
| 6 | KQL correlation returned same account/endpoint sequence | Correlation query | Detection logic validated |
| 7 | Activity dispositioned | Analyst assessment | Authorized lab activity / benign simulation |

## Evidence Boundary

The earlier local baseline and later cloud-validation sequence are separate evidence sets.

The six locally observed failed authentications are not claimed to have been retroactively ingested into Sentinel.

The cloud validation visibly confirmed at least one 4625 and one 4624 for the same test identity and endpoint.
