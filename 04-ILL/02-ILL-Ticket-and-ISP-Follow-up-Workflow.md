# ILL Ticket and ISP Follow-up Workflow

## Overview

When an Internet Leased Line (ILL) issue requires ISP support, the NOC team needs a structured process for ticket creation, communication, follow-up, escalation, restoration verification, and closure.

This document focuses on the **ticket and ISP coordination workflow** rather than repeating the technical troubleshooting steps covered in the ILL monitoring guide.

All examples are generic and sanitized.

## Objectives

- Raise an ILL incident with clear technical information
- Provide useful evidence to the ISP
- Track ISP ticket status
- Follow up for progress and ETR
- Escalate delayed incidents through the approved process
- Verify restoration from the monitoring side
- Maintain a clear incident timeline
- Close the ticket only after verification

## ILL Ticket Workflow

```text
Issue Detected
      |
      v
Verify Issue
      |
      v
Collect Basic Evidence
      |
      v
Raise ISP Ticket
      |
      v
Record ISP Reference
      |
      v
Follow Up
      |
      v
Get Status / ETR
      |
      +---- Still Down ----> Continue Follow-up / Escalate
      |
      +---- Restored -----> Verify Internally
                              |
                              v
                         Monitor Stability
                              |
                              v
                         Close / Update
```

## 1. Verify Before Raising the Ticket

Before contacting the ISP, confirm the issue through the approved monitoring and troubleshooting process.

Collect relevant information such as:

- Issue type
- Detection time
- Current link status
- Device/interface status
- Reachability result
- Packet-loss observation where relevant
- Latency observation where relevant
- Flapping observation where relevant
- Basic troubleshooting already completed

Avoid sending unverified assumptions such as “ISP fault confirmed” unless there is evidence supporting that conclusion.

## 2. Information Required for an ISP Ticket

A generic ILL ticket can contain:

| Information | Example |
|---|---|
| Service Type | ILL |
| Issue | Link Down |
| Detection Time | YYYY-MM-DD HH:MM |
| Current Status | Down |
| Device | Device-A |
| Interface | Interface-X |
| Verification | Reachability/interface checked |
| Troubleshooting | Basic checks completed |
| Request | Please investigate and restore |
| ETR | To be provided by ISP |

Use the organization's approved identifiers when communicating with the ISP. Do not publish those real identifiers in this repository.

## 3. Raising the ISP Ticket

Use the approved ISP communication channel, such as:

- ISP portal
- Official support email
- Approved support number
- Existing escalation channel

When raising the ticket:

1. Clearly state the service type.
2. State the issue.
3. Provide the detection time.
4. Provide relevant technical observations.
5. Mention troubleshooting already completed.
6. Request investigation.
7. Request the ISP ticket/reference number.
8. Request an estimated restoration time when available.

## 4. Generic ISP Ticket Message

A concise technical format can be:

```text
Subject: ILL Link Down - Investigation Required

Hello Team,

We are observing an ILL link-down issue for the affected service.

Issue Start Time: YYYY-MM-DD HH:MM
Service Type: ILL
Current Status: Link Down
Basic Verification: Device/interface checks completed

Please investigate the issue and provide the ISP ticket/reference number along with the current status and ETR.

Regards,
NOC Team
```

Use the organization's approved email format and actual identifiers only in authorized communication channels.

## 5. Record the ISP Reference

After the ISP creates the ticket, record the reference in the approved internal system.

Example:

```text
Internal Incident: Ticket-XXXX
ISP Reference: ISP-Ticket-XXXX
Status: ISP Investigation
ETR: Pending
```

Do not store real ticket numbers in this public repository.

## 6. ISP Follow-up

Follow-up should be based on the approved escalation timeline.

During each follow-up, confirm:

- Current ticket status
- Troubleshooting progress
- Any findings from the ISP
- Action currently being performed
- Expected next update
- ETR, if available

Example internal note:

```text
YYYY-MM-DD HH:MM - Followed up with ISP.
Status: Investigation in progress.
ETR: Pending.
Next follow-up: As per escalation process.
```

## 7. ETR Tracking

ETR means **Estimated Time of Restoration**.

When the ISP provides an ETR:

```text
Status: ISP Investigation
ETR: YYYY-MM-DD HH:MM
```

The ETR is an estimate, not confirmation of restoration.

If the ETR passes without restoration:

1. Recheck monitoring.
2. Contact the ISP.
3. Request an updated status.
4. Request revised ETR if available.
5. Escalate according to the approved process.

## 8. Escalation

Escalation may be required when:

- The service remains down beyond the expected timeline
- ETR is missed
- ISP updates are delayed
- The issue has significant business impact
- Repeated follow-ups do not produce progress
- The approved escalation threshold is reached

Use the organization's defined escalation contacts and hierarchy.

Do not invent escalation contacts or publish real contact details.

## 9. Restoration Notification

When the ISP reports that the service has been restored, do not immediately close the incident.

First verify internally:

1. Monitoring status
2. Device reachability
3. Interface state
4. Packet loss if relevant
5. Latency if relevant
6. Alert clearance
7. Service stability

## 10. Restoration Verification Example

Generic verification:

```text
Monitoring: Alert Cleared
Device: Reachable
Interface: Up / Up
Packet Loss: No abnormal loss observed
Latency: Within expected observation
Stability: Monitoring continued
```

The exact acceptance criteria depend on the service and organization's procedure.

## 11. Post-Restoration Monitoring

After restoration:

- Continue monitoring for recurrence.
- Watch for link flapping.
- Check for packet loss.
- Check latency where relevant.
- Confirm no new related alerts appear.
- Record the restoration time.

A link that briefly returns and goes down again should be treated as an ongoing incident rather than a confirmed stable restoration.

## 12. Ticket Closure

Before closure, confirm:

- Service restored
- Monitoring normal
- Interface operational
- Required testing completed
- ISP update received
- Restoration time recorded
- Internal ticket updated
- Any RCA requirement identified

If RCA is required, keep the incident open or follow the organization's separate RCA process.

## 13. Generic Incident Timeline

**Scenario:** Generic ILL link-down incident.

```text
10:00 - Monitoring alert detected
10:05 - Alert verified
10:10 - Basic device/interface checks completed
10:15 - ISP ticket raised
10:20 - ISP reference received
11:00 - ISP follow-up completed
11:05 - ETR received
12:00 - Follow-up completed
12:30 - ISP reports restoration
12:35 - NOC verifies link and monitoring
12:50 - Stability monitoring completed
13:00 - Ticket updated / closure process started
```

Times above are only examples.

## 14. Follow-up Log Template

| Time | Action | ISP Status | ETR | Next Action |
|---|---|---|---|---|
| HH:MM | Initial ticket | Investigation | Pending | Follow up |
| HH:MM | Follow-up | In progress | HH:MM | Monitor |
| HH:MM | Follow-up | Awaiting restoration | HH:MM | Escalate if required |
| HH:MM | Restoration | Restored | N/A | Verify internally |

## 15. Communication Principles

When communicating with the ISP:

- Be concise
- Give exact timestamps
- State the observed symptom
- Mention completed checks
- Ask direct questions
- Record the response
- Avoid assumptions
- Keep communication professional

Useful questions:

- “Could you please confirm the current status of the ticket?”
- “Could you please provide the latest ETR?”
- “Has any fault been identified so far?”
- “Could you please confirm the next update time?”
- “The link is still showing down on our monitoring. Could you please investigate further?”

## 16. Shift Handover

If the incident remains open at shift change, the handover should contain:

- Service type
- Issue
- Detection time
- Current status
- ISP reference
- Latest ISP update
- ETR
- Last follow-up time
- Next follow-up requirement
- Actions already completed
- Any escalation already performed

Generic example:

```text
ILL - Link Down
Status: ISP Investigation
ISP Ref: ISP-Ticket-XXXX
ETR: YYYY-MM-DD HH:MM
Last Follow-up: YYYY-MM-DD HH:MM
Next Action: Follow up at agreed time
Monitoring: Link still down
```

## 17. Ticket Quality Checklist

### Before Raising

- [ ] Issue verified
- [ ] Detection time recorded
- [ ] Service type identified
- [ ] Relevant technical evidence collected
- [ ] Basic checks completed

### After Raising

- [ ] ISP reference recorded
- [ ] Current status recorded
- [ ] ETR requested
- [ ] Follow-up time tracked
- [ ] Escalation performed when required

### After Restoration

- [ ] Monitoring checked
- [ ] Device reachable
- [ ] Interface verified
- [ ] Performance checked where relevant
- [ ] Stability monitored
- [ ] Restoration time recorded
- [ ] Ticket updated
- [ ] Closure/RCA process completed as applicable

## Important NOC Practices

- Raise tickets with evidence, not assumptions.
- Record timestamps for every important update.
- Treat ETR as an estimate.
- Do not close based only on an ISP restoration message.
- Verify recovery from the NOC side.
- Maintain a clear follow-up trail.
- Use approved escalation channels.
- Keep customer and ISP information confidential.

## Confidentiality

Never publish:

- Customer names
- Real circuit IDs
- ISP ticket numbers
- Internal ticket numbers
- Phone numbers
- Email addresses
- Production IP addresses
- Credentials
- Monitoring screenshots containing real data
- Internal escalation contacts
- Proprietary ISP information
- Company-confidential information

Use placeholders:

```text
Customer-Site-A
ILL-Circuit-XXXX
Ticket-XXXX
ISP-Ticket-XXXX
Generic-ISP
Device-A
Interface-X
X.X.X.X
```

## Key Takeaways

- Verify an ILL issue before raising an ISP ticket.
- Provide clear technical evidence to the ISP.
- Record the ISP reference and every follow-up.
- Track ETR but treat it as an estimate.
- Escalate missed or delayed restoration through the approved process.
- Verify restoration using monitoring and technical checks.
- Keep a complete incident timeline for handover and closure.

## Related Topics

- ILL Monitoring and Troubleshooting
- ISP Coordination
- Ticketing
- Monitoring Logs and Documentation
- RCA
- Shift Handover

## Author

Mohamed Ashik
