# Scenario: Adapter Disconnected

## Problem
A Windows PC reports no network connection and the adapter may be disconnected or disabled.

## Symptoms / clues
- `Get-NetAdapter` shows `Disconnected` or `Disabled`
- `ipconfig /all` may show media disconnected

## Commands to collect evidence
```powershell
Get-NetAdapter
ipconfig /all
```

## How to interpret
The adapter is not connected to the expected network. Possible reasons include a loose cable, Wi-Fi being disconnected, adapter disabled, docking station issue, or access-point coverage.

## Safe troubleshooting steps
1. Confirm whether the connection is wired or Wi-Fi.
2. For wired, inspect cable and switch/dock connection. For Wi-Fi, confirm the correct SSID and airplane mode.
3. If the adapter is disabled, enable it only if permitted and after confirming the correct interface.

## Verification
Adapter shows connected and valid configuration; then test gateway reachability.

```powershell
Get-NetAdapter
ipconfig
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: User reports network unavailable. Adapter state is disconnected. Physical/Wi-Fi connection is checked and restored. Adapter state returns to Up; IP settings appear; gateway test is successful.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
