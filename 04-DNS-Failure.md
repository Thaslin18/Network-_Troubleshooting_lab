# Scenario: DNS Resolution Failure

## Problem
A user can reach an IP destination but cannot resolve hostnames.

## Symptoms / clues
- Hostname lookup times out or returns an error
- IP-based test may work while hostname-based access fails

## Commands to collect evidence
```powershell
ipconfig /all
nslookup example.com
Resolve-DnsName example.com
```

## How to interpret
Potential causes include wrong DNS server settings, resolver outage, network path to DNS, or a domain-specific record issue.

## Safe troubleshooting steps
1. Record the DNS server configured on the client.
2. Test a known hostname and, if allowed, a second approved hostname.
3. Compare with a working device on the same network.
4. Only change DNS settings with authorization; use organization-approved DNS.

## Verification
Name resolution succeeds and the application can connect; record the resolver and evidence.

```powershell
nslookup example.com
Resolve-DnsName example.com
Test the actual application hostname
```
Repeat the original failing test and test the affected application. Compare before/after observations.

## Sample incident note (illustrative)
Example only: IP connectivity is available, but hostname lookup fails. Configured resolver is checked and compared with a known-good client; DNS issue is escalated or corrected through approved process.

## Important
This is a learning scenario, not a claim of an actual incident. Actual results vary. Follow your organization's change-control and security policies.
