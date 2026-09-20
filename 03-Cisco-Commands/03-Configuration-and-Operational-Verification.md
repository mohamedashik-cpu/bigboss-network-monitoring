# Configuration and Operational Verification Commands

## Overview

NOC engineers may need to inspect the current operational state and review configuration-related information while troubleshooting routers and switches.

This document focuses on **read-only verification and information collection**. Configuration changes should only be performed by authorized personnel using the organization's approved change process.

## Objectives

- Verify the current operational state of a device
- Review relevant running configuration sections safely
- Check VLAN and trunk information on switches
- Review routing information
- Check ARP and MAC learning
- Verify interface configuration
- Compare configuration with operational status
- Collect evidence for troubleshooting and ticket updates

## Verification Flow

```text
Identify Issue
      |
      v
Check Operational State
      |
      v
Review Relevant Configuration
      |
      v
Compare Config vs Operational Output
      |
      v
Check Routing / VLAN / ARP / MAC
      |
      v
Collect Evidence
      |
      v
Document / Escalate
```

## 1. Check Running Configuration

Use:

```text
show running-config
```

This displays the active configuration in memory.

The output can contain sensitive information, so avoid copying the complete production configuration into notes or public repositories.

For troubleshooting, inspect only the relevant section when possible.

Examples:

```text
show running-config interface GigabitEthernet0/1
show running-config | section interface
```

Command filtering support can vary by platform and software version.

## 2. Check Startup Configuration

Use:

```text
show startup-config
```

This displays the configuration saved for use during the next reload.

A difference between running and startup configuration may be relevant during troubleshooting, but do not save or modify configuration without authorization.

## 3. Compare Running and Startup Configuration

A useful verification command on supported Cisco platforms is:

```text
show running-config
show startup-config
```

Compare relevant sections when investigating configuration persistence.

Do not use configuration-saving commands unless the approved change process specifically requires them.

## 4. Check Interface Configuration

Use:

```text
show running-config interface <interface>
```

Example:

```text
show running-config interface GigabitEthernet0/1
```

Review relevant items such as:

- Interface description
- IP address
- Shutdown state
- Speed/duplex settings where configured
- VLAN-related configuration where applicable
- Other interface-specific settings

## 5. Verify Interface Operational State

Compare configuration with:

```text
show ip interface brief
show interfaces <interface>
```

Example comparison:

```text
Configuration     -> Interface settings
Operational state -> Current up/down condition
```

This helps determine whether the configured state matches the current operational state.

## 6. Check VLAN Information

On a Cisco switch:

```text
show vlan brief
```

This can provide information about:

- VLAN IDs
- VLAN names
- VLAN status
- Assigned access ports

Example sanitized output:

```text
VLAN Name                             Status    Ports
10   USER-VLAN                        active    Gi0/1, Gi0/2
20   SERVER-VLAN                      active    Gi0/3
```

Use generic VLAN information in public documentation.

## 7. Check Trunk Status

Use:

```text
show interfaces trunk
```

This can help verify:

- Trunking interfaces
- Encapsulation information where supported
- Native VLAN
- Allowed VLANs
- Active VLANs

Example:

```text
Port        Mode         Encapsulation  Status
Gi0/24      on           802.1q         trunking
```

Actual output varies by platform.

## 8. Check Switchport Information

For a specific switch interface:

```text
show interfaces <interface> switchport
```

Example:

```text
show interfaces GigabitEthernet0/1 switchport
```

Useful information may include:

- Administrative mode
- Operational mode
- Access VLAN
- Trunk VLAN information
- Native VLAN
- Voice VLAN where configured

## 9. Check MAC Address Table

Use:

```text
show mac address-table
```

For a specific interface:

```text
show mac address-table interface <interface>
```

Example:

```text
show mac address-table interface GigabitEthernet0/1
```

This can help verify whether a switch has learned MAC addresses through a port.

Never publish real production MAC addresses.

## 10. Check ARP Table

On routers and Layer 3 switches:

```text
show ip arp
```

This can help correlate IP addresses with learned MAC addresses.

For a specific IP:

```text
show ip arp X.X.X.X
```

ARP output can contain production addressing information and should be treated as confidential.

## 11. Check Routing Table

Use:

```text
show ip route
```

For a specific destination:

```text
show ip route X.X.X.X
```

This can help verify:

- Connected routes
- Static routes
- Dynamic routing entries
- Default route
- Next-hop information

The exact route codes and output depend on the routing protocols configured.

## 12. Check Default Route

A default route is commonly visible in:

```text
show ip route
```

Look for the default route indicator where supported.

A missing or incorrect default route can affect communication with external networks.

Do not change routing configuration during routine monitoring unless authorized.

## 13. Check Routing Protocol Information

When required and authorized, protocol-specific commands may include:

### OSPF

```text
show ip ospf neighbor
show ip ospf interface brief
```

### EIGRP

```text
show ip eigrp neighbors
```

### BGP

```text
show ip bgp summary
```

The exact commands depend on the platform, software version, and configured routing protocol.

## 14. Check Access Control Information Carefully

Commands such as:

```text
show access-lists
```

may help during connectivity troubleshooting.

However, access-control output can expose security-sensitive configuration. Do not copy production ACLs or firewall/security rules into a public repository.

## 15. Operational Verification vs Configuration Verification

### Configuration Verification

Answers:

> What is configured?

Examples:

```text
show running-config interface <interface>
show vlan brief
show interfaces <interface> switchport
```

### Operational Verification

Answers:

> What is happening now?

Examples:

```text
show ip interface brief
show interfaces <interface>
show interfaces trunk
show ip route
show mac address-table
show ip arp
```

Both types of information can be useful during troubleshooting.

## 16. Generic NOC Verification Example

**Scenario:** A generic switch port is reported as having connectivity problems.

### Step 1 — Check port status

```text
show interfaces status
```

### Step 2 — Check interface details

```text
show interfaces <interface>
```

### Step 3 — Check switchport information

```text
show interfaces <interface> switchport
```

### Step 4 — Check VLAN

```text
show vlan brief
```

### Step 5 — Check MAC learning

```text
show mac address-table interface <interface>
```

### Step 6 — Check ARP if Layer 3 troubleshooting is relevant

```text
show ip arp
```

### Step 7 — Check routing if the issue is beyond the local VLAN

```text
show ip route
```

### Step 8 — Document findings

Record the relevant observations in the approved ticketing system without copying sensitive production configuration.

## 17. Generic Router Verification Example

**Scenario:** A WAN-related connectivity problem is reported.

Useful read-only checks:

```text
show ip interface brief
show interfaces <interface>
show running-config interface <interface>
show ip route
show ip arp
show logging
```

Depending on the environment, also check the relevant routing protocol.

The purpose is to compare:

```text
Configured State
       +
Operational State
       +
Routing State
       =
Troubleshooting Evidence
```

## Command Reference

| Purpose | Command |
|---|---|
| Active configuration | `show running-config` |
| Saved configuration | `show startup-config` |
| Interface configuration | `show running-config interface <interface>` |
| Interface status | `show ip interface brief` |
| Interface details | `show interfaces <interface>` |
| VLANs | `show vlan brief` |
| Trunks | `show interfaces trunk` |
| Switchport details | `show interfaces <interface> switchport` |
| MAC table | `show mac address-table` |
| ARP table | `show ip arp` |
| Routing table | `show ip route` |
| OSPF neighbors | `show ip ospf neighbor` |
| EIGRP neighbors | `show ip eigrp neighbors` |
| BGP summary | `show ip bgp summary` |
| Access lists | `show access-lists` |

## Important NOC Practices

- Use read-only commands for routine verification.
- Inspect only the relevant configuration section when possible.
- Never expose passwords, secrets, keys, or production configurations.
- Do not make routing, VLAN, interface, or ACL changes without authorization.
- Compare configuration with operational output.
- Correlate CLI output with monitoring alerts.
- Record timestamps and relevant evidence.
- Follow the approved change and escalation process.

## Confidentiality

Never publish:

- Full production running configurations
- Passwords or secrets
- Production IP addressing
- Customer names
- Circuit IDs
- Ticket IDs/numbers
- Real MAC addresses
- Internal VLAN details
- Production routing tables
- ACL/security rules
- Internal topology
- Monitoring screenshots
- Company-confidential information

Use sanitized placeholders:

```text
Device-A
Interface-X
VLAN-XX
X.X.X.X
AA:BB:CC:DD:EE:FF
Ticket-XXXX
Generic-ISP
```

## Key Takeaways

- Configuration verification shows what is configured.
- Operational verification shows what is happening now.
- Comparing both can provide useful troubleshooting evidence.
- VLAN, trunk, MAC, ARP, and routing checks help isolate connectivity problems.
- Routing-protocol commands should be used only when relevant.
- Read-only verification should come before configuration changes.
- Production configuration and security information must remain confidential.

## Related Topics

- Cisco Device Health Check
- Interface and Port Troubleshooting
- Link Down Troubleshooting
- Packet Loss and High Latency Troubleshooting
- DNS and Connectivity Troubleshooting
- ISP Coordination
- Ticketing
- RCA

## Author

Mohamed Ashik
