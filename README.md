GoHighLevel CRM - Full Build for Australian Professional Services Firm

Project Overview

A complete GoHighLevel CRM implementation built from 
scratch for Meridian Professional Services - a fictional 
Australian advisory firm used to demonstrate a 
production-grade GHL build.

This build covers the full commercial scope of a real 
GHL implementation project: paid ad lead capture, 
CRM pipeline architecture, funnel design, calendar 
system, 10 automated workflows, UTM attribution 
tracking, and Xero accounting integration via Make.com.

Every element of this build addresses a real operational 
problem that professional services firms face. 
The architecture decisions, automation logic, and 
integration design reflect how this would be built 
for a paying client - not a tutorial exercise.**

---

The Problem This Build Solves

Before This Build - The Manual Reality

An Australian professional services firm was managing 
its entire lead and client operation manually:

| Problem | Business Impact |
|---------|----------------|
| Paid ad leads captured in a spreadsheet | No real-time CRM visibility. Leads sat uncontacted for hours |
| Manual email responses to enquiries | Inconsistent response time. Some leads never received a reply |
| No pipeline structure | No visibility into lead stages, deal values, or conversion rates |
| Manual team notifications | Leads assigned by whoever happened to check the inbox |
| No follow-up system | Leads that did not convert immediately were forgotten |
| No appointment automation | Discovery calls booked manually by email back-and-forth |
| New clients onboarded manually | 4–6 manual steps per client with frequent items missed |
| No Xero integration | Client data entered twice — once in CRM, once in Xero |
| No attribution tracking | No way to know which ad campaigns generated revenue |

Estimated manual time per lead from enquiry to onboarding: 
3–5 hours of staff time spread across multiple people 
over multiple days.

---

The Solution — What Was Built

1. Paid Ad Lead Capture System
A complete landing page and form system that captures 
leads from paid Google and Meta advertising, 
including UTM parameter tracking that identifies 
exactly which campaign, ad, and keyword generated 
each lead.

2. CRM Pipeline Architecture
Two structured pipelines covering the full client 
journey from first enquiry to long-term retention:

New Business Pipeline - 11 Stages:
```
New Enquiry → Attempted Contact → Contacted → 
Discovery Booked → Discovery Complete → 
Proposal Sent → Proposal Follow-Up → 
Verbal Commitment → Closed Won → 
Closed Lost → Nurture
```

Client Success Pipeline - 7 Stages:
```
Active Client → Renewal Due → 
Upsell Opportunity → Renewal Sent → 
Renewed → At Risk → Churned
```

3. Multi-Page Funnel System
Two complete funnels:

Paid Ad Lead Funnel:
- Landing page with embedded enquiry form
- Hero section with headline, trust signals, and form
- Services section with four service cards
- Social proof section with testimonials
- Professional footer with ABN and legal compliance
- Thank You page with discovery call CTA

Discovery Call Booking Funnel:
- Pre-qualification page
- Calendar booking page
- Booking confirmation page

4. Calendar System
Two calendars handling different stages of the 
client journey:

Discovery Call Calendar:
- Round Robin across three advisors
- 30-minute appointments
- 15-minute buffer after each call
- 4-hour minimum advance booking
- 14-day maximum booking window
- Automated confirmation, 24-hour, and 1-hour reminders

Follow-Up Call Calendar:
- Routes to contact owner (same advisor as Discovery)
- 15-minute appointments
- Ensures relationship continuity at the proposal stage

5. Ten Automated Workflows
A complete automation stack covering every stage 
of the lead and client lifecycle:

| # | Automation | Trigger | Purpose |
|---|-----------|---------|---------|
| 01 | Paid Ad Lead Entry | Form submitted | Tags, creates opportunity, assigns rep, creates task |
| 03 | Immediate Response | new-lead tag | SMS at 2 min, email at 5 min |
| 04 | Follow-Up No Response | new-lead tag | Day 1, 3, 7, 14 follow-up sequence |
| 05 | Appointment Booked | Appointment created | Stops follow-up, moves pipeline, sends reminders |
| 06 | Post-Discovery | Appointment complete | Thank you email, proposal task |
| 07 | Proposal Sent | Pipeline stage | Day 2, 5, 10 follow-up |
| 08 | Closed Won | Pipeline stage | Welcome email, Xero webhook, onboarding tasks |
| 09 | Closed Lost | Pipeline stage | 9-month nurture sequence |
| 10 | Stop All | Tag added | Emergency kill switch — stops all sequences |

6. Xero Integration via Make.com
A Make.com scenario that fires the moment a deal 
is marked Closed Won in GHL — automatically creating 
or updating the client record in Xero with full 
duplicate detection and sync logging.

Make.com Scenario Architecture:
```
GHL Webhook → Xero Search (duplicate check) → 
Router (exists/new) → 
Path A: Update existing Xero contact
Path B: Create new Xero contact → 
Google Sheets sync log → 
GHL contact update (Xero Client ID written back)
```

7. UTM Attribution Tracking
Complete paid ad attribution- every lead captured 
with utm_source, utm_medium, utm_campaign, utm_term, 
and utm_content - enabling the client to trace 
revenue back to specific ad campaigns.

---

Architecture Decisions and Why

Why Two Separate Pipelines
A single pipeline cannot serve both the sales 
motion (new business) and the retention motion 
(client success) without mixing signals. Separate 
pipelines give each function clean reporting, 
appropriate stages, and independent automation triggers.

Why Automations 01 and 03 Are Separate
Automation 01 fires on form submission. 
Automation 03 fires on the new-lead tag. 
This separation means the immediate response 
sequence can serve any lead source — paid ad, 
organic, referral, manual entry — without 
rebuilding the logic. One response sequence 
serves all entry points.

Why Stop Conditions Are Critical
Every follow-up sequence has explicit stop conditions. 
Without them a prospect who books a call on Day 2 
would still receive the Day 3 SMS, Day 7 email, 
and Day 14 closing email — after they have 
already engaged. Stop conditions are the difference 
between a professional automated system and 
an automated annoyance

Why Round Robin for Discovery but Not Follow-Up
Round Robin on Discovery Call distributes new leads 
fairly across the advisory team. But Follow-Up calls 
route to the contact owner — the same advisor who 
handled the Discovery Call. Switching advisors at the 
proposal stage breaks relationship continuity and 
loses the context built during the first call.

Why Xero Integration Uses Make.com
GoHighLevel has no native Xero connector. The Make.com 
bridge was chosen over direct API calls because it 
is maintainable by a non-developer, provides a 
visual error log, supports conditional logic 
(duplicate detection), and can be extended without 
touching GHL's automation configuration.

---

ROI - Measurable Business Impact

Time Saved Per Lead

| Task | Before (Manual) | After (Automated) | Time Saved |
|------|----------------|-------------------|------------|
| First response to lead | 2–4 hours | Under 5 minutes | 115–235 min |
| CRM record creation | 5 minutes | Instant | 5 min |
| Team notification | 5 minutes | Instant | 5 min |
| Task creation | 3 minutes | Instant | 3 min |
| Follow-up scheduling | 10 minutes | Automatic | 10 min |
| Appointment reminders | 5 minutes per appointment | Automatic | 5 min |
| Post-call email | 10 minutes | Automatic | 10 min |
| Proposal follow-up | 15 minutes per follow-up | Automatic | 45 min (3 follow-ups) |
| Client onboarding tasks | 10 minutes | Automatic | 10 min |
| Xero client entry | 8 minutes | Automatic | 8 min |
| **Total per lead** | **~73–101 minutes** | **~0 minutes** | **~90 minutes** |

At 20 leads per month:** 1,800 minutes = **30 hours of staff time saved monthly**

**At an average staff cost of $35/hour:** **$1,050 saved per month in administrative labour**

 Response Time Impact

Research consistently shows that responding to 
a B2B lead within 5 minutes increases the 
probability of qualification by over 400% 
compared to responding within 10 minutes.

**Before:** Average first response time: 2–4 hours
**After:** Automated SMS and email within 5 minutes

**Conversion rate impact:** Even a conservative 
20% improvement in lead-to-discovery conversion 
rate represents significant revenue at typical 
professional services deal values of $5,000–$50,000+.

Attribution Value

Without UTM tracking the client had no way to know 
which paid ad campaigns generated revenue. 
Ad spend decisions were based on gut feel.

With UTM attribution now flowing through to 
every GHL contact record — the client can run 
a simple report to see:

- Which campaigns generated the most leads
- Which campaigns generated the highest-value leads
- Which keywords converted at the highest rate
- Which ad creatives produced the most qualified prospects

**This data directly informs where to increase, 
decrease, or reallocate ad spend - typically 
improving paid ad ROI by 15–30% when acted on.**

No-Lead-Left-Behind Value

The 9-touch follow-up system (Automations 03, 04, 07) 
ensures no lead is forgotten. Before automation — 
leads that did not respond immediately were typically 
abandoned after one or two manual attempts.

**Industry data shows that 80% of sales require 
5 or more follow-up contacts. Most salespeople 
give up after 2.**

The automated sequences deliver up to 9 touchpoints 
(SMS, email, phone task) across 14 days without 
requiring the advisor to remember or manually execute 
each one.

**Conservative estimate: 1 additional closed deal 
per quarter from previously-abandoned follow-ups 
at an average deal value of $15,000 = $60,000 
additional annual revenue.**

---

Custom Fields Built

| Field | Type | Purpose |
|-------|------|---------|
| Service Interest | Dropdown | Lead qualification and routing |
| Business Type | Dropdown | Proposal personalisation |
| Annual Revenue | Dropdown | Lead scoring and tier routing |
| Number of Employees | Dropdown | Enterprise vs SME classification |
| Urgency | Dropdown | Priority assignment |
| UTM Source | Text | Paid ad attribution |
| UTM Medium | Text | Channel attribution |
| UTM Campaign | Text | Campaign attribution |
| UTM Term | Text | Keyword attribution |
| Lead Score | Number | Qualification scoring |
| Xero Client ID | Text | CRM-accounting system link |
| Proposal Sent Date | Date | Cycle time reporting |
| Estimated Deal Value | Currency | Pipeline value reporting |
| Qualification Date | Date | Time-to-qualify reporting |

---

Tags Used

```
new-lead           paid-ad-lead        organic-lead
referral-lead      qualified           unqualified
proposal-sent      follow-up-1         follow-up-2
follow-up-3        no-response         booked-appointment
appointment-complete  closed-won       closed-lost
xero-client        nurture-sequence    stop-all-automations
```

---

Screenshots

Pipelines

New Business Pipeline — All 11 Stages


Client Success Pipeline


---

Forms

Paid Ad Enquiry Form — All Fields


Hidden UTM Fields Configuration


---

Funnels

Paid Ad Landing Page — Hero Section


Paid Ad Landing Page — Services Section


Discovery Call Booking Funnel — Calendar Page
![Calendar Booking Page](screenshots/03-funnels/06-discovery-funnel-calendar-page.png)

---

Calendars

Discovery Call Calendar — Round Robin Settings
![Discovery Calendar](screenshots/04-calendars/02-discovery-call-team-members-round-robin.png)

Discovery Call Calendar — Confirmation Email
![Calendar Confirmation](screenshots/04-calendars/04-discovery-call-confirmation-email.png)

---

Automations

All 10 Workflows — Overview

Automation 01 — Paid Ad Lead Entry

Automation 03 — Immediate Response with Stop Condition

Automation 04 — Follow-Up Sequence with Condition Checks

Automation 08 — Closed Won with Xero Webhook

Automation 10 — Emergency Kill Switch


---

Contact Record

UTM Fields Populated After Paid Ad Form Submission

All Four Onboarding Tasks Created Automatically


---

Make.com — Xero Integration

Full Scenario Canvas
![Make.com Scenario](screenshots/07-makecom-xero/01-makecom-scenario-full-canvas.png)

---

Tools Used

| Tool | Purpose |
|------|---------|
| GoHighLevel | CRM, pipelines, automations, funnels, calendars |
| Make.com | Xero integration bridge |
| Xero | Accounting system (client record creation) |
| Google Sheets | Xero sync audit log |
| Gmail | Automated email delivery |

---

Certifications Relevant To This Build

- Make Basics Certification — Make Academy, 2026
- Google AI Essentials — Google via Coursera, 2026
- Certified Airtable Builder — Airtable, 2026
- CRM Certification — CICRM, 2022

---

Key Takeaway

Most GHL implementations fail at three points:

**1. UTM attribution is not configured** — leads arrive 
with no source data. Ad spend becomes untraceable.

**2. Stop conditions are missing** — contacts receive 
follow-up messages after they have already engaged. 
Trust is damaged.

**3. Xero integration is skipped** — client data 
is entered manually in two systems. Errors accumulate. 
Time is wasted.

This build addresses all three. Every architectural 
decision was made for a specific operational reason — 
not default settings applied without thought.

That is the difference between a GHL configuration 
and a GHL implementation.

---

*Built by Olubunmi Akinola — AI-Powered Operations Specialist*
*[LinkedIn](your-linkedin-url) | aoluwabunmilofe@yahoo.com*
*[GitHub Portfolio](https://github.com/yourusername)*
