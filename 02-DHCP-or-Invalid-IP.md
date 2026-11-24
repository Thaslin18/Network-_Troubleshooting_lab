# Scenario: DHCP / Invalid IPv4 Configuration

## Problem
A client has no usable address or receives an APIPA address.

## Symptoms / clues
- IPv4 is `169.254.x.x`
- DHCP Enabled is Yes but address/gateway is missing
- No default gateway is shown

## Commands to collect evidence
```powershell
ipconfig /all
Get-NetIPConfiguration
```

## How to interpret
DHCP server, wireless association, VLAN, or relay may be unavailable. APIPA is a clue—not proof of a DHCP server fault.

## Safe troubleshooting steps
1. Check link/adapter state first.
2. Confirm the correct network/VLAN and whether other clients receive leases.
3. If authorized, request a lease using `ipconfig /renew`; document before/after values.
4. Escalate DHCP scope/server/relay checks to the network team if multiple clients are affected.

## Verification
A valid address, subnet, gateway, and DNS configuration is present; connectivity tests proceed.

```powershell
ipconfig /all
Get-NetIPConfiguration
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: Client shows an APIPA address and no gateway. Link is confirmed, other clients on the segment are checked, and the issue is escalated for DHCP service/segment validation.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
