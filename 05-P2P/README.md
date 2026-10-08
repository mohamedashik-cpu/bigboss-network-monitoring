# Point-to-Point (P2P) Links

This section documents generic NOC practices for monitoring and troubleshooting Point-to-Point (P2P) connectivity, coordinating with the ISP, tracking incidents, and verifying restoration.

> **Confidentiality:** Keep this repository generic and sanitized. Never publish real circuit IDs, customer/site details, internal IP addresses, ticket references, credentials, monitoring screenshots, or company-confidential information.

## Guides in This Section

1. [P2P Monitoring and Troubleshooting](01-P2P-Monitoring-and-Troubleshooting.md) — P2P basics, link health indicators, common symptoms, first-line checks, and restoration verification.
2. [P2P Ticket and ISP Follow-up](02-P2P-Ticket-and-ISP-Follow-up.md) — information for raising an ISP ticket, reference tracking, follow-up, ETR tracking, escalation, and closure.

## What to Monitor

- Link state: Up, Down, or Flapping
- Device and interface reachability/status
- Packet loss and latency, where available
- Interface errors and relevant device logs
- Alert history and repeated interruptions
- ISP ticket status, latest update, and ETR
- Link stability after reported restoration

Use the approved monitoring platform and internal procedures. Verify an alert and its scope before treating it as a confirmed incident.

## P2P Incident Workflow

**Monitor → Verify → Identify Affected Link → Perform Approved Checks → Record Evidence → Raise/Update ISP Ticket → Track Reference and ETR → Follow Up/Escalate → Verify Restoration → Monitor Stability → Document and Close**

## First-Line Checklist

- [ ] Confirm the correct P2P link and current alert state.
- [ ] Record the alert time and relevant event history.
- [ ] Check device and interface status where authorized.
- [ ] Run approved connectivity checks and record the results.
- [ ] Review relevant interface counters or logs if available and authorized.
- [ ] Determine what is known and what still needs investigation.
- [ ] Check for an existing ISP ticket before creating a duplicate.
- [ ] Record the ISP reference and any advised ETR.
- [ ] Follow up or escalate according to the approved process.
- [ ] Verify restoration and stability before closing the incident.

## Common P2P Symptoms

| Symptom | Initial focus | Next step |
|---|---|---|
| Link Down | Confirm status, scope, device/interface state, and recent events | Collect evidence and follow the incident process |
| Link Flapping | Check repeated up/down transitions and event timestamps | Track recurrence and coordinate with the responsible team/ISP |
| Packet Loss | Perform approved repeat tests and compare available evidence | Record test conditions and investigate the likely path |
| High Latency | Compare repeated measurements and relevant destinations | Document observations and escalate with evidence |
| Interface Errors | Review relevant counters and logs | Follow the approved troubleshooting process |

These checks help describe the symptom; they do not automatically prove the root cause.

## ISP Coordination and Restoration

When raising or following up on a P2P incident, provide verified details through approved company channels. Request the ISP ticket/reference number, current investigation status, and ETR where appropriate. If the ETR is exceeded or the issue continues, follow the organization's escalation process.

After the ISP reports restoration, perform the approved connectivity and monitoring checks. Record whether the link is available and stable. If it is still flapping or unavailable, report the observed facts and continue the incident process.

## Generic Incident Record

| Field | Example value |
|---|---|
| Link type | P2P |
| Symptom | Down / Flapping / Packet Loss / High Latency |
| Detection time | Verified timestamp |
| Checks | Approved tests and observed results |
| Impact | Confirmed service impact |
| ISP reference | Stored in approved internal systems |
| ETR | ISP-advised time or Pending |
| Current status | Investigating / Monitoring / Restored |
| Next action | Follow-up, escalation, or verification |

Do not invent timestamps, claim an unconfirmed root cause, or add real production identifiers to this public repository.

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [Cisco Commands](../03-Cisco-Commands/README.md)
- [ILL](../04-ILL/README.md)
- [ISP Coordination](../06-ISP-Coordination/README.md)
- [Ticketing](../07-Ticketing/README.md)
- [RCA](../08-RCA/README.md)

## Learning Outcome

After reviewing these guides, you should be able to describe common P2P link symptoms, perform authorized first-line checks, coordinate an evidence-based ISP ticket, track follow-ups and ETR, and verify restoration before closure.

## Author

**Mohamed Ashik**
