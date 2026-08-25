# Lab 4 — ServiceNow ITSM

A hands-on lab using a free ServiceNow Personal Developer Instance to work IT tickets end to end: incident management, a self-service catalog item, a change approval workflow, and reporting.

![ServiceNow](https://img.shields.io/badge/ServiceNow-PDI-00C487?logo=servicenow&logoColor=white)
![Cost](https://img.shields.io/badge/Cost-%240-brightgreen)
![Status](https://img.shields.io/badge/Status-Complete-success)

## 🎥 Demo Video
[Watch me build this lab end-to-end →](PASTE_YOUR_LINK_HERE)

## Overview

| Field | Value |
|---|---|
| Certification alignment | CompTIA A+ · Network+ · ITIL 4 Foundation |
| Tools used | ServiceNow Personal Developer Instance (free, no credit card) |
| Time to complete | 2–3 hours |
| Cost | $0 |
| Career relevance | IT Support, Help Desk, Sysadmin, ITSM Platform Administrator |

## The Problem This Lab Solves

When users report IT problems, those problems need to be tracked, routed, prioritized, assigned, and resolved consistently, or things fall through the cracks. ServiceNow is an IT Service Management (ITSM) platform that enforces process around this: incidents follow a defined workflow, changes require approval before they touch production, and routine requests come from a self-service catalog instead of a phone call to the help desk.

ServiceNow is one of the most widely deployed platforms in enterprise IT. Most IT support and sysadmin roles use it, or something functionally identical, from day one — so hands-on experience with it before starting a job is a real differentiator.

## What I Built

- Requested and configured a free ServiceNow Personal Developer Instance
- Created and worked a full incident lifecycle: logged a ticket, assigned it, added internal work notes, documented a resolution, and closed it
- Built a **Service Catalog item** (New Laptop Request) with custom variables so users can self-serve a common IT request instead of filing a ticket
- Created a **Change Request** with a risk/impact assessment, test plan, and backout plan, then routed it through an approval workflow
- Built reports on incident volume, resolution time, and workload distribution

## Skills Demonstrated

| Skill | Real-world application |
|---|---|
| Creating and resolving an Incident | The most common task in every IT support role, from day one |
| Setting ticket priority and SLA | Priority drives response time commitments to the business |
| Assigning tickets to queues and individuals | Correct routing avoids wasted time and delayed resolution |
| Building a Service Catalog item | Lets users self-serve routine requests, reducing ticket volume |
| Creating an approval workflow | Change requests need authorization before touching production |
| Running reports on ticket data | Metrics drive IT operations decisions at every level |
| Understanding ITIL Incident / Problem / Change | The core process vocabulary used across enterprise IT |

## Incident Walkthrough

**Scenario:** User cannot access Outlook — "Cannot connect to server."

| Field | Value |
|---|---|
| Category / Subcategory | Software / Email |
| Priority | 3 — Moderate |
| Assignment Group | Service Desk |

**Process followed:**
1. Logged the incident with caller, category, and description
2. Set state to *In Progress* and self-assigned
3. Added a work note documenting troubleshooting steps and an ETA
4. Documented the resolution (corrupted Outlook profile, rebuilt account)
5. Closed the ticket with user confirmation

## Service Catalog Item — New Laptop Request

Built a catalog entry so employees can request hardware without opening a ticket manually.

| Variable | Type | Mandatory |
|---|---|---|
| Requester Name | Single Line Text | Yes |
| Business Justification | Multi Line Text | Yes |
| Required By Date | Date | Yes |
| Laptop Model Preference | Select Box (Standard / Developer / Executive) | No |

Fulfillment routed to the IT Hardware Team, with a documented SLA (reviewed within 2 business days, delivered within 5–7 after approval).

## Change Request & Approval Workflow

**Scenario:** Deploy security patch MS24-001 to all Windows workstations.

| Field | Value |
|---|---|
| Risk | Low |
| Impact | 2 — Medium |
| Window | Saturday 2:00 AM – 6:00 AM |

Included a documented test plan and backout plan, then submitted for approval. Approved the change as admin and confirmed it moved to *Scheduled* — demonstrating the control that prevents uncoordinated changes to production.

## Reports Built

- **Incident Volume by Priority** — last 30 days, bar chart
- **Mean Time to Resolution (MTTR)** — grouped by Assignment Group
- **Open Incidents by Assigned Agent** — used for workload balancing

## ITIL Concepts Applied

| ITIL Term | Definition | ServiceNow Module |
|---|---|---|
| Incident | Unplanned interruption to a service; goal is fast restoration | Service Desk → Incidents |
| Problem | Root cause behind one or more incidents; goal is permanent elimination | Service Desk → Problems |
| Change | Planned modification to infrastructure or applications | Change → Changes |
| Service Request | A request for something new (access, hardware); not a break/fix | Service Catalog |
| SLA | Committed response and resolution time by priority level | SLA → SLA Definitions |
| CMDB | Record of every IT asset and its relationships | Configuration → CIs |
| Knowledge Base | Documented known issues and solutions, reducing repeat incidents | Knowledge → Articles |

## Notes / Lessons Learned

- ServiceNow hibernates a Personal Developer Instance after 10 days of inactivity and reclaims it after 30 — logging in weekly keeps it (and the work in it) alive.
- Separating **work notes** (internal, IT-only) from **resolution notes** (customer-facing) reflects real help desk practice and keeps the audit trail clean.
- The approval step on the change request is the actual control — without it, anyone could push a change straight to production.

## Related Labs

- **Lab 3** — Splunk SIEM & Log Analysis

---

*Part of a home-lab portfolio built to demonstrate practical IT support and ITSM skills for entry-level roles.*
