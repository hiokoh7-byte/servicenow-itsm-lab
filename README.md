# Lab 4 — ServiceNow ITSM

A hands-on lab using a free ServiceNow Personal Developer Instance to work IT tickets end to end: incident management, a self-service catalog item, a change approval workflow, and reporting.

![ServiceNow](https://img.shields.io/badge/ServiceNow-PDI-00C487?logo=servicenow&logoColor=white)
![Cost](https://img.shields.io/badge/Cost-%240-brightgreen)
![Status](https://img.shields.io/badge/Status-Complete-success)

## 🎥 Demo Video
[Watch me build this lab end-to-end →](https://www.loom.com/share/556a49187ecc4c049f187dca1e3bc882)

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

## Setup — Step by Step

### 1. Get a free instance
1. Go to `developer.servicenow.com`
2. Click **Sign Up** and create a free account — email and password only, no credit card required
3. Click **Request Instance**
4. Select the latest stable release (Washington or newer)
5. Click **Request** — the instance provisions in 10–15 minutes
6. Check your email for the instance URL (format: `dev12345.service-now.com`) and login credentials

> ServiceNow hibernates a Personal Developer Instance after 10 days of inactivity and reclaims it after 30. Log in at least once a week to keep it (and your work) alive.

### 2. Navigate the platform
Key modules used in this lab, found in the left navigation panel:
- **Incident** → Service Desk → Incidents
- **Problem** → Service Desk → Problems
- **Change** → Change → Changes
- **Service Catalog** → Service Catalog → Catalogs
- **Reports** → Reports → Create New
- **Workflow Editor** → Process Automation → Flow Designer

### 3. Create and work an incident
7. Navigate to **Service Desk → Incidents → New**
8. Fill in the form — caller (e.g. Abel Tuter), category (Software), subcategory (Email), a short description of the issue, full description, priority (3 — Moderate), and Assignment Group (Service Desk)
9. Click **Submit**
10. Note the ticket number (format: `INC0001234`)
11. Open the incident, set **State** to *In Progress*
12. Assign it to yourself
13. Add a **Work Note** documenting troubleshooting steps and an ETA (internal, IT-only)
14. Add a **Resolution Note** documenting the fix
15. Set **State** to *Resolved* → *Closed*

### 4. Build a service catalog item
16. Navigate to **Service Catalog → Catalogs → Service Catalog**
17. Click **Maintain Items → New**
18. Fill in name (e.g. "New Laptop Request"), category (Hardware), short description, full description, fulfillment group (IT Hardware Team), and leave price blank
19. Click **Submit**
20. Go to the **Variables** tab and add fields — e.g. Requester Name (text, mandatory), Business Justification (multi-line text, mandatory), Required By Date (date, mandatory), Laptop Model Preference (select box, optional)
21. **Save and Preview** — the item now appears in the catalog portal

### 5. Create a change request with an approval workflow
22. Navigate to **Change → Changes → New (Standard)**
23. Fill in short description, category, risk, impact, start/end date, and a full description including the rollback plan
24. Under the **Planning** tab, add a Test Plan and Backout Plan
25. Click **Request Approval** — moves the change to *Pending Approval*
26. Go to the **Approvals** tab and approve it as the admin user
27. Confirm the change moves to *Scheduled*

### 6. Build reports
28. Navigate to **Reports → Create New**
29. Name it (e.g. "Incident Volume by Priority — Last 30 Days")
30. Set Data to `Incident [incident]`, Type to Bar Chart, Group by to Priority
31. Add a condition: Created is on or after 30 days ago
32. Click **Save and Run**
33. Repeat for two more reports: **MTTR by Assignment Group** and **Open Incidents by Assigned Agent**

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

![Incident INC0010001](./screenshots/01-incident-INC0010001.png)
> **Takeaway:** Ticket INC0010001 shows the completed record — caller (Abel Tuter), category/subcategory (Software/Email), priority set to 3-Moderate with urgency at 1-High, routed to the Help Desk assignment group, and state moved all the way through to Closed. This is what a fully worked ticket looks like end to end, not just the initial submission.

## Service Catalog Item — New Laptop Request

Built a catalog entry so employees can request hardware without opening a ticket manually.

| Variable | Type | Mandatory |
|---|---|---|
| Requester Name | Single Line Text | Yes |
| Business Justification | Multi Line Text | Yes |
| Required By Date | Date | Yes |
| Laptop Model Preference | Select Box (Standard / Developer / Executive) | No |

Fulfillment routed to the IT Hardware Team, with a documented SLA (reviewed within 2 business days, delivered within 5–7 after approval).

![Service Catalog — New Laptop Request](./screenshots/02-service-catalog-new-laptop-request.png)
> **Takeaway:** The live catalog item as an end user would see it — the Required By Date, Laptop Model Preference dropdown, and Business Justification field all render as real form inputs in the self-service portal, with a 2-day delivery estimate shown up front. This is the difference between a ticket type and an actual self-service experience.

## Change Request & Approval Workflow

**Scenario:** Deploy security patch MS24-001 to all Windows workstations.

| Field | Value |
|---|---|
| Risk | Low |
| Impact | 2 — Medium |
| Window | Saturday 2:00 AM – 6:00 AM |

Included a documented test plan and backout plan, then submitted for approval. Approved the change as admin and confirmed it moved to *Scheduled* — demonstrating the control that prevents uncoordinated changes to production.

![Change Request CHG0030001](./screenshots/03-change-request-CHG0030001.png)
> **Takeaway:** CHG0030001 sitting in the *Scheduled* state on the workflow bar, having already cleared *Assess* and *Authorize*. This is the visual proof that the approval gate actually worked — the change couldn't reach Scheduled without being authorized first.

## Reports Built

- **Incident Volume by Priority** — last 30 days, bar chart
- **Mean Time to Resolution (MTTR)** — grouped by Assignment Group
- **Open Incidents by Assigned Agent** — used for workload balancing

![Report — Open Incidents by Assigned Agent](./screenshots/04-report-open-incidents-by-agent.png)
> **Takeaway:** The donut chart breaks down open incidents by assignee — a large chunk (37.5%) unassigned, ITIL User carrying 20% of the load, and the rest spread thin across individual agents. This is the exact kind of view a team lead uses to catch an unbalanced queue before it becomes a bottleneck.

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
