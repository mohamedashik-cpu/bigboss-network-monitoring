# Cisco Commands for NOC Operations

This section is a practical reference for using Cisco IOS show commands to verify device health, inspect interfaces and ports, and review configuration or operational state during authorized NOC troubleshooting.

> **Safety and confidentiality:** Use commands only on devices you are authorized to access. Do not publish real production command output, customer details, internal IP addresses, credentials, circuit IDs, or proprietary configurations in this repository. Prefer sanitized examples.

## Guides in This Section

1. [Device Health Check](01-Device-Health-Check.md) — basic device information, CPU/memory, logs, environment, and neighbor discovery checks.
2. [Interface and Port Troubleshooting](02-Interface-and-Port-Troubleshooting.md) — interface status, errors, counters, speed/duplex, switch ports, MAC tables, and link symptoms.
3. [Configuration and Operational Verification](03-Configuration-and-Operational-Verification.md) — read-only verification of running/startup configuration, VLANs, trunks, ARP, routing, and ACLs.

## Command Categories

| Purpose | Example commands |
|---|---|
| Device and software information | `show version` |
| CPU and memory health | `show processes cpu`, `show processes memory` |
| Interface summary | `show ip interface brief` |
| Interface details | `show interfaces <interface>` |
| Interface descriptions | `show interfaces description` |
| Interface errors | `show interfaces counters errors` |
| Logs | `show logging` |
| VLAN and trunk verification | `show vlan brief`, `show interfaces trunk` |
| MAC address table | `show mac address-table` |
| ARP and routing tables | `show ip arp`, `show ip route` |
| Neighbor discovery | `show cdp neighbors`, `show lldp neighbors` |

Command availability and syntax vary by platform, software version, privilege level, and device role. Check the device's supported syntax and internal SOP.

## Recommended Verification Workflow

**Confirm Device → Check Summary Status → Inspect Relevant Interface → Review Counters and Logs → Validate Related VLAN/Routing/Neighbor State → Record Findings → Escalate or Continue Approved Troubleshooting**

Use the smallest relevant set of commands needed to investigate the symptom. A command output is evidence, not automatically a root-cause conclusion.

## Before Running Commands

- [ ] Confirm the device and interface are the correct ones.
- [ ] Verify that you have authorization and the required access level.
- [ ] Prefer read-only `show` commands during initial investigation.
- [ ] Follow change-control approval for configuration changes.
- [ ] Avoid disruptive commands unless specifically authorized.
- [ ] Record timestamps, observations, and relevant output securely.
- [ ] Sanitize any examples before sharing or committing them publicly.

## Common Interpretation Reminders

- `administratively down` usually indicates that an interface has been disabled in configuration.
- `down/down` indicates that the interface and line protocol are not operational; further checks are needed to determine why.
- Increasing CRC errors can indicate a physical-layer or link-quality problem, but should be assessed with other evidence.
- A routing entry or reachable next hop does not alone prove that the full application path is healthy.
- CPU, memory, and interface counters should be assessed against device/platform behavior and a suitable baseline.

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [ISP Coordination](../06-ISP-Coordination/README.md)
- [Ticketing](../07-Ticketing/README.md)

## Learning Outcome

After reviewing these guides, you should be able to select relevant read-only Cisco commands for basic health and connectivity checks, interpret common interface states, collect evidence for tickets, and explain why command output must be considered in context.

## Author

**Mohamed Ashik**
