# Analyst Notes

## Investigation Context

A sequence of failed and successful Windows network authentication events was investigated for the local test account `CyberLabUser` on `CRYPTOGRAPHIC18`.

## Observations

- Authentication telemetry was present in Microsoft Sentinel's `SecurityEvent` table.
- Event ID 4625 represented failed authentication.
- Event ID 4624 represented successful authentication.
- Both event types were associated with `CyberLabUser`.
- Logon type was 3, indicating network authentication.
- The observed source address was loopback (`::1`).
- The failed-to-successful correlation query returned the expected sequence.

## Analyst Assessment

A failed authentication followed by a successful authentication can warrant investigation in a production environment.

In this lab, the surrounding evidence supports a benign disposition because the activity was intentionally generated, the source was localhost/loopback, the account was a dedicated lab identity, and the endpoint was owned and controlled for testing.

## Disposition

**Authorized security validation / benign simulation**

## Production Investigation Expansion

A production analyst should additionally review source IP reputation, authentication history, device history, identity privilege, MFA/conditional-access context, adjacent process activity, lateral movement, endpoint alerts, and related cloud and identity telemetry.

## Confidence

High confidence in the lab disposition because the activity was intentionally generated and independently observed through endpoint and Sentinel telemetry.
