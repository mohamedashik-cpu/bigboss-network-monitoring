# Internet Leased Line (ILL)

This section covers generic NOC practices for monitoring and troubleshooting Internet Leased Line (ILL) connectivity, coordinating with the ISP, tracking service restoration, and documenting the incident.

> **Confidentiality:** This public learning repository must contain only sanitized examples. Do not publish real circuit IDs, customer/site details, internal IP addresses, ISP ticket references, credentials, monitoring screenshots, or company-confidential information.

## Guides in This Section

1. [ILL Monitoring and Troubleshooting](01-ILL-Monitoring-and-Troubleshooting.md) — ILL basics, common link symptoms, initial checks, escalation, and restoration verification.
2. [ILL Ticket and ISP Follow-up Workflow](02-ILL-Ticket-and-ISP-Follow-up-Workflow.md) — information to prepare for an ISP ticket, reference tracking, follow-ups, ETR tracking, escalation, and closure.

## What to Monitor

- Link status: Up, Down, or Flapping
- Device and interface reachability/status
- Packet loss and latency, where monitored
- Relevant alerts, event history, and interface errors
- Open ISP tickets, latest updates, and ETR
- Service status after the ISP reports restoration

Use the approved monitoring platform and internal SOP. An alert should be verified before it is treated as a confirmed outage.

## ILL Incident Workflow

**Monitor → Verify Alert → Check Device/Interface → Collect Evidence → Raise or Update ISP Ticket → Record Reference → Follow Up → Track ETR → Verify Restoration → Monitor Stability → Document and Close**

### Initial Verification

- [ ] Confirm the correct ILL link and current status.
- [ ] Check the alert timestamp and recent event history.
- [ ] Perform authorized device, interface, and connectivity checks.
- [ ] Record the observed symptom and available evidence.
- [ ] Check whether an existing incident or ISP ticket is already open.

### ISP Coordination

Prepare the verified link type, bandwidth, approved site identifier, circuit reference, observed symptom, start time, impact, and relevant test results. Share real operational details only through approved company channels.

When contacting the ISP:

- Request a ticket/reference number.
- Ask for the current investigation status.
- Request an ETR when appropriate.
- Record each follow-up and the next expected update.
- Escalate according to the approved process if the issue persists or the advised ETR is exceeded.

### Restoration Verification

An ISP restoration message is not by itself proof of end-to-end recovery. Follow the approved checks to confirm the link is available, connectivity is working as expected, and the service remains stable. Document the verification result and continue monitoring as required.

## Quick Incident Record

| Field | What to record |
|---|---|
| Link type | ILL |
| Symptom | Down / Flapping / Packet Loss / High Latency |
| Detected at | Verified date and time |
| Impact | Confirmed service impact |
| Checks performed | Approved checks and results |
| ISP reference | Internal ticket/reference, stored in approved systems |
| Latest ISP update | Factual status |
| ETR | As advised by the ISP, or Pending |
| Restoration | Time and verification result |
| Next action | Follow-up, escalation, monitoring, or closure |

Do not use invented timestamps or assume a root cause without evidence.

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [P2P](../05-P2P/README.md)
- [ISP Coordination](../06-ISP-Coordination/README.md)
- [Ticketing](../07-Ticketing/README.md)
- [RCA](../08-RCA/README.md)

## Learning Outcome

After reviewing these guides, you should be able to explain basic ILL monitoring, carry out approved first-line checks, provide clear evidence to an ISP, track ticket progress and ETR, and verify service restoration before closure.

## Author

**Mohamed Ashik**
