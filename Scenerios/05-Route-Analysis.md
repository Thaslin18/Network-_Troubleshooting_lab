# Scenario: Route / Path Analysis

## Problem
Traffic to a destination may follow an unexpected route or fail beyond the local network.

## Symptoms / clues
- Local gateway test succeeds
- Destination is unreachable or path appears to stop
- Different destinations behave differently

## Commands to collect evidence
```powershell
route print
tracert example.com
ipconfig
```

## How to interpret
Possible causes include missing/incorrect routes, upstream routing, destination filtering, or non-responsive traceroute hops.

## Safe troubleshooting steps
1. Review the default route and interface metrics.
2. Run `tracert` to an approved destination and note where responses stop.
3. Do not treat a silent hop as proof of failure; routers may suppress TTL-expired replies.
4. Escalate with timestamps and destination details if upstream investigation is needed.

## Verification
Compare route/path and verify the original destination; document any unresolved upstream segment.

```powershell
route print
tracert example.com
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: Default route is present and local gateway responds; trace does not receive replies after an upstream hop. Evidence is recorded and escalated.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
