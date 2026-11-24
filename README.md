# Network Troubleshooting & Monitoring Lab (Windows)

A beginner-friendly, portfolio-ready Windows networking lab that documents a structured approach to diagnosing common connectivity problems. It uses built-in Windows commands and PowerShell—no Linux installation or paid tools required.

> **Evidence note:** The images in `screenshots/sample-output/` are clearly labeled **ILLUSTRATIVE SAMPLE OUTPUT**. They are mock examples for learning the expected format, not screenshots captured from a real Windows device. Run the commands on your own PC and replace them with genuine screenshots before claiming hands-on execution.

## Project objective
Practice a repeatable troubleshooting workflow: identify symptoms, gather evidence, isolate the layer or component, apply a safe correction, and verify that connectivity is restored.

## Skills demonstrated
- Windows IP configuration and adapter inspection
- DHCP address, subnet mask, default gateway, and DNS interpretation
- Basic connectivity testing with `ping`
- Name resolution testing with `nslookup` and `Resolve-DnsName`
- Route inspection with `tracert` and `route print`
- TCP connection testing with `Test-NetConnection`
- ARP cache inspection
- Structured incident notes, root-cause analysis, and verification

## Lab scope
This is a local learning lab. All diagnostics are read-only except for optional, clearly documented Windows troubleshooting actions. Only troubleshoot devices and networks you own or are authorized to administer. Do not change network settings on a managed device without approval.

## Troubleshooting workflow
1. **Define the symptom** — what fails, when, and who is affected?
2. **Check the local interface** — adapter state and IP configuration.
3. **Check local TCP/IP** — loopback and local address.
4. **Check the gateway** — can the host reach its router?
5. **Check external connectivity** — use a known destination when permitted.
6. **Check DNS** — compare IP reachability with name resolution.
7. **Check the route / service** — trace path or test the expected TCP port.
8. **Document and verify** — record evidence, likely cause, fix, and retest.

## Quick start (Windows 10/11)
1. Download or clone this repository.
2. Open **Windows Terminal**, PowerShell, or Command Prompt.
3. Start with `scripts/Collect-NetworkDiagnostics.ps1`:
   - Right-click PowerShell → Run as administrator is **not normally required** for this read-only script.
   - If policy blocks script execution, do not weaken organization policy. Run the commands listed in `reference/Windows-Network-Commands.md` individually.
4. Run individual commands from the reference sheet and compare your observations with the scenario documents.
5. Capture your own screenshots and replace sample images in the evidence folder.

## Diagnostic collector
Run from PowerShell in the project directory:
```powershell
.\scripts\Collect-NetworkDiagnostics.ps1
```
If execution policy blocks the script, use the individual commands in the reference sheet instead. Avoid changing execution policy on a managed PC.

The script writes a timestamped text report under `output/`. Review the report before sharing; it may contain device names, adapter details, IP addresses, DNS servers, and other network information.

## Scenarios included
| ID | Scenario | Main checks |
|---|---|---|
| 01 | Adapter disconnected | `Get-NetAdapter`, `ipconfig /all` |
| 02 | DHCP / invalid IPv4 | `ipconfig`, lease details |
| 03 | Gateway unreachable | `ipconfig`, `ping` gateway |
| 04 | DNS failure | `nslookup`, `Resolve-DnsName` |
| 05 | Path / routing issue | `tracert`, `route print` |
| 06 | TCP service / port unavailable | `Test-NetConnection` |
| 07 | One endpoint vs wider outage | Compare tests and scope |

Each scenario includes symptoms, sample evidence, interpretation, safe actions, verification, and an incident-note example.

## Repository layout
```text
Network-Troubleshooting-Lab/
├── README.md
├── docs/
│   ├── Project-Overview.md
│   ├── Troubleshooting-Methodology.md
│   ├── Incident-Report-Template.md
│   └── scenarios/
├── scripts/
│   └── Collect-NetworkDiagnostics.ps1
├── reference/
│   ├── Windows-Network-Commands.md
│   └── Glossary.md
├── templates/
│   └── Incident-Log.csv
├── diagrams/
│   ├── Troubleshooting-Flow.png
│   └── Small-Office-Network.png
└── screenshots/
    └── sample-output/
```

## Sample evidence gallery
The gallery is useful as a reference for what evidence can look like. All sample visuals are labeled as illustrative. Capture genuine outputs on your own system for a final portfolio version.

## Results and limitations
This lab demonstrates a method and command knowledge through documented scenarios. Sample outputs are illustrative and cannot establish that the commands were executed on a physical device. Actual network results vary by adapter, router, ISP, firewall, DNS configuration, and Windows version. A failed ping alone does not prove a device is offline—ICMP may be blocked.

## Suggested GitHub description
**Windows-based networking troubleshooting lab covering IP configuration, gateway and DNS checks, route analysis, TCP connectivity testing, and structured incident documentation.**

## Next improvements
- Add real screenshots from a Windows PC
- Record an actual troubleshooting case with anonymized evidence
- Add a simple network-monitoring dashboard using safe, local test data
- Add a short screen-recording walkthrough
