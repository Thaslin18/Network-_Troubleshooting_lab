# Scenario: Default Gateway Unreachable

## Problem
Local device has IP configuration but cannot reach its configured router.

## Symptoms / clues
- Gateway is listed but ping fails
- Other local devices may also fail
- Internet tests fail

## Commands to collect evidence
```powershell
ipconfig
ping <default-gateway>
arp -a
```

## How to interpret
Possible causes include local Wi-Fi/cabling, wrong subnet configuration, gateway outage, VLAN mismatch, or ICMP filtering.

## Safe troubleshooting steps
1. Confirm the gateway address belongs to the configured subnet.
2. Check adapter/link and compare with a known-good device on the same segment.
3. If authorized, inspect router/AP status or escalate.
4. Remember: ping failure alone does not prove the gateway is down.

## Verification
Re-test gateway and the user's actual service; verify scope.

```powershell
ping <default-gateway>
Test-NetConnection <gateway>
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: Several devices on the same segment cannot reach the gateway. Local link is checked; the issue is escalated for router/VLAN validation.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
