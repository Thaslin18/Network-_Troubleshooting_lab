# Scenario: Is It One Device or a Wider Outage?

## Problem
Determine whether a symptom is local to one endpoint, shared by a segment, or widespread.

## Symptoms / clues
- Reports from multiple users
- Some users succeed while others fail
- Same test gives different results across devices

## Commands to collect evidence
```powershell
Compare `Get-NetIPConfiguration` on a working and affected device
Test gateway and DNS on both
Record affected locations/users
```

## How to interpret
If only one endpoint is affected, local configuration or device-specific issues are more likely. If several devices on one segment fail, shared infrastructure or configuration becomes more likely.

## Safe troubleshooting steps
1. Use anonymized device aliases and compare the same tests.
2. Check whether affected users share a switch, VLAN, access point, or service.
3. Avoid changing multiple settings at once.
4. Escalate with a concise scope summary and evidence.

## Verification
Scope is understood, and the next owner has enough evidence to investigate.

```powershell
Get-NetIPConfiguration
ping <gateway>
nslookup <hostname>
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: One endpoint fails DNS while peers work. Comparison narrows the issue to endpoint configuration/resolver behavior; report is documented.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
