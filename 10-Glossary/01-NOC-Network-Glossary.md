# NOC and Network Operations Glossary

A quick-reference glossary for common terms used in Network Operations Center (NOC) monitoring, troubleshooting, ISP coordination, and incident management.

> **Confidentiality:** This is a generic learning reference. Do not add real customer details, internal IP addresses, circuit IDs, ticket IDs, credentials, or other confidential production information.

---

## 1. NOC and Link Types

| Term | Full Form | Simple Meaning |
|---|---|---|
| NOC | Network Operations Center | Team or function that monitors and supports network services |
| ISP | Internet Service Provider | Provider supplying internet or network connectivity |
| ILL | Internet Leased Line | Dedicated internet connectivity service |
| P2P | Point-to-Point | Direct connectivity between two network endpoints |
| LAN | Local Area Network | Network within a limited area, such as an office |
| WAN | Wide Area Network | Network connecting sites over a larger geographic area |
| CPE | Customer Premises Equipment | Network equipment installed at the customer site |
| POP | Point of Presence | Provider location where network services are made available |
| NMS | Network Management System | Platform used to monitor network devices and links |

## 2. Incident and Communication Terms

| Term | Full Form | Simple Meaning |
|---|---|---|
| ETA | Estimated Time of Arrival | Expected arrival time; in operations, clarify what event the estimate refers to |
| ETR | Estimated Time to Restore | Expected time when the affected service will be restored |
| TETR | Tentative Estimated Time to Restore | Tentative or provisional restoration estimate; usage can vary by organization |
| RCA | Root Cause Analysis | Process of identifying and documenting the underlying cause of an incident |
| SLA | Service Level Agreement | Agreed service expectations and measurable commitments |
| MTTR | Mean Time to Repair / Restore / Resolve | A time-based reliability metric; the exact expansion depends on organizational usage |
| Ticket ID | Ticket Identifier | Reference used to track an incident or service request |
| Escalation | — | Raising an issue to a higher support level or responsible team |
| Follow-up | — | Contacting the responsible party for a status update |
| Handover | — | Passing current status, pending actions, and important details to the next shift |
| Maintenance Window | — | Approved period for planned maintenance or changes |

**Note:** ETA, ETR, TETR, and MTTR may be defined differently in internal procedures. Follow your organization's approved definitions.

## 3. Link and Performance Terms

| Term | Full Form | Simple Meaning |
|---|---|---|
| Link Down | — | Link is unavailable or not operational |
| Link Flapping | — | Link repeatedly changes between up and down |
| Latency | — | Time taken for data to travel between endpoints |
| Packet Loss | — | Some transmitted packets fail to reach the destination |
| RTT | Round-Trip Time | Time for a packet to travel to a destination and for the response to return |
| Jitter | — | Variation in packet delay |
| Bandwidth | — | Capacity of a connection, commonly expressed in Mbps or Gbps |
| Throughput | — | Actual rate of successful data transfer |
| Availability | — | Portion of time a service is operational |
| Uptime | — | Time a device or service remains operational |
| Downtime | — | Time a device or service is unavailable |
| Interface | — | Physical or logical connection on a network device |
| CRC Error | Cyclic Redundancy Check Error | Error indicating a frame failed an integrity check |
| Drop | — | Packet or frame discarded by a device or interface |
| Failover | — | Switching to a backup path or device when the primary path fails |
| Redundancy | — | Additional components or paths that help maintain service if one fails |

## 4. Monitoring and Troubleshooting Terms

| Term | Full Form | Simple Meaning |
|---|---|---|
| Alert | — | Notification generated when a monitored condition meets a rule |
| Alarm | — | Warning or fault indication requiring attention |
| Reachability | — | Whether a device or destination can be reached |
| Ping | Packet Internet or Inter-Network Groper | Utility commonly used to test IP reachability and measure response time |
| Traceroute / Tracert | — | Utility that helps show the network path toward a destination |
| DNS | Domain Name System | Translates domain names into IP addresses |
| DHCP | Dynamic Host Configuration Protocol | Automatically provides IP configuration to clients |
| Gateway | — | Device or next hop used to reach networks outside the local subnet |
| Routing | — | Process of selecting paths for packets between networks |
| Interface Status | — | Reported state of a device interface |
| Logs | — | Recorded events used to investigate device or service behavior |
| Baseline | — | Normal or expected performance used for comparison |
| False Positive | — | Alert that indicates a problem when the condition is not actually present |
| Correlation | — | Comparing related events to understand whether they share a cause |

## 5. Ticket Priority and Service Management

| Term | Full Form | Simple Meaning |
|---|---|---|
| Priority | — | Order in which an incident should be handled, based on impact and urgency |
| Severity | — | Degree of seriousness or technical/business impact |
| Impact | — | Effect of an incident on users, services, or business operations |
| Urgency | — | How quickly action is needed |
| P1 / P2 / P3 / P4 | Priority levels | Common priority labels; exact definitions depend on company policy |
| Acknowledgement | — | Confirmation that a report or ticket has been received |
| Resolution | — | Action or outcome that resolves the incident |
| Closure | — | Formal completion of a ticket after required checks |
| Recurring Incident | — | An issue that happens repeatedly |
| Change | — | Authorized modification to a network or service |
| Preventive Action | — | Action intended to reduce the chance of recurrence |
| Corrective Action | — | Action taken to correct an identified problem |

## 6. Common NOC Status Wording

| Phrase | Meaning |
|---|---|
| Under Investigation | Checks are in progress; the cause may not yet be known |
| Awaiting ISP Update | Waiting for the provider's response |
| ETR Pending | A restoration estimate has not yet been provided or confirmed |
| ETR Exceeded | The previously advised restoration estimate has passed |
| Restored — Verification Pending | Restoration was reported, but internal checks are not complete |
| Restored and Verified | Internal checks confirm service restoration |
| Monitoring for Stability | Service is available and being observed for recurrence |
| Root Cause Not Confirmed | Available evidence is insufficient to state the cause |
| Escalated | Raised to the designated higher support level or team |

## 7. Quick Reference: Common Distinctions

- **Link Down vs Link Flapping:** Down means unavailable at the time of checking; flapping means repeated up/down transitions.
- **Latency vs Packet Loss:** Latency is delay; packet loss is packets that do not reach the destination.
- **Bandwidth vs Throughput:** Bandwidth is link capacity; throughput is the actual successful transfer rate.
- **Symptom vs Root Cause:** A symptom describes what happened; the root cause explains why it happened.
- **Resolution vs Prevention:** Resolution addresses the current incident; preventive action reduces future recurrence.
- **ISP Restoration vs Verified Restoration:** An ISP update should be followed by internal verification according to the operational process.

## 8. Practical Learning Tip

When you see a new NOC term, note:

1. Its full form or definition
2. Where it appears (monitoring tool, ticket, email, or device CLI)
3. What action it requires
4. How the action and outcome should be documented

Use your organization's approved SOP for priority levels, SLA rules, escalation timing, and internal terminology.

---

## Author

**Mohamed Ashik**

Network Monitoring | NOC | ISP Coordination | Networking | Cloud Security Learning
