# Scenario: TCP Service / Port Check

## Problem
A host may be reachable but a particular service is not accepting TCP connections.

## Symptoms / clues
- Host responds to ping, but app connection fails
- Port test reports `TcpTestSucceeded: False`

## Commands to collect evidence
```powershell
Test-NetConnection example.com -Port 443
netstat -ano
```

## How to interpret
Service may be stopped, listening on another port, filtered by firewall, or unreachable due to routing. A failed test does not isolate cause.

## Safe troubleshooting steps
1. Confirm the correct hostname and port from the service owner.
2. Test only the intended service endpoint.
3. Check service status/logs if authorized; ask service owner/network team to verify firewall policy.
4. Do not disable firewalls as a troubleshooting shortcut.

## Verification
TCP test succeeds and application test works; if not, collect result and escalate.

```powershell
Test-NetConnection <host> -Port <port>
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: TCP check to the expected port fails. Host/service owner confirms service and firewall policy; no firewall is disabled during the lab.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
