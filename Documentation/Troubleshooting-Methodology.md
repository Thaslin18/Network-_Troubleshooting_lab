# Troubleshooting Methodology

## 1. Establish scope
Ask:
- What exact application or destination fails?
- Is it one user, one device, one network, or multiple users?
- When did it start? Any recent change?
- Is the issue intermittent or constant?

## 2. Gather baseline facts
Use `Get-NetAdapter` and `ipconfig /all`. Record adapter status, IPv4 address, subnet mask, DHCP status, gateway, and DNS servers. Do not publish private information without redaction.

## 3. Test progressively
- Loopback: `ping 127.0.0.1` (TCP/IP stack check; not a full NIC test)
- Local address: ping the host's own assigned address
- Gateway: ping the default gateway (may be blocked)
- Destination IP: test a known, approved destination
- DNS: resolve a hostname
- Service: test the expected TCP port

## 4. Interpret evidence
One test rarely proves the root cause. Correlate results. For example, an IP connection working while name resolution fails points toward DNS, but confirm the resolver and suffix behavior.

## 5. Apply the least disruptive correction
Prefer a reversible, approved change. On managed networks, follow IT change processes. Avoid resetting adapters, changing DNS, or restarting equipment without authorization.

## 6. Verify
Repeat the failed test, test the user's actual application, and check whether other users are affected.

## 7. Document
Record time, symptoms, scope, commands, observations, likely cause, action, verification, and follow-up.
