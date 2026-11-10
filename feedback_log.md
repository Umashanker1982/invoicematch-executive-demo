# Stakeholder feedback log

**Session:** executive demo (7 minutes) + productization workshop (20 minutes) · **Facilitator:** Umashanker (FDE lead)
**Attendees:** Diana (CFO), Marcus (Compliance), Kevin (InfoSec), Priya (AP Manager), Lena (Procurement), Grace (Internal Audit)

> This is a simulated stakeholder session for the course. Silverbrook Financial and its people are fictional. Each entry is turned into an action, a decision, or a backlog item in [productization_plan.md](productization_plan.md).

**Workshop agenda.** (1) What did you see that you trust? (2) What would stop you from launching? (3) Decide: ready / launch with conditions / not ready. (4) Agree owners and dates.

## Feedback, questions, and objections

| ID | Who | Type | What was said | Response in the session | Follow-up | Owner | Due | Status |
|---|---|---|---|---|---|---|---|---|
| F-1 | Diana (CFO) | Question | "Are the 57% and the payback real, or based on sample data?" | Measured on 40 sample invoices; the business case uses stated assumptions with ranges | Re-measure on anonymized real invoices during shadow mode | FDE lead | Week 4 | Open → **C-2** |
| F-2 | Marcus (Compliance) | Objection | "I won't sign off on auto-approval until I see it on our own invoices." | Agreed: auto-approval stays off during shadow mode | Shadow-mode report: system decision vs human decision on every invoice | FDE lead + AP Manager | Week 6 | Open → **C-2** |
| F-3 | Kevin (InfoSec) | Objection | "Invoice text leaving our account needs a security review first." | Only redacted text goes out, through the approved gateway; review is welcome | Security review of egress and gateway; key rotation test | InfoSec + Platform lead | Week 3 | Open → **C-1** |
| F-4 | Kevin (InfoSec) | Question | "What if someone hides instructions in an invoice?" | Showed tour 4: the AI cannot approve; rules decide | Add 10 more injection cases to the test set | FDE team | Week 4 | Backlog **B-6** |
| F-5 | Priya (AP Manager) | Feedback | "The explanations are great. My team needs the contract link on the review screen." | Agreed, small change | Add the contract link and PO link to each held invoice | FDE team | Week 2 | Backlog **B-2** |
| F-6 | Priya (AP Manager) | Objection | "My team is worried this is about headcount." | Goal is overtime and routine work; people keep every exception | Written statement from the CFO; team Q&A session | CFO + AP Manager | Week 1 | Decision **D-3** |
| F-7 | Lena (Procurement) | Feedback | "If price mismatches come to us, give us a monthly summary, not one email per invoice." | Agreed | Monthly price-drift report by vendor | FDE analyst | Week 8 | Backlog **B-5** |
| F-8 | Grace (Internal Audit) | Question | "Can I sample decisions myself without asking IT?" | The audit log is read-only for Audit | Read-only audit role and a CSV export | FDE team | Week 6 | Backlog **B-4** |
| F-9 | Diana (CFO) | Question | "What does it cost if it goes wrong at 2 AM?" | Safety switch sends everything to people in minutes; rules fallback | Run a gateway-outage drill before go-live | Platform lead | Week 10 | Open → **C-3** |
| F-10 | Marcus (Compliance) | Feedback | "Changing the $10,000 limit must stay a Compliance decision." | Agreed; it is configuration with sign-off | Document the change process in the runbook | AP Manager | Week 2 | Done in plan |

## Decisions made

| ID | Decision | Made by |
|---|---|---|
| **D-1** | **Launch with conditions:** 12-week pilot, starting in shadow mode (no auto-approval) | Diana (CFO), with Marcus and Kevin agreeing |
| **D-2** | Pilot scope: PO-backed digital USD invoices from 10 pilot vendors; auto-approve limit stays at $10,000 when turned on | Steering group |
| **D-3** | CFO publishes a written statement: the tool is not used to rate individuals, and freed time goes to exceptions and vendor work | Diana (CFO) |
| **D-4** | Auto-approval is switched on only after conditions C-1 to C-3 are met | Marcus (Compliance) |

## Launch conditions (from the session)

| ID | Condition | Evidence required | Owner |
|---|---|---|---|
| **C-1** | Security review passed for egress, gateway, and secrets | Signed InfoSec review | Kevin |
| **C-2** | Shadow mode on real invoices: field accuracy ≥ 97%, **0** wrong would-be approvals, ≥ 98% agreement with human decisions for 2 weeks | Shadow-mode report | FDE lead + Priya |
| **C-3** | Gateway-outage and wrong-approval drills passed using only the runbook | Drill records | Platform lead |
