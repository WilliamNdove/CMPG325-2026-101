# CMPG325-2026-101
CPMG325-2026-101

# CMPG 325 – Computer Networks: Individual Semester Project

**Student:** Ndove, W  
**Student Number:** 45157995  
**Project ID:** CMPG325-2026-101  
**Client ID:** CLI-101  
**Assigned Organisation:** Ditsobotla Local Municipality Offices (Lichtenburg)  
**Industry:** Municipal Services  

---

## Milestone 2 - Client Implementation Review (Completed)

### What Was Implemented
- **Inter-VLAN Routing (Assigned Challenge):** Configured Switch Virtual Interfaces (SVIs) on the L3 Core Switch with `ip routing` enabled.
- **Secure Remote Management (CR9):** Configured SSHv2 on the Core-L3-Switch, disabled Telnet, and applied a Management ACL (`MGMT-ACCESS`) restricting access to the management subnet (`192.168.45.112/28`).
- **Off-site Administrator Path:** Configured a WRT300N wireless router with a static WAN IP (`192.168.45.114`) and WPA2 security, allowing the off-site PC (`PC0`) to securely SSH into the core switch.
- **Routing:** Added a static route on the Core switch (`ip route 192.168.0.0 255.255.255.0 192.168.45.114`) to allow return traffic to the off-site PC.
- **Topology:** 1x Core-L3-Switch (3560), 3x Access Switches (2960), 1x WRT300N Wireless Router, and end devices (Admin PCs, Finance PCs, Public/Records PCs, Off-site Admin PC).

### VLAN & IP Addressing Plan
| VLAN | Name | Subnet | Gateway |
|------|------|--------|---------|
| 10 | ADMIN | 192.168.45.0/27 | 192.168.45.1 |
| 20 | FINANCE | 192.168.45.32/27 | 192.168.45.33 |
| 30 | PUBLIC SERVICES | 192.168.45.64/27 | 192.168.45.65 |
| 40 | IT/SERVERS | 192.168.45.96/28 | 192.168.45.97 |
| 99 | MANAGEMENT | 192.168.45.112/28 | 192.168.45.113 |

### Files Added in Milestone 2
- `05-testing-evidence/` — Screenshots of Inter-VLAN ping tests, CR9 SSH success, SSH denial (negative test), Telnet refusal, and verification commands.
- `04-packet-tracer/` — Working Packet Tracer file (`.pkt`) and text copies of `show running-config` for all three switches.
- `06-troubleshooting/` — Documentation of faults encountered and resolved (e.g., trunk encapsulation, `ip routing` enabled, CLI freeze workaround).

### Testing Results
| Test | Result |
|------|--------|
| Same-VLAN connectivity | Pass |
| Inter-VLAN Routing (e.g., Admin to Finance) | Pass |
| CR9: SSH Remote Management from Off-site PC | Pass |
| CR9: SSH Denial from normal User PC | Pass (ACL blocks it) |
| CR9: Telnet Refusal | Pass (Connection refused) |
| `show ip route` (5 connected routes + 1 static) | Pass |

---
Ditsobotla Local Municipality Offices is a municipal services client based in Lichtenburg. The network design must support four functional areas (Administration, Finance, Public Services/Records, and IT/Servers) plus secure access for one off-site administrator, all within the assigned addressing block **192.168.45.0/24**.

## Assigned Networking Challenge
**Inter-VLAN Routing (L3 switch / SVI)** — Difficulty: Foundational

## Design Constraint
Load-shedding resilience: core devices on UPS, minimal device count preferred.

## Change Request
**CR9:** One off-site administrator requires secure remote management access to network devices.

## Repository Structure

```
Testing-Evidence-Configuration/    Configuration evidence (VLANs, routes, IPs, trunks)
Testing-Evidence-Ping-Tests/       Ping test evidence (same-VLAN + Inter-VLAN)
CMPG-325-101_Milestone2_Ndove.pkt  Working Packet Tracer implementation
README.md                          Project documentation
```

## Project Milestones

- Project commencement: 14 August 2026
- Milestone 1 (Client Design Review): 28 August 2026
- Milestone 2: 2 October 2026
- Final submission: 16 October 2026

## Academic Integrity

This repository contains my own analysis and implementation for the client scenario assigned to
me (Client CLI-101 / Project CMPG325-2026-101). It has not been substituted with another
student's project or client allocation, in line with the NWU AI Policy and the CMPG 325 project
brief.
