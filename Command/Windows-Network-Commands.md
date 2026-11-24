# Windows Network Command Reference

> Run commands on a device/network you own or are authorized to support. Some commands reveal identifying network information; redact before sharing.

| Command | Purpose | Notes |
|---|---|---|
| `ipconfig` | Basic IP configuration | Quick view |
| `ipconfig /all` | Full adapter configuration | Shows DHCP, DNS, MAC, lease |
| `ipconfig /release` | Releases DHCP lease | Changes connectivity; use only with approval |
| `ipconfig /renew` | Requests DHCP lease | Use only when appropriate |
| `ipconfig /flushdns` | Clears local DNS cache | May be useful after approved DNS troubleshooting |
| `ping 127.0.0.1` | Loopback test | Does not test physical network |
| `ping <gateway>` | Test gateway reachability | ICMP can be blocked |
| `ping <destination>` | Basic reachability | Not definitive if ICMP filtered |
| `tracert <destination>` | Shows path hops | Some hops may not reply |
| `nslookup <hostname>` | DNS lookup | Shows resolver and returned address |
| `Resolve-DnsName <hostname>` | PowerShell DNS lookup | Supports detailed record queries |
| `arp -a` | Displays ARP cache | Local IPv4 neighbor mappings |
| `route print` | Displays routing table | Look for default route |
| `netstat -ano` | Displays connections/listeners | PID can be mapped with Task Manager |
| `Get-NetAdapter` | Adapter status/details | PowerShell |
| `Get-NetIPConfiguration` | IP/gateway/DNS summary | PowerShell |
| `Test-NetConnection host -Port 443` | TCP connection test | `TcpTestSucceeded` is useful evidence |

## Typical diagnostic sequence
```powershell
Get-NetAdapter
Get-NetIPConfiguration
ipconfig /all
ping 127.0.0.1
ping <default-gateway>
nslookup example.com
tracert example.com
Test-NetConnection example.com -Port 443
route print
arp -a
```

## Interpreting common observations
- `Media disconnected`: adapter may be unplugged, disabled, or disconnected.
- `169.254.x.x`: Windows may have assigned APIPA after failing to obtain DHCP configuration.
- Missing default gateway: the device may not know where to send off-subnet traffic.
- DNS timeout: resolver may be unreachable or not responding; confirm with another approved resolver only if policy permits.
- `TcpTestSucceeded: False`: service/port/path/firewall may be blocking or unavailable; it does not alone identify the cause.
- `Request timed out`: ICMP response was not received; target may be offline or ICMP blocked.
