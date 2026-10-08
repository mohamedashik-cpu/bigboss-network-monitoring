# BigBoss Network Monitoring

A practical learning portfolio documenting Network Operations Center (NOC) concepts from network-monitoring internship exposure. This repository focuses on monitoring, first-line troubleshooting, ISP coordination, ticket handling, and incident documentation.

> **Confidentiality and scope:** This is a personal learning repository, not an official company document. It contains generic learning material only. Never upload customer or company-confidential information, internal IP addresses, circuit IDs, ticket/reference IDs, credentials, monitoring screenshots, personal contact details, or proprietary configurations.

## Repository Guide

| Section | Topics and practical guides |
|---|---|
| [01 — Network Monitoring](01-Network-Monitoring/README.md) | ISP monitoring, OpManager concepts, device reachability, link status/flapping, alert verification, monitoring checklists and logs |
| [02 — Troubleshooting](02-Troubleshooting/README.md) | Link-down investigation, packet loss, high latency, DNS and connectivity checks |
| [03 — Cisco Commands](03-Cisco-Commands/README.md) | Device health, interface and port troubleshooting, configuration and operational verification |
| [04 — ILL](04-ILL/README.md) | Internet Leased Line monitoring, troubleshooting, ISP tickets, follow-up and restoration verification |
| [05 — P2P](05-P2P/README.md) | Point-to-Point monitoring, troubleshooting, ticketing and ISP follow-up |
| [06 — ISP Coordination](06-ISP-Coordination/README.md) | ISP call/email communication, ticket references, ETR follow-up and escalation |
| [07 — Ticketing](07-Ticketing/README.md) | Ticket lifecycle, updates, priority/severity, SLA tracking, shift handover, recurring incidents, maintenance and RCA tracking |
| [08 — RCA](08-RCA/README.md) | Root Cause Analysis workflow, evidence collection, incident timelines and corrective/preventive actions |
| [09 — Email Templates](09-Email-Templates/README.md) | Generic link-down/flapping emails, follow-ups, escalations and restoration updates |
| [10 — Glossary](10-Glossary/README.md) | Common NOC, networking, incident and service-management terms |

## Common NOC Incident Workflow

**Monitor → Verify Alert → Identify Scope and Impact → Perform Authorized Checks → Create/Update Ticket → Coordinate with Team/ISP → Track Status and ETR → Verify Restoration → Monitor Stability → Document and Close**

Use the organization's approved SOP, access rules, escalation path, and change-control process. Run commands only on systems you are authorized to access. An alert or symptom alone does not prove the root cause.

## Documentation Principles

- Use generic, sanitized scenarios rather than real production incidents.
- Record observations and timestamps accurately.
- Separate confirmed facts from assumptions and suspected causes.
- Include useful verification steps and outcomes.
- Keep each guide focused; avoid unnecessary duplicate files.
- Store real customer, circuit, ticket and ISP details only in approved company systems.

## Learning Objectives

This repository is intended to build practical knowledge of:

- NOC monitoring and alert verification
- Basic network and interface troubleshooting
- ILL and P2P incident handling
- Cisco device health and operational checks
- ISP communication, follow-up and escalation
- Ticket lifecycle, SLA awareness and shift handover
- Incident timelines, RCA and service-restoration verification

## Author

**Mohamed Ashik**

Network Monitoring · NOC Operations · Networking · Cloud Security Learning
