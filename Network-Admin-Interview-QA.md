# Network Administrator Interview Q&A

## 1. What is an IP address?
A logical address used to identify an interface and communicate over an IP network. IPv4 is 32 bits; IPv6 is 128 bits.

## 2. What does a subnet mask do?
It identifies the network and host portions of an IPv4 address. Devices use it to determine whether a destination is local or requires a router.

## 3. What is a default gateway?
The router a host uses to forward traffic to destinations outside its local subnet.

## 4. What is DHCP?
Dynamic Host Configuration Protocol automatically leases configuration such as IP address, subnet mask, gateway, and DNS server

## 5. What does 169.254.x.x indicate?
An APIPA address. Windows may assign it when it cannot obtain usable DHCP configuration. It is a clue, not a definitive diagnosis

## 6. What is DNS?
A distributed naming system that resolves hostnames to addresses and provides other records. DNS issues can make names fail while IP connectivity works

## 7. What does ping test?
ICMP echo reachability and round-trip time when replies are permitted. A failed ping does not prove a host is offline

## 8. What is tracert used for?
It discovers the path using TTL behavior and reports responding hops. Some routers do not reply, so timeouts are not conclusive

## 9. What is ARP?
IPv4 local-link address resolution that maps a local IP address to a MAC address

## 10. What does route print show?
The Windows routing table, including destination networks, next hops, interfaces, and metrics

## 11. How do you check TCP port connectivity?
Use `Test-NetConnection host -Port number`. Its result helps determine if a TCP handshake to that endpoint succeeds

## 12. Difference between TCP and UDP?
TCP is connection-oriented and provides ordered reliable delivery. UDP is connectionless and has lower overhead but no built-in delivery guarantee

## 13. What is a VLAN?
A logical Layer 2 segmentation of a switched network. VLANs separate broadcast domains and require routing for inter-VLAN communication

## 14. What is the OSI model?
Seven conceptual layers: Physical, Data Link, Network, Transport, Session, Presentation, Application

## 15. How would you troubleshoot 'internet not working'?
Define scope, inspect adapter and IP configuration, test gateway, test approved destination, test DNS, test route/service, document and verify

## 16. Why compare a working and failing device?
A controlled comparison can isolate differences in IP configuration, DNS, adapter, VLAN, or policy and helps determine the scope

## 17. What does a DNS timeout mean?
The query did not receive a response in time. The resolver may be unreachable, unavailable, filtered, or experiencing an issue; verify before concluding

## 18. What is packet loss?
Packets that fail to arrive or receive a response during a measurement. Investigate across multiple tests and paths

## 19. What should an incident report contain?
Time, symptom, scope, evidence, likely cause, approved action, verification, and follow-up

## 20. What is the safest troubleshooting approach?
Gather evidence first, make one approved reversible change at a time, retest, and record the result
