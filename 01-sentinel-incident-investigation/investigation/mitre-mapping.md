# MITRE ATT&CK Mapping

MITRE ATT&CK mappings in this project describe behaviors the lab is designed to emulate for detection engineering.

They do **not** indicate that a real adversary compromised the endpoint.

| Technique | ID | Lab behavior | Detection signal |
|---|---|---|---|
| Brute Force | T1110 | Controlled authentication failures | Event ID 4625 |
| Valid Accounts | T1078 | Controlled successful authentication following failure activity | Event ID 4624 |
| PowerShell | T1059.001 | Controlled PowerShell script execution | Event ID 4104; local validation completed, cloud collection pending |
| Data from Local System | T1005 | Controlled reads of synthetic local files | Event ID 4663 context; cloud validation pending |

## Interpretation

Windows Event IDs do not prove ATT&CK techniques by themselves.

For example, Event ID 4624 is generated during normal Windows activity.

It becomes relevant to T1078 only when surrounding evidence supports credential misuse or when the event is deliberately generated to validate that behavior in a controlled lab.

This distinction reduces false positives and produces more defensible detection engineering.
