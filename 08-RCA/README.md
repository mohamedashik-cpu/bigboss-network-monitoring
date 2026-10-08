# Root Cause Analysis (RCA)

This section explains how to investigate network incidents systematically, distinguish symptoms from confirmed causes, preserve evidence, and document corrective and preventive actions.

> **Confidentiality:** Keep this repository generic. Never publish customer details, internal IP addresses, circuit IDs, production ticket references, credentials, screenshots, or confidential logs/configurations.

## Guides in This Section

1. [RCA Overview and Workflow](01-RCA-Overview-and-Workflow.md) — RCA purpose, when it is required, evidence collection, incident timelines, root-cause confirmation, and a reusable generic format.

Additional RCA guides should be added only when they provide a distinct practical benefit and do not repeat the ticketing documentation.

## RCA Workflow

**Define Incident → Record Impact → Build Timeline → Collect Evidence → Analyze Possible Causes → Confirm Cause Using Evidence → Document Corrective Action → Define Preventive Action → Track Actions → Review and Close**

A ticket tracks the incident and its operational progress. RCA focuses on understanding why the incident occurred and how recurrence can be reduced.

## Core RCA Principles

- **Describe symptoms accurately:** For example, “link down” describes what was observed, not why it happened.
- **Build a reliable timeline:** Use verified monitoring, ticket, device, and provider timestamps.
- **Collect relevant evidence:** Use approved monitoring records, device/interface checks, logs, change records, and confirmed ISP updates.
- **Separate fact from assumption:** Do not present a suspected cause as confirmed.
- **Record unknown causes honestly:** If the available evidence is insufficient, state that the root cause is not confirmed or remains under investigation.
- **Distinguish actions:** Corrective actions address the identified issue; preventive actions reduce the likelihood of recurrence.
- **Track ownership and status:** Record responsible teams and pending actions according to the organization's process.

## Evidence Checklist

- [ ] Incident symptom and impact are documented.
- [ ] Detection, investigation, and restoration times are verified.
- [ ] Relevant monitoring history is reviewed.
- [ ] Authorized device/interface checks and results are recorded.
- [ ] Relevant logs, counters, or change records are considered.
- [ ] ISP findings are recorded accurately when applicable.
- [ ] Root cause is supported by evidence or explicitly marked unconfirmed.
- [ ] Corrective and preventive actions are identified where possible.
- [ ] Required follow-up actions and owners are tracked.
- [ ] Confidential details are removed from public learning material.

## Generic RCA Summary

| Field | What to record |
|---|---|
| Incident | Short description of the observed issue |
| Impact | Verified service or user impact |
| Timeline | Important events in chronological order |
| Evidence | Relevant checks, logs, monitoring, or provider findings |
| Root cause | Confirmed cause, or “Not confirmed” |
| Corrective action | Action taken to address the identified issue |
| Preventive action | Action intended to reduce recurrence |
| Follow-up | Pending actions, responsible team, and status |
| Final status | Open / Under Review / Completed, according to process |

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [Cisco Commands](../03-Cisco-Commands/README.md)
- [ISP Coordination](../06-ISP-Coordination/README.md)
- [Ticketing](../07-Ticketing/README.md)
- [Glossary](../10-Glossary/README.md)

## Learning Outcome

After reviewing this guide, you should be able to explain the RCA process, assemble a factual incident timeline, identify the evidence needed to assess a cause, and document corrective and preventive actions without confusing assumptions with confirmed findings.

## Author

**Mohamed Ashik**
